# Pkgman - Package manager for LFS.

Pkgman is a [package manager](https://en.wikipedia.org/wiki/Package_manager) for [LFS](linuxfromscratch.org). It serves as a automated build system with automatically downloading dependencies and etc.

### Package build system

Everything starts with a some kind of file where are build instructions. Pkgman uses files that are ending with .rc suffix. Here is an example.

```shell
#!/bin/bash
name=example
version=1.0
src=git+https://github.com/$name/$name.git
dependencies=base/kernel base/bash base/dialog

prepare() {
    cd $name
    git checkout $version
    ./autogen.sh
    ./configure
}

build() {
    make
}

install() {
    sudo make install
}
```

### Configuration

At the start of the pkgman file, there are some values that can be configured:

```shell
arch=$(uname -m)
server=dl.mpm.sk
technology=wget
suffix=rc
compression=xz
download_dir=/var/db/pkgman/downloads
src_dir=/var/db/pkgman/src
compression=gz
```

### Contributing

See [Contributing](CONTRIBUTING.md)
