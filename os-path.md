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

### Ubuntu ~/.bashrc [/home/google/.bashrc] Path Variable
```sh
export PATH="$PATH:/opt/redis"
export PATH="$PATH:/opt/python"
export PATH="$PATH:/opt/jdk/bin"
export PATH="$PATH:/opt/nodejs/bin"
export PATH="$PATH:/opt/gradle/bin"
export PATH="$PATH:/opt/erlang/bin"
export PATH="$PATH:/opt/matlab/bin"
export PATH="$PATH:/home/google/Android/Sdk/platform-tools"
export PATH="$PATH:/opt/rust/build/x86_64-unknown-linux-gnu/stage1/bin"
```

### Ubuntu ~/.profile [/home/google/.bashrc] Path Variable
```sh
# set PATH so it includes user's private bin directories
PATH="$HOME/bin:$HOME/.local/bin:$PATH"
--------------------------------------------------------
export GOROOT=/opt/go
export PATH=$PATH:$GOROOT/bin
export GOPATH=$HOME/data/code/golang
export GOBIN=$HOME/data/code/golang/bin
```

