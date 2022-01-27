---
title: "Build from source"
weight: 3
---

>From version 2.0.19 libcleri is not included as part of this source anymore
>and needs to be installed separately. libcleri can be found here:
>[https://github.com/cesbit/libcleri](https://github.com/cesbit/libcleri)
>or can be installed using `apt`.

#### Linux
Install the following requirements: (Ubuntu 18.04)
```bash
sudo apt install libcleri-dev
sudo apt install libpcre2-dev
sudo apt install libuv1-dev
sudo apt install libyajl-dev
sudo apt install uuid-dev
```

Compile (replace Release with Debug for a debug build):
```bash
cd ./Release
make clean
make test
make
```

Install
```bash
sudo make install
```

#### OSX
>Make sure [libcleri](https://github.com/cesbit/libcleri) is installed!

Install the following requirements:
```bash
brew install pcre2
brew install libuv
brew install yajl
brew install ossp-uuid
```
Compile (replace Release with Debug for a debug build):
```bash
cd ./Release
export CFLAGS="-I/usr/local/include"
export LDFLAGS="-L/usr/local/lib"
make clean
make test
make
```

Install
```bash
sudo make install
```
