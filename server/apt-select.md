## Ubuntu Mirror Apt Select Nearest Server
```sh
sudo apt install python3-pip
pip3 install apt-select
sudo reboot now
apt-select --country BD
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
sudo mv sources.list /etc/apt
sudo apt update
sudo apt dist-upgrade
sudo reboot now
```
