## Postman Install
### Install Dependency
```sh
sudo apt -y install libgconf2-4 [ubuntu 18.04.2]
```

### Download and Create Link
```sh
wget https://dl.pstmn.io/download/latest/linux64 -O Postman.tar.gz
sudo tar -xzf Postman.tar.gz -C /opt/tools
rm Postman.tar.gz
sudo ln -s /opt/tools/Postman/Postman /usr/bin/Postman
```
### Create Desktop Icon
```sh
cat > ~/.local/share/applications/Postman.desktop <<EOL
[Desktop Entry]
Encoding=UTF-8
Name=Postman
Exec=Postman
Icon=/opt/tools/Postman/app/resources/app/assets/icon.png
Terminal=false
Type=Application
Categories=Development;
EOL
```
