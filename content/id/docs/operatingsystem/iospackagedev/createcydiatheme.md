---
title: "Membuat Tema Cydia"
description: "Langkah awal dalam membuat tema untuk Snowboard Cydia"
date: 2020-01-27T00:36:19+09:00
weight: 1
draft: false
---

## Membuat Tema Cydia
Tema dapat digunakan untuk mengubah icon dan notification badge

### Persiapan

Hal yang dibutuhkan:
1. Aplikasi pengolah gambar seperti Inkscape
2. SSH komputer dan iPhone
3. dpkg package

### Struktur Folder

Tanpa struktur yang benar, tema tidak akan bekerja bahkan mungkin tidak akan muncul.
Buat folder `NamaTema.theme` dengan akhiran .theme 

```
  NamaTema.theme/
    IconBundles/
    Info.Plist
```

### Modifikasi Info.Plist

Ubah `ThemeName` dengan nama tema yang kamu buat.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
  <plist version="1.0">
  <dict>
    <key>PackageName</key>
    <string>ThemeName</string>
    <key>ThemeType</key>
    <string>Icons</string>
  </dict>
</plist>
```

### Buat Icon

Gunakan Aplikasi Inkscape. Ukuran Resolusi Icon `512x512px` agar bisa bekerja di iPad dan perangkat lain dengan resolusi layar yang lebih tinggi. Buatlah icon berbentuk persegi.

### Simpan Icon

Icon disimpan dalam folder `IconBundles` dengan format `.png`. Pemberian nama icon sangat penting, misalnya `com.apple.AppStore-large.png`
```
  NamaTema.theme/
    IconBundles/
      com.apple.AppStore-large.png
```

### BundleID

BundleID adalah identifier untuk masing-masing aplikasi. Misalnya untuk App Store adalah `com.apple.AppStore`. Berarti icon untuk App Store harus disimpan dengan nama `com.apple.AppStore-large.png`

### Daftar BundleID

Cari ya...

### Icon Mask

Icon mask digunakan untuk membuat icon (yang semula berbentuk kotak) menjadi lingkaran, misalnya. Keuntungannya adalah pengguna dapat mengaktifkan atau mematikan fungsi icon mask, dan juga dapat menggunakan berbagai bentuk mask yang diinginkan.

### Cara Menggunakan Icon Mask

Tambahkan ke dalam Info.Plist
```xml
       <key>IB-MaskIcons</key>
    <true/>
```
Sehingga menjadi:
```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
  <dict>
       <key>IB-MaskIcons</key>
    <true/>
    <key>PackageName</key>
    <string>ThemeName</string>
    <key>ThemeType</key>
    <string>Icons</string>
    </dict>
  </plist>
```

### Membuat Mask

Yaitu dengan cara membuat kotak 512x512px dengan background transparan. Area yang akan disembunyikan diberi warna transparan, sedangkan area yang ingin tetap ditampilkan diberi warna hitam (#000000ff)

### Menyimpan Mask

Buat folder `Bundles` dalam folder `NamaTema.theme`
```
  NamaTema.theme/
    IconBundles/
    Bundles/
```
Lalu tambahkan folder `com.apple.mobileicons.framework` ke dalam folde `Bundles`
```
  NamaTema.theme/
    IconBundles/
    Bundles/
      com.apple.mobileicons.framework
