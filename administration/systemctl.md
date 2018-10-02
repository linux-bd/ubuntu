
## [Service Enable Disable Start Stop](https://www.digitalocean.com/community/tutorials/how-to-use-systemctl-to-manage-systemd-services-and-units)
```sh
sudo systemctl start application.service
sudo systemctl stop application.service
sudo systemctl restart application.service
sudo systemctl reload application.service
sudo systemctl reload-or-restart application.service
sudo systemctl enable application.service
sudo systemctl disable application.service
systemctl status application.service
systemctl is-active application.service
systemctl is-enabled application.service
systemctl is-failed application.service
systemctl list-units
systemctl list-units --all
systemctl list-units --all --state=inactive
systemctl list-units --type=service
systemctl list-unit-files
systemctl cat atd.service
systemctl list-dependencies sshd.service
systemctl show sshd.service
systemctl show sshd.service -p Conflicts
sudo systemctl mask nginx.service
systemctl list-unit-files
```
