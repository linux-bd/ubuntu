### Ubuntu OS Directory Structure
* username: ``` amran ```
* ``` /home/amran/ ```
#### ``` amran ``` user directory
```sh
app
home
├── amran
   ├── android
       ├── android-studio
       ├── sdk
   ├── app
       ├── android
       ├── clang
       ├── cpp
       ├── erlang
       ├── golang
       ├── java
       ├── kotlin
       ├── matlab
       ├── nodejs
       ├── php
       ├── python
       ├── ruby
       ├── rust
       └── scala
   ├── media
   ├── phone
   ├── soft
   ├── tools
   ├── vmware
```

#### ``` opt ``` directory permission
```sh
sudo chmod -R 777 /opt/*
```

#### ``` opt ``` directory
* ``` BFS = Built From Source ```
```sh
opt
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
├── openjdk     [BINARY]
├── python      [BFS]
├── qtsdk       [INSTALL]
├── redis       [BFS]
├── rust        [BFS]
└── webstorm    [INSTALL]
```

### Ubuntu ~/.bashrc Path Variable
* ``` sudo vim /home/amran/.bashrc ```
```sh
export PATH="$PATH:/opt/yasm"
export PATH="$PATH:/opt/nasm"
export PATH="$PATH:/opt/ffmpeg"

export PATH="$PATH:/opt/redis"
export PATH="$PATH:/opt/nodejs/bin"

export PATH="$PATH:/opt/jdk/bin"
export PATH="$PATH:/opt/gradle/bin"

export PATH="$PATH:/opt/erlang/bin"
export PATH="$PATH:/opt/rust/build/x86_64-unknown-linux-gnu/stage1/bin"

export PATH="$PATH:/opt/python"
export PATH="$PATH:/opt/php-7.2.2/sapi/cli"

export PATH="$PATH:/opt/robo3t/bin"
export PATH="$PATH:/opt/mongodb/bin"

export PATH="$PATH:/opt/pgsql/bin"
export PATH="$PATH:/opt/qtsdk/5.10.0/gcc_64/bin"

export PATH="$PATH:/opt/matlab/bin"
export PATH="$PATH:/home/google/Android/Sdk/platform-tools"


alias matlab='matlab -desktop'
alias postgre='pg_ctl -D /opt/pgsql/data -l logfile start'
alias mongod='mongod --config "/opt/mongodb/config/mongod.cfg"'

export PATH="$PATH:/opt/mssql-tools/bin"
```

### Ubuntu ~/.profile Path Variable
* ``` sudo vim ~/.profile ```
```sh
# set PATH so it includes user's private bin directories
PATH="$HOME/bin:$HOME/.local/bin:$PATH"
--------------------------------------------------------
export GOROOT=/opt/go
export PATH=$PATH:$GOROOT/bin
export GOPATH=$HOME/data/code/golang
export GOBIN=$HOME/data/code/golang/bin
```

