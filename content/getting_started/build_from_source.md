---
title: "Build from source"
weight: 2
---

> As of version `2.0.19`, libcleri is no longer included as part of this source anymore and must be installed separately.
> Libcleri can be found here:
> [https://github.com/cesbit/libcleri](https://github.com/cesbit/libcleri)
> or can be installed using `apt`.

### Linux

Install the following requirements (Ubuntu 20.04):

```bash
sudo apt install libcleri-dev
sudo apt install libpcre2-dev
sudo apt install libuv1-dev
sudo apt install libyajl-dev
sudo apt install uuid-dev
```

Compile the source code:

```bash
cd ./Release
make clean
make test
make
```

> **Note**: Replace `./Release` with `./Debug` for a debug build. It is less optimized, but shows more logging.

And finally install the server:

```bash
sudo make install
```

### OSX

> Make sure [libcleri](https://github.com/cesbit/libcleri) is installed!

Install the following requirements:

```bash
brew install pcre2
brew install libuv
brew install yajl
brew install ossp-uuid
```

Compile the source code:

```bash
cd ./Release
export CFLAGS="-I/usr/local/include"
export LDFLAGS="-L/usr/local/lib"
make clean
make test
make
```

> **Note**: Replace `./Release` with `./Debug` for a debug build. It is less optimized, but shows more logging.

And finally install the server:

```bash
sudo make install
```
