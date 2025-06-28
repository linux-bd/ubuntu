### Make Soft link for portably installed Cmake, Ninja, Clang, Clang++
```sh
# CMake
sudo ln -sf /opt/tools/cmake/bin/cmake /usr/local/bin/cmake

# Ninja
sudo ln -sf /opt/tools/ninja/ninja /usr/local/bin/ninja

# Clang and Clang++
sudo ln -sf /opt/sdk/LLVM/bin/clang /usr/local/bin/clang
sudo ln -sf /opt/sdk/LLVM/bin/clang++ /usr/local/bin/clang++
```
