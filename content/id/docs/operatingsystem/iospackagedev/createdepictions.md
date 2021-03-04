---
title: "Menambahkan Halaman Depiction"
description: "Menggunakan Depiction untuk memperbaiki tampilan di Cydia"
date: 2020-01-29T00:36:19+09:00
draft: false
---

# Fungsi Depictions

Dengan adanya halaman depictions, dapat mengubah tampilan pada repo Cydia menggunakan CSS dan JS. Dan depiction, juga berguna untuk menambahkan elemen yang diperlukan dan yang ingin ditampilkan.

## Struktuf folder

```
cydia/
  debs/
  depictions/
    com.name.package1/
      screenshots/
        image.png
      changelog.xml
      info.xml
    com.name.package2/
    js/
    changelog.hmtl
    index.html
    screenshot.html
    style.css
  Release
  etc...
```

## File yang harus diedit

File yang harus diedit:
- /cydia/depiction/com.name.package/changelog.xml
- /cydia/depiction/com.name.package/info.xml
- /cydia/depiction/com.name.package/screenshot/image.png
- /theme/com.name.package/DEBIAN/control

tambahkan :
`Depiction: https://kva.github.io/cydia/depictions/?p=com.name.package`

ke dalam file `control`.
Misalnya: 
```
Package: com.kva.whiteoutline
Name: White Outline
Version: 1.4
Architecture: iphoneos-arm
Description: Outline icons with white color
Author: kva <herusularto@gmail.com>
Section: Themes
Depends: com.anemonetheming.anemone, com.spark.snowboard
Depiction: https://kva.github.io/cydia/depictions/?p=com.kva.whiteoutline
```

## Rebuilding Packages file

Setelah file `control` diperbarui, build tweak/theme. Simpan file `.deb` ke dalam folder /debs di dalam repo. Build `Packages` file dan kompres dengan bzip2.

```bash
cd repo
dpkg-scanpackages -m ./debs > Packages
bzip2 Packages
```

## Push ke Github. 
Alhamdulillah, selesai.

## Referensi

[github.com/supermamon/Reposi3](https://github.com/supermamon/Reposi3)
