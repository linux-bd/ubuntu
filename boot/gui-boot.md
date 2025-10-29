### **Solution for GRUB Only boot (No systemd-boot, No kernelstub)**

You are **stuck with GRUB** — but we’ll make it **100% silent and graphical**.

---

## Step-by-Step: **Only Spinner Loader, No Text, No Menu**

### 1. **Reinstall Plymouth Spinner Theme**
```bash
sudo apt update
sudo apt install --reinstall plymouth-theme-spinner
```

---

### 2. **Set `spinner` as Default**
```bash
sudo update-alternatives --install /usr/share/plymouth/themes/default.plymouth default.plymouth /usr/share/plymouth/themes/spinner/spinner.plymouth 150

sudo update-alternatives --config default.plymouth
```
→ **Type `2`** (or the number for `spinner`)

---

### 3. **Create Plymouth Config**
```bash
sudo mkdir -p /etc/plymouth
sudo nano /etc/plymouth/plymouthd.conf
```

```ini
[Daemon]
Theme=spinner
ShowDelay=0
DeviceTimeout=30
```

---

### 4. **Configure GRUB (Hide Everything)**
```bash
sudo nano /etc/default/grub
```

```bash
GRUB_TIMEOUT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_DISABLE_OS_PROBER=true
GRUB_CMDLINE_LINUX_DEFAULT="quiet loglevel=0 splash vt.global_cursor_default=0"
GRUB_CMDLINE_LINUX=""
GRUB_TERMINAL=console
GRUB_GFXMODE=auto
GRUB_GFXPAYLOAD_LINUX=keep
```

---

### 5. **Update GRUB & Initramfs**
```bash
sudo update-grub
sudo update-initramfs -u -k all
```

---

### 6. **(Optional) Lock GRUB Menu**
```bash
printf "yourpassword\nyourpassword\n" | grub-mkpasswd-pbkdf2
```
→ Copy the **long hash**

```bash
sudo nano /etc/grub.d/40_custom
```

```bash
set superusers="admin"
password_pbkdf2 admin YOUR_HASH_HERE
```

```bash
sudo chmod 600 /etc/grub.d/40_custom
sudo update-grub
```

---

### 7. **Reboot**
```bash
sudo reboot
```

---

### **Result: 100% Clean Boot**
```
[Power On] → [BIOS] → GRUB (invisible) → **SPINNER (circles + dots)** → GDM Login
```

- **No GRUB menu**  
- **No console text**  
- **No cursor**  
- **Only graphical loader**

---

### Verify After Reboot
```bash
cat /proc/cmdline
# → Must show: quiet loglevel=0 splash vt.global_cursor_default=0

journalctl -b | grep -i "plymouth.*theme"
# → Using theme 'spinner'
```

---

### Prevent Future Breaks
In **Synaptic**:
- Lock: `plymouth-theme-spinner`
- **Never** remove `grub-*` or `plymouth*`

---

**Done.**  
You now have **only the loader** — **start to finish** — **no console, no text, no menu**.  
No `kernelstub`, no `systemd-boot` needed. GRUB is silent and invisible.
