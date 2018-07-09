## Robomongo Ubuntu Install

[Robo Icon](https://robomongo.org/static/robomongo-128x128-129df2f1.png)
## Create Desktop Icon
```sh
cat > ~/.local/share/applications/robo.desktop <<EOL
[Desktop Entry]
Encoding=UTF-8
Name=Robo
Exec=robo
Icon=/opt/robo3t/bin/robo.png
Terminal=false
Type=Application
Categories=Development;
EOL
```