```
Berikut ini adalah nama file dan resolusi yang harus disimpan untuk file mask

|Filename|Resolution|
|----|-----|
|AppIconMask@2x~ipad.png|512x512|
|AppIconMask@2x~iphone.png|120x120|
|AppIconMask@3x~ipad.png|180x180|
|AppIconMask@3x~iphone.png|180x180|
|AppIconMask~ipad.png|76x76|
|DocumentBadgeMask-20\@2x.png|40x40|
|DocumentBadgeMask-145\@2x.png|145x145|
|GameAppIconMask\@2x.png|84x84|
|NotificationAppIconMask\@2x.png|40x40|
|NotificationAppIconMask\@3x.png|60x60|
|SpotlightAppIconMask\@2x.png|80x80|
|SpotlightAppIconMask\@3x.png|120x120|
|TableIconMask\@2x.png|58x58|
|TableIconOutline\@2x.png|58x58|

Jadi folder `com.apple.mobileicons.framework` akan berisi:
```
  NamaTema.theme/
    Bundles/
      com.apple.mobileicons.framework
        AppIconMask@2x~ipad.png
        AppIconMask@2x~iphone.png
        AppIconMask@3x~ipad.png
        AppIconMask@3x~iphone.png
        AppIconMask~ipad.png
        DocumentBadgeMask-145@2x.png
        DocumentBadgeMask-20@2x.png
        GameAppIconMask@2x.png
        NotificationAppIconMask@2x.png
        NotificationAppIconMask@3x.png
        SpotlightAppIconMask@2x.png
        SpotlightAppIconMask@3x.png
        TableIconMask@2x.png
        TableIconOutline@2x.png
```

### Compile untuk Cydia

Membuat tema yang telah dibuat menjadi file `.deb` format untuk Cydia. Dengan cara membuat folder baru dengan nama tanpa spasi atau karakter khusus. Misalnya, nama foldernya adalah `NamaTemaUntukCydia`
```
NamaTemaUntukCydia/
```
Lalu tambahkan folder DEBIAN di dalamnya
```
NamaTemaUntukCydia/
  DEBIAN/
```
Kemudian, buat file `control` ke dalam folder `DEBIAN`. File `control` berguna untuk memberikan informasi tentang tema yang dibuat. Termasuk nama tema dan deskripsi.
```
NamaTemaUntukCydia/
  DEBIAN/
    control
```
Buka dan edit file `control`, ubah yang ada di dalam tanda kurung.
```text
Package: com.(yourname).(themename)
Name: (Theme Name)
Version: (1.0)
Architecture: iphoneos-arm
Description: (A theme with beautiful icons!)
Author: (Your Name)
Maintainer: (Your Name)
Section: Themes
Depends: com.anemonetheming.anemone | com.spark.snowboard
```

Catatan!
`Package` harus dalam lowercase
`Version` harus diganti setiap kali mengupdate tema
File `control` harus memiliki beberapa baris kosong di bawah

### Menambahkan Tema ke Package

Buat folder `Library`
```
NamaTemaUntukCydia/
  DEBIAN/
  Library/
```
Buat folder `Themes` di dalam folder `Library`
```
NamaTemaUntukCydia/
  DEBIAN/
  Library/
    Themes/
```
Tambahkan folder `NamaTema.theme` yang telah dibuat di awal ke dalam folder `Themes`.
```
NamaTemaUntukCydia/
  DEBIAN/
  Library/
    Themes/
      NamaTema.theme/
```

### Hampir Selesai

Sekarang waktunya mengubah folder menjadi `.deb` package. SSH ke iOS.
Buka file exporer, lalu klik `Other Location` dan masukkan alamat `sftp://root@ip_iphone`

Copy folder `NamaTemaUntukCydia` ke dalam iOS `/var/mobile/Documents`
```
ssh - iPhone
  var/
    mobile/
      Documents/
        NamaTemaUntukCydia/
```

Buka terminal hubungkan komputer dengan iOS melalui ssh, lalu jalankan perintah:
```sh
 dpkg -b /var/mobile/Documents/NamaTemaUntukCydia
```
 Jika proses sudah selesai, maka akan muncul file `NamaTemaUntukCydia.deb`. Pindahkan file `.deb` ke komputer dan hapus folder `NamaTemaUntukCydia` dari perangkat iOS.
 
### Alhamdulillah Selesai
 
 
### Referensi

https://pinpal.github.io/theme-guide/
