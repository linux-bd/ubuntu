Below is a complete, step-by-step guide to **copy a QCOW2 VM image to another machine** (different host, different path) **and restore/run it properly** with `libvirt`/`qemu-kvm` (the most common setup on Linux).

---

## 1. Prerequisites on **both** machines

| Requirement | Command |
|-------------|---------|
| Same or newer QEMU/KVM version | `qemu-img --version` |
| `libvirt` installed & running | `sudo systemctl status libvirtd` |
| User in `libvirt` group | `sudo usermod -aG libvirt $USER` |
| `virt-manager` (optional GUI) | `sudo dnf install virt-manager` / `apt install virt-manager` |

> **Tip**: Use the **same major QEMU version** on source and destination to avoid compatibility issues.

---

## 2. On the **source** machine – Prepare & copy the QCOW2

```bash
# 1. Find the VM name and its disk path
virsh list --all
virsh domblklist <vm-name>

# Example output:
#  vda  /var/lib/libvirt/images/myvm.qcow2
```

### A. Shut down the VM cleanly
```bash
virsh shutdown <vm-name>   # or virsh destroy if stuck
```

### B. Optional: Create a **consistent snapshot** (zero-downtime copy)
```bash
qemu-img create -f qcow2 -b /var/lib/libvirt/images/myvm.qcow2 \
         /var/lib/libvirt/images/myvm-snap.qcow2
```
> You can copy `myvm-snap.qcow2` while the VM keeps running.

### C. Copy the file (choose one method)

#### 1. `rsync` (recommended, resumable)
```bash
rsync -avh --progress /var/lib/libvirt/images/myvm.qcow2 \
      user@dest-host:/var/lib/libvirt/images/
```

#### 2. `scp`
```bash
scp /var/lib/libvirt/images/myvm.qcow2 user@dest-host:/var/lib/libvirt/images/
```

#### 3. USB/External drive
```bash
cp /var/lib/libvirt/images/myvm.qcow2 /mnt/usb/
# then plug into dest and copy to final path
```

---

## 3. On the **destination** machine – Restore the VM

### A. Place the QCOW2 in the new path
```bash
sudo mkdir -p /new/path/images
sudo mv /var/lib/libvirt/images/myvm.qcow2 /new/path/images/
sudo chown qemu:qemu /new/path/images/myvm.qcow2
```

### B. Export the original VM definition (XML)
**On source:**
```bash
virsh dumpxml <vm-name> > myvm.xml
scp myvm.xml user@dest-host:~
```

### C. Edit the XML for the **new disk path**
```bash
vim myvm.xml
```
Find the `<disk>` section and change:
```xml
<source file='/var/lib/libvirt/images/myvm.qcow2'/>
```
→
```xml
<source file='/new/path/images/myvm.qcow2'/>
```

> Also update `<name>`, `<uuid>` (optional), MAC addresses, or any host-specific paths (e.g. CDROM ISO).

### D. Define & start the VM
```bash
sudo virsh define myvm.xml
sudo virsh start <vm-name>
```

### E. Verify
```bash
virsh list --all
virsh domblklist <vm-name>
```

---

## 4. Common Gotchas & Fixes

| Issue | Fix |
|-------|-----|
| **Permission denied** | `chown qemu:qemu /new/path/images/*.qcow2` |
| **SELinux denials** | `restorecon -Rv /new/path/images/` or `setsebool -P virt_use_nfs 1` |
| **Different CPU topology** | Edit XML `<cpu mode='host-passthrough'/>` or `<cpu mode='host-model'/>` |
| **Backing file errors** | Copy **all** backing chain files or use `qemu-img rebase` |
| **Snapshot chain broken** | Use `qemu-img commit` or `virsh snapshot-revert` on source first |

---

## 5. One-liner Summary (for scripts)

```bash
# SOURCE
virsh shutdown myvm && \
virsh dumpxml myvm > myvm.xml && \
rsync -av myvm.qcow2 user@dest:/new/path/images/

# DEST
sudo mv /new/path/images/myvm.qcow2 /new/path/images/ && \
sudo chown qemu:qemu /new/path/images/myvm.qcow2 && \
sed -i "s|/var/lib/libvirt/images/|/new/path/images/|g" myvm.xml && \
sudo virsh define myvm.xml && sudo virsh start myvm
```

---

## Bonus: Convert to raw (if needed)
```bash
qemu-img convert -O raw myvm.qcow2 myvm.raw
```

---

You’re done! The VM will boot on the new machine with the new disk path.
