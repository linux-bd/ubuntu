### Change the Minimum Password Length in Ubuntu

Ubuntu requires a minimum password length of 8 characters, as well as complexity check by default, though you can set a short password while installing Ubuntu.

The /etc/pam.d/common-password file handles password-related configurations. If you want to set a short password and disable complexity check, edit the file via below steps:

1. Open terminal from the Dash, Launcher or by pressing `Ctrl+Alt+T` on keyboard. When it opens, run below command to edit the file:

```sh
sudo nano /etc/pam.d/common-password
edit-password
```

Type in your user password when it asks

2. When the file opens in the terminal screen, scroll down and find out the line:

` password     [success=1 default=ignore]    pam_unix.so obscure sha512 `

To set minimum password length, add minlen=N (N is a number) to the end of this line.

To disable complexity check, remove ` obscure ` from that line.

set-password-length

After that, press Ctrl+X and then type Y to save changes and finally press Enter to exit editing.

After all, change your password via `passwd USERNAME ` command.

change user password in Ubuntu

