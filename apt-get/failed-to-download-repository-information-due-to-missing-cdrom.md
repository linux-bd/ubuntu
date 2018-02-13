### [sudo apt-get update](https://askubuntu.com/questions/125111/failed-to-download-repository-information-due-to-missing-cdrom)

#### The issue here is that your OS is looking for CD-ROM in the apt sources list. To fix this:
```sh
sudo vi /etc/apt/sources.list
```
#### Remove any lines that include CD-ROM. Save the file and try once more.
