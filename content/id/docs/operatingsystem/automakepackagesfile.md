---
title: "Membuat file Packages otomatis"
description: "Cara membuat file Packages secara otomatis"
date: 2020-01-29T00:36:19+09:00
draft: false
---

## Membuat .deb file otomatis
Hanya menggunakan terminal tanpa harus mengedit secara manual satu per satu

## Command

```bash
#!/bin/bash

# tampilan di terminal
echo -n "Masukkan nama folder yang ingin diproses: "

# menyimpan input keyboard
read folder

# menyalin folder ke alamat tujuan
scp -r $folder root@172.20.10.1:/var/mobile/Documents

# membuat .deb file
ssh root@172.20.10.1 dpkg -b /var/mobile/Documents/$folder

# menyalin .deb file dari iDevices ke komputer
scp root@172.20.10.1:/var/mobile/Documents/$folder.deb ~/Apps/cydia/debs

# hapus folder yang telah diproses dadn sudah tidak diperlukan
ssh root@172.20.10.1 rm -r /var/mobile/Documents/$folder
ssh root@172.20.10.1 rm /var/mobile/Documents/$folder.deb

# verifikasi
# Ada .deb di ~/Apps/cydia/debs
# Folder tema di root@172.20.10.1:/var/mobile/Documents/ hilang
# File .deb di root@172.20.10.1:/var/mobile/Documents/ hilang

```

Tugas selanjutnya adalah membuat program untuk mengolah file Packages dan Folder Depictions

### Referensi

Lupa belum disimpan, terlalu banyak.
