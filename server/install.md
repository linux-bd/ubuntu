# 🧭 **Ubuntu Server 24.04 Installation with Static IPs (192.168.1.201–210)**

---

## 🪄 **Step 1: Boot from Ubuntu Server ISO**

1. [Ubuntu Server 24.04 LTS ISO](https://ubuntu.com/download/server) ডাউনলোড করো।
2. Rufus বা balenaEtcher দিয়ে USB বুটেবল করো।
3. BIOS/UEFI থেকে USB Boot করে "Install Ubuntu Server" নির্বাচন করো।

---

## 🪄 **Step 2: Language, Keyboard, Mirror**

* **Language:** English
* **Keyboard layout:** English (US)
* **Mirror (Bangladesh):**

  ```
  http://mirror.xeonbd.com/ubuntu-archive/
  ```

  অথবা fallback:

  ```
  http://archive.ubuntu.com/ubuntu/
  ```

---

## 🪄 **Step 3: Network Configuration (Static IP Setup)**

প্রতিটি ল্যাপটপে এই ধাপে static IP আলাদা করে দাও।

### Example for each:

| Laptop | Hostname | IP Address    | Subnet         | Gateway     | Nameservers      |
| ------ | -------- | ------------- | -------------- | ----------- | ---------------- |
| 1      | linux1   | 192.168.1.201 | 192.168.1.0/24 | 192.168.1.1 | 8.8.8.8, 1.1.1.1 |
| 2      | linux2   | 192.168.1.202 | 192.168.1.0/24 | 192.168.1.1 | 8.8.8.8, 1.1.1.1 |
| 3      | linux3   | 192.168.1.203 | 192.168.1.0/24 | 192.168.1.1 | 8.8.8.8, 1.1.1.1 |
| 4      | linux4   | 192.168.1.204 | 192.168.1.0/24 | 192.168.1.1 | 8.8.8.8, 1.1.1.1 |
| 5      | linux5   | 192.168.1.205 | 192.168.1.0/24 | 192.168.1.1 | 8.8.8.8, 1.1.1.1 |
| 6      | linux6   | 192.168.1.206 | 192.168.1.0/24 | 192.168.1.1 | 8.8.8.8, 1.1.1.1 |
| 7      | linux7   | 192.168.1.207 | 192.168.1.0/24 | 192.168.1.1 | 8.8.8.8, 1.1.1.1 |
| 8      | linux8   | 192.168.1.208 | 192.168.1.0/24 | 192.168.1.1 | 8.8.8.8, 1.1.1.1 |
| 9      | linux9   | 192.168.1.209 | 192.168.1.0/24 | 192.168.1.1 | 8.8.8.8, 1.1.1.1 |
| 10     | linux10  | 192.168.1.210 | 192.168.1.0/24 | 192.168.1.1 | 8.8.8.8, 1.1.1.1 |

**Search domain:** `lab.local`

> “Save” দিয়ে confirm করো এবং পরের ধাপে যাও।

---

## 🪄 **Step 4: Proxy & Mirror**

* **Proxy:** ফাঁকা রাখো
* **Mirror:** আগেই auto detect হবে (`xeonbd` বা `archive.ubuntu.com`)

---

## 🪄 **Step 5: Storage Configuration**

* “Use an entire disk”
* RAID দরকার না হলে simple configuration রাখো
* পরবর্তীতে LVM বা ZFS প্রয়োজনে enable করা যাবে

---

## 🪄 **Step 6: Profile Setup**

| Field              | Value                    |
| ------------------ | ------------------------ |
| Your name          | Amran                    |
| Your server’s name | (যেমন linux1, linux2, …) |
| Pick a username    | amran                    |
| Choose a password  | 0                        |

---

## 🪄 **Step 7: SSH Setup**

* ✅ “Install OpenSSH server” নির্বাচন করো
  → পরে remote automation, cluster setup, Ansible ইত্যাদি করতে পারবে।

---

## 🪄 **Step 8: Snaps / Packages**

* Skip featured snaps

---

## 🪄 **Step 9: Installation & Reboot**

ইনস্টল শেষ হলে reboot করো।

Login:

```bash
amran
0
```

---

## 🪄 **Step 10: Verify IP and Hostname**

```bash
hostnamectl
ip a show enp0s31f6
```

উদাহরণ:

```
Static IP: 192.168.1.201
Hostname: linux1
```

---

## 🪄 **Step 11: Setup /etc/hosts (Common for all nodes)**

```bash
sudo nano /etc/hosts
```

```text
127.0.0.1   localhost
192.168.1.201 linux1
192.168.1.202 linux2
192.168.1.203 linux3
192.168.1.204 linux4
192.168.1.205 linux5
192.168.1.206 linux6
192.168.1.207 linux7
192.168.1.208 linux8
192.168.1.209 linux9
192.168.1.210 linux10
```

---

## 🪄 **Step 12: Connectivity Test**

```bash
ping -c 3 192.168.1.202
ssh amran@192.168.1.202
```

সব ঠিক থাকলে nodes একে অপরকে ping ও SSH করতে পারবে।

---

## ✅ **Summary Table**

| Laptop | Hostname | Static IP     | Username | Password |
| ------ | -------- | ------------- | -------- | -------- |
| 1      | linux1   | 192.168.1.201 | amran    | 0        |
| 2      | linux2   | 192.168.1.202 | amran    | 0        |
| 3      | linux3   | 192.168.1.203 | amran    | 0        |
| 4      | linux4   | 192.168.1.204 | amran    | 0        |
| 5      | linux5   | 192.168.1.205 | amran    | 0        |
| 6      | linux6   | 192.168.1.206 | amran    | 0        |
| 7      | linux7   | 192.168.1.207 | amran    | 0        |
| 8      | linux8   | 192.168.1.208 | amran    | 0        |
| 9      | linux9   | 192.168.1.209 | amran    | 0        |
| 10     | linux10  | 192.168.1.210 | amran    | 0        |

---

## 💡 **Best Practice Tips**

* Router এ DHCP range রাখো 192.168.1.2–150 পর্যন্ত
  → Static range (201–210) conflict-free থাকবে
* SSH key authentication পরে সেট করো
* NTP sync enable রাখো (time drift এড়াতে)
* `/etc/netplan/01-netcfg.yaml` ফাইল backup রাখো
