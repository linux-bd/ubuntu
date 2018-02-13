### Ubuntu OS Directory Structure
* username: ``` google ```
* ``` /home/google/ ```
#### ``` google ``` user directory
```sh
Android [sdk]
data
├── code
    ├── android
    ├── cpp
    ├── erlang
    ├── golang
    ├── java
    ├── matlab
    ├── nodejs
    └── rust  
media
software
```

#### ``` opt ``` directory permission
```sh
sudo chmod -R 777 /opt/*
```

#### ``` opt ``` directory [Built From Source = BFS]
```sh
├── android     [STUDIO]
├── erlang      [BFS]
├── ffmpeg      [BFS]
├── go          [BINARY]
├── golang      [SRC]
├── google      [chrome chrome-beta chrome-unstable]
├── gradle      [BINARY ONLY]
├── idea        [IntelliJ IDEA]
├── INSTALLER   [BACKUP SRC + BINARY]
├── jdk         [PORTABLE BINARY]
├── matlab      [INSTALL]
├── nodejs      [BINARY]
├── python      [BFS]
├── qtsdk       [INSTALL]
├── redis       [BFS]
├── rust        [BFS]
└── webstorm    [INSTALL]
```
