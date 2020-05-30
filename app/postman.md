## Postman Install
### Install Dependency
```sh
sudo apt -y install libgconf2-4 [ubuntu 18.04.2]
```

### Download and Create Link
```sh
wget https://dl.pstmn.io/download/latest/linux64 -O postman.tar.gz
sudo tar -xzf postman.tar.gz -C /opt
rm postman.tar.gz
sudo ln -s /opt/postman/Postman /usr/bin/Postman
```
### Create Desktop Icon
```sh
cat > ~/.local/share/applications/postman.desktop <<EOL
[Desktop Entry]
Encoding=UTF-8
Name=Postman
Exec=Postman
Icon=/opt/postman/app/resources/app/assets/icon.png
Terminal=false
Type=Application
Categories=Development;
EOL
```
