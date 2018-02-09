### Development Tools Codes Portable Binaries Diretory Structures

```sh
chmod -R 777 /ssd-tech/*
tree -L 3
.
├── bin
│   ├── backup
│   │   └── node-v9.0.0-linux-x64.tar.xz
│   ├── gradle
│   │   ├── bin
│   └── node
│       ├── bin
├── codes
│   ├── cpp
│   ├── nodejs
│   └── spring
└── media
    └── Syria.mp4
```

### Adding Binaries To Bashrc

```sh
export PATH="/ssd-tech/bin/node/bin:$PATH"
export PATH="/ssd-tech/bin/gradle/bin:$PATH"
```
