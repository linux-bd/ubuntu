### Upgrade gcc
```sh
sudo add-apt-repository ppa:ubuntu-toolchain-r/test
sudo apt update
sudo apt dist-upgrade
sudo apt install gcc-7
sudo apt install g++-7
```

### [Build Using Latest gcc](https://askubuntu.com/questions/942784/install-gcc-7-1-on-xubuntu-16-04-and-make-it-default)
#### How to use multiple instances of gcc?
* Although in practice it's often not necessary, since most build systems allow you to 
* specify a particular compiler, either using command-line arguments or environment variables e.g.
```sh
CC=/usr/bin/gcc-7 ./configure
make CC=/usr/bin/gcc-7
cmake -D CMAKE_C_COMPILER=/usr/bin/gcc-7 ..
```
