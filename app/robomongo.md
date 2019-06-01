## Robomongo Ubuntu Install
* Download and save as `robo3t`
* [robo3t icon](https://robomongo.org/static/robomongo-128x128-129df2f1.png)

## Export `Path` Variable
```sh
export PATH="$PATH:/opt/robo3t/bin"
```

## Create Soft Link
```sh
sudo ln -s /opt/robo3t/bin/robo3t /usr/bin/robo3t
```

## Create Desktop Icon
```sh
cat > ~/.local/share/applications/robo3t.desktop <<EOL
[Desktop Entry]
Encoding=UTF-8
Name=Robo
Exec=robo3t
Icon=/opt/robo3t/bin/robo3t.png
Terminal=false
Type=Application
Categories=Development;
EOL
```
