---
title: "Install Theos di Ubuntu"
description: "Theos digunakan untuk pembuatan tema dan tweak di iOS"
date: 2020-01-29T00:36:19+09:00
draft: false
---

### Instalasi LLVM
web : [https://apt.llvm.org/](https://apt.llvm.org/)

```bash
sudo apt install clang-format clang-tidy clang-tools clang clangd libc++-dev libc++1 libc++abi-dev libc++abi1 libclang-dev libclang1 liblldb-dev libllvm-ocaml-dev libomp-dev libomp5 lld lldb llvm-dev llvm-runtime llvm python-clang
```

Lalu,

```
sudo apt update
```

### Install Prerequisite

```bash
 sudo apt-get install fakeroot git perl clang-6.0 build-essential
```

### Mengatur THEOS environment

```bash
 echo "export THEOS=~/theos" >> ~/.profile
```

Di bagian ini perlu merestart shell, buka tab baru lalu `echo $THEOS` untuk memeriksa apakah sudah bekerja atau belum.

### Clone THEOS ke perangkat

```bash
 git clone --recursive https://github.com/theos/theos.git $THEOS
```

### Unduh toolchain

```bash
curl https://kabiroberai.com/toolchain/download.php?toolchain=ios-linux -Lo toolchain.tar.gz
tar xzf toolchain.tar.gz -C $THEOS/toolchain
rm toolchain.tar.gz
```

### Unduh iOS SDK

Dapatkan patch SDK dari [repo Theos](https://github.com/theos/sdks)

```bash
curl -LO https://github.com/theos/sdks/archive/master.zip
TMP=$(mktemp -d)
unzip master.zip -d $TMP
mv $TMP/sdks-master/*.sdk $THEOS/sdks
rm -r master.zip $TMP
```

### Install Swift toolchain (optional)

```bash
curl https://kabiroberai.com/toolchain/download.php?toolchain=swift-ubuntu-latest -Lo swift-toolchain.tar.gz
tar xzf swift-toolchain.tar.gz -C $THEOS/toolchain
rm swift-toolchain.tar.gz
```

Versi SDK paling rendah yang dibutuhkan untuk meng-compile kode Swift adalah versi iOS 11.2

### Alhamdulillah, selesai

Selanjutnya dalah membua packages menggunakan Theos, mungkin bisa dibaca di sini [https://ivancristina.github.io/2020/01/02/tweakdevelop/](https://ivancristina.github.io/2020/01/02/tweakdevelop/)

### Referensi

[https://github.com/theos/theos/wiki/Installation-Linux](https://github.com/theos/theos/wiki/Installation-Linux)
