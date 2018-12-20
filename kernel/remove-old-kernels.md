## [Ubuntu Remove Old Unused Kernels](https://gist.github.com/ipbastola/2760cfc28be62a5ee10036851c654600)

* List Kernels
```sh
dpkg --list 'linux-image-*'
```

* Get Active Kernel Version
```sh
uname -r
```

* Remove lower versions linux images one by one
```sh
sudo apt-get purge linux-image-xxxx-generic
```

* Update Grub finally
```sh
sudo update-grub2
sudo update-grub
```

* Remove all unused Headers
```sh
dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | xargs sudo apt-get -y purge
```

* List out active Headers
```sh
dpkg --list | grep linux-headers
```
