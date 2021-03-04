---
title: "Membuat Repo Cydia"
description: "Setelah tema jadi, tema perlu di-compile dan diunggah ke repository"
date: 2020-01-28T00:36:19+09:00
weight: 3
draft: false
---

## Membuat Repo Cydia

Repositori Cydia digunakan untuk banyak hal, mulai dari membuat *tweak* dan tema hingga *hosting tweak* dan tema. Aku membuat tutorial ini dan percaya bahwa kamu tiak menggunakan ini untuk membuat repo bajakan.

### Persiapan

Hal yang perlu dipersiapkan:
- Akun Github, dengan Github Pages yang aktif
- Git
- Program pengarsipan yang mendukung pengarsipan bzip2 seperti 7-Zip
- Perangkat iOS yang telah di-*jailbreak* (kalau ada)
- Teks editor seperti Notepad++ atau lainnya

### Buat repository baru

Masuk ke Github dan buat repository baru

### Clone Repository

```sh 
  git clone https://github.com/your_username/project_name.git
```

### Buat file index.html

```html
  <!DOCTYPE html>
  <html>
  <body>
  <h1>Hello World!</h1>
  <p>This is a Cydia repo!</p>
  </body>
  </html>
```

### Buat folder debs

### Buat file Release dan Packages

### Tambahkan tweak atau theme

Tambahkan tweak.deb atau theme.deb ke dalam folder debs/

### Susunan File

Susunan file sebelum diunggah:
```
TweakFolder/
| debs/
| | com.kva.family.deb
| Packages
| Release
```

### Modifikasi file Release dan Packages

Isi dari file Release
```text
  Origin: (Modify)
  Label: (Modify)
  Suite: stable
  Version: 1.0
  Codename: ios
  Architectures: iphoneos-arm
  Components: main
  Description: (Modify)
```
Ubah apa yang ada di dalam kurung, bisa nama repo, ini tidak masalah.

Isi dari file Packages
```text
  Package: 
  Name: 
  Version: 
  Architecture: 
  Description: 
  Maintainer: 
  Author: 
  Section: 
  Depends: 
  Filename: 
  Size: 
  MD5sum: 
  SHA1: 
  SHA256: 
  SHA512: 
```
`Package` adalah id untuk tweak (com.example.tweak)
`Name` adalah nama tweak (Tes Tweak)
`Version` adalah versi dari tweak
`Architecture` umumnya adalah `iphone-os-arm` atau `iphoneos-arm64`, isi `iphone-os-arm` jika kamu tidak tahu apa ini
`Description` adalah deskripsi tweak
`Maintainer` adalah orang yang memperbarui tweak (nama orang alamat email)
`Author` adalah orang yang membuat tweak (nama orang alamat email)
`Section` adalah kategori yang cocok dengan tweak (Tweaks) atau (Themes)
`Depends` adalah apapun yang dibutuhkan agar tweak bisa bekerja dengan baik
`Filename` adalah nama file deb, jika file deb berada di dalam folder maka debs/nama_file.deb
`Size` adalah ukuran file dalam bytes (123456)
`MD5sum` adalah MD5 hash ditulis dengan lowercase
`SHA1sum` adalah SHA1 hash ditulis dengan lowercase
`SHA256sum` adalah SHA256 hash ditulis dengan lowercase
`SHA512sum` adalah SHA512 hash ditulis dengan lowercase

Misalnya:
```text
  Package: com.kva.family
  Name: Family Theme
  Version: 1.0
  Architecture: iphoneos-arm
  Description: Family Theme
  Maintainer: kva <kva@mail.xyz>
  Author: kva <kva@mail.xyz>
  Section: Themes
  Depends: com.anemonetheming.anemone, com.spark.snowboard
  Filename: debs/com.kva.family.deb
  Size: 6646680
  MD5sum:  3ce81314d0ff5fede8c5ec78500f76f0
  SHA1: a71bf963de5fc5d3b619dfbbf7a9d8f7982ff7b6
  SHA256: 4f1bef6cc4132de5a6725652f9fe0a9381487aa0c2d719777e541446c1905d4c
  SHA512: 16b1a0484f5dddd9f6755792200135515d41ba09d95a759cf8c70be6c1cb0b110394cb1b917c9401ad54ecf9be3e6aab036c5003ebad4a91c8251d0e63feb8dc
```

### Add, commit dan push ke Github

```sh
  git add .
  git commit -m "pesan"
  git push
```


### Referensi
https://www.reddit.com/r/jailbreak/comments/90gpli/tutorial_create_a_cydia_repository_using_github/
