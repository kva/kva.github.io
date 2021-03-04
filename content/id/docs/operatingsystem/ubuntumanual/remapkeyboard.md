---
title: "Remap Keyboard"
description: "Mengubah fungsi tombol keyboard di Ubuntu"
date: 2020-01-28T00:34:39+09:00
draft: false
weight: 1
collapsible: false
---

## Mengubah fungsi tombol keyboard di Ubuntu

Tombol `z`,`CTRL`, `CAPS LOCK` dan `Fn` di komputerku tidak berfungsi. Karena tombol `z` adalah tombol yang penting, dan karena tidak ada alasan ekonomis untuk mengganti keseluruhan tombol (baca: beli keyboard baru) hanya karena beberapa tombol rusak. Jadi aku putuskan untuk melakukan remap keyboard

### Mencari keycode

```bash
xmodmap -pk
```

Ditemukan: keycode `z` = 52 dan tombol yang akan digunakan adalah `ALT` kanan dengan keycode 108

### Buat shell script

```sh
#!/bin/bash
xmodmap -e "keycode 52 = Alt_R" && xmodmap -e "keycode 108 = z"
```
simpan dengan ekstensi .sh, misalnya `key.sh`

### Ubah Format Permission File

Ubah dengan :

```
sudo chmod 774 key.sh
```
Digit pertama adalah adalah pengguna saat ini (current user).
Digit kedua adalahh untuk user group.
Digit ketiga adalah untuk user yang lain (others)

4 adalah ijin read-only
2 adalah ijin write
1 adalah ijin execute

Jadi angka 7 adalah jumlah dari 4 + 2 + 1.

### Jalankan program

```sh
./key.sh
```

Jika program tersebut dijalankan, maka fungsi tombol `z` dan `ALT-kanan` akan ditukar, jadi saat menekan tombol `ALT-kanan` akan keluar huruf z. Program di atas hanya bisa dijalankan satu kali, maka agar bisa berfungsi terus-menerus secara otomatis, perlu ditambahkan alias

### Menambahkan alias

```bash
touch .bash_aliases
nano .bash_aliases
alias key="./key.sh"
```
Alhamdulillah, selesai


### Referensi

[https://hassanzaid.medium.com/how-to-remap-your-keys-in-ubuntu-900404f2ca61](https://hassanzaid.medium.com/how-to-remap-your-keys-in-ubuntu-900404f2ca61)
