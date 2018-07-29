## ifconfig
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

## route -n
```sh
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.244.1   0.0.0.0         UG    100    0        0 ens33
192.168.244.0   0.0.0.0         255.255.252.0   U     0      0        0 ens33
192.168.244.1   0.0.0.0         255.255.255.255 UH    100    0        0 ens33
```

## cat /etc/network/interfaces
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

## Service Restart
```sh
sudo service networkd-dispatcher restart
```
