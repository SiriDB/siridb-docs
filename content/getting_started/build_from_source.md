---
title: "Build from source"
weight: 3
---

>From version 2.0.19 libcleri is not included as part of this source anymore
>and needs to be installed separately. libcleri can be found here:
>[https://github.com/transceptor-technology/libcleri](https://github.com/transceptor-technology/libcleri)
>or can be installed using `apt`.

#### Linux
Install the following requirements: (Ubuntu 18.04)
```
sudo apt install libcleri-dev
sudo apt install libpcre2-dev
sudo apt install libuv1-dev
sudo apt install libyajl-dev
sudo apt install uuid-dev
```

Compile (replace Release with Debug for a debug build):
```
cd ./Release
make clean
make test
make
```

Install
```
sudo make install
```

#### OSX
>Make sure [libcleri](https://github.com/transceptor-technology/libcleri) is installed!

Install the following requirements:
```
brew install pcre2
brew install libuv
brew install yajl
brew install ossp-uuid
```
Compile (replace Release with Debug for a debug build):
```
cd ./Release
export CFLAGS="-I/usr/local/include"
export LDFLAGS="-L/usr/local/lib"
make clean
make test
make
```

Install
```
sudo make install
```