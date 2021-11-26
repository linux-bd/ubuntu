## Create Wifi Hotspot & Startup in Ubuntu

### Create Hotspot
* Go to Wifi Settings
* Create a Hotspot
* By default it will named as `Hotspot`

### Automatica Start
* Show Wifi Hotspot by
```sh
nmcli device show | grep GENERAL.CONNECTION:
```
### It will out as like
```sh
GENERAL.CONNECTION:                     Hotspot
GENERAL.CONNECTION:                     Wired
GENERAL.CONNECTION:                     --
GENERAL.CONNECTION:                     --
```

### Script for automatic start
```sh
nmcli con modify Hotspot connection.autoconnect true
sudo reboot now
```
