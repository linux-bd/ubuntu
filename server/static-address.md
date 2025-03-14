### Static Address Configuration for multiple linux servers connected with Wifi and ethernet
### ```sudo cat /etc/netplan/50-cloud-init.yaml```
```sh
network:
  version: 2
  renderer: networkd
  ethernets:
    enp0s31f6:  # Change this to your actual network interface name -> ip link show
      dhcp4: no
      addresses:
        - 192.168.1.101/24  # Your desired static IP
      routes:
        - to: 0.0.0.0/0  # Default route
          via: 192.168.1.1  # Your router’s IP
          table: 100  # Custom table for Ethernet
      routing-policy:
        - from: 192.168.1.101
          table: 100
      nameservers:
        addresses:
          - 8.8.8.8   # Google DNS
          - 8.8.4.4

  wifis:
    wlp0s20f3:  # Change this to your actual Wi-Fi interface name -> ip link show
      dhcp4: no
      addresses:
        - 192.168.1.201/24  # Static IP for Wi-Fi (Change for each laptop)
      routes:
        - to: 0.0.0.0/0  # Default route
          via: 192.168.1.1  # Router IP
          table: 101  # Custom table for Wi-Fi
      routing-policy:
        - from: 192.168.1.201
          table: 101
      nameservers:
        addresses:
          - 8.8.8.8
          - 8.8.4.4
      access-points:
        "TP-Link_3A36":
          password: "333888222"
      optional: true  # Avoids boot delay if Wi-Fi is unavailable
```
### ```sudo netplan apply```

### Updated Static Server Address Setup
### ``` sudo vim /etc/netplan/50-cloud-init.yaml ```
```
network:
  version: 2
  renderer: networkd
  ethernets:
    enp0s31f6:  # Change this to your actual network interface name
      dhcp4: no
      addresses:
        - 192.168.1.103/24  # Your desired static IP
      routes:
        - to: default
          via: 192.168.1.1  # Your router’s IP
      nameservers:
        addresses:
          - 8.8.8.8   # Google DNS
          - 8.8.4.4
```
### Try/Debug
```sh
sudo netplan try
sudo netplan apply
```
### SSH Without Password Giving
```sh
ssh-keygen -t rsa -b 4096
```
This will Create a file in ```.ssh``` folder named ``` id_rsa.pub ```

### Copy Above file contents to server ``` .ssh/authorized_keys ```
### From Multiple Pc
For multiple computer proceed with same process and paste the generated key to ```authorized_keys``` under the existing key file giving a new line

### Restore DHCP Default Setup
### ``` sudo vim /etc/netplan/50-cloud-init.yaml ```
```sh
network:
  version: 2
  ethernets:
    enp0s31f6:
      dhcp4: true
```

### [Tutorial](https://www.youtube.com/watch?v=-WUCqkjOIMY)
### ifconfig
```sh
ens33: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.247.218  netmask 255.255.252.0  broadcast 192.168.247.255
        inet6 fe80::20c:29ff:fe3b:72a0  prefixlen 64  scopeid 0x20<link>
        ether 00:0c:29:3b:72:a0  txqueuelen 1000  (Ethernet)
        RX packets 4857952  bytes 655205565 (655.2 MB)
        RX errors 0  dropped 96895  overruns 0  frame 0
        TX packets 653290  bytes 735396068 (735.3 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 1137  bytes 225578 (225.5 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 1137  bytes 225578 (225.5 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
```

### route -n
```sh
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.244.1   0.0.0.0         UG    100    0        0 ens33
192.168.244.0   0.0.0.0         255.255.252.0   U     0      0        0 ens33
192.168.244.1   0.0.0.0         255.255.255.255 UH    100    0        0 ens33
```

### sudo vim /etc/network/interfaces
```sh
# ifupdown has been replaced by netplan(5) on this system.  See
# /etc/netplan for current configuration.
# To re-enable ifupdown on this system, you can run:
#    sudo apt install ifupdown
auto ens33
iface ens33 inet static
	address 192.168.247.218
	netmask 255.255.252.0
	broadcast 192.168.247.255
	gateway 192.168.244.1
dns-nameservers 192.168.244.1
```

### Service Restart
```sh
sudo service networkd-dispatcher restart
```
