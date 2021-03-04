---
title: "Ubuntu Useful Packages"
description: "Daftar Packages Ubuntu yang aku rekomendasikan, beserta penggunaannya"
date: 2020-01-28T00:34:39+09:00
draft: false
weight: 1
collapsible: false
---

## Daftar Package yang aku rekomendasikan

Berikut ini adalah beberapa program yang saya rekomendasikan. Beberapa berupa GUI dan beberapa berupa command line. Daftar aplikasi diurutkan sesuai dengan alfabet.

### apt
Aptitude

Penggunaan:
- sudo apt update
- sudo apt -y upgrade
- sudo apt -y dist-upgrade
- sudo apt -y autoremove
- sudo apt install &lt;package&gt;
- sudo apt install &lt;package&gt;=&lt;version&gt;
- apt-cache showpkg &lt;package-name&gt;

### bash

Bourne Again Shell, command language interpreter. Perintah di terminal Ubuntu menggunakan Bash

Penggunaan:

chmod +x nama_file && bash nama_file
Mengubah file agar bisa dieksekusi menggunakan Bash.
cd dir \
&& rm file \
&& mkdir /new
Menggunakan backslash (\) agar skrip mudah dibaca.

### ffmpeg
ffmpeg; solution to record, convert and stream audio and video

Penggunaan:

ffmpeg -i "concat:a.mp3|b.mp3" -acodec copy c.mp3
Menggabungkan file audio a.mp3 dan b.mp3 menjadi c.mp3
ffmpeg -ss 00:00:00 -t 00:01:00 -i input.avi -vcodec copy -acodec copy output.avi
Menyalin video dan audio dari file input.avi dari detik ke 0 dengan durasi satu menit.
ffmpeg -i input.m4a -c:a libmp3lame -q:a 8 output.mp3
Mengonversi file audio m4a menjadi mp3.
gnome-shell
Graphical shell for the GNOME desktop

Penggunaan:

sudo apt install gnome-shell
Memasang gnome-shell
gnome-shell-extension
Extensions to extend functionality of GNOME Shell

Penggunaan:

sudo apt install gnome-shell-extension
Memansang gnome-shell-extension
Internet speed meter, Openweather,
Ini adalah beberapa ekstensi yang saya rekomendasikan.
gnome-tweak-tool
Adjust advanced settings for GNOME - transitional package

Penggunaan:

sudo apt install gnome-tweak-tool
Memasang gnome-tweak-tool
gtts
gtts, google to text speech. Mengubah teks menjadi file audio.

Penggunaan:

sudo apt install gtts
Menginstall gTTS
gtts-cli "Hello World" --lang en --output hello.mp3
Mengubah teks “Hello World” menjadi file audio dan menyimpannya dalam file hello.mp3
gtts-cli "Hello World" --lang en --output hello.mp3 && mpg123 hello.mp3
Membuat, menyimpan, dan memainkan file hello.mp3
hugo
Fast and flexible Static Site Generator written in Go

Penggunaan:

hugo new hugo blog
Membuat situs dengan nama blog
cd /dir/hugo && hugo server -D
Mengaktifkan server hugo
inkscape
Desain grafis 2D dengan ekstensi SVG

Penggunaan:

sudo apt install inkscape
Menginstall Inkscape
kdenlive
non-linear video editor

Penggunaan:

sudo apt install kdenlive
Memasang kdenlive
mpg123
mpg123, memutar audio dari terminal.

Penggunaan:

mpg123 lagu.mp3
Memutar file lagu.mp3.
mpg123 *.mp3
Memutar semua file yang berekstensi .mp3.
ssh username@my-remote-machine-address && mpg123 -Z --@ < myplaylistfile
Memutar file yang berada di perangkat lain.
openssh-server
OpenSSH is the premier connectivity tool for remote login with the SSH protocol.

Penggunaan:

sudo apt install openssh-server
Memasang openssh.
sftp://root@192.168.1.3/
Contoh mengakses perangkat dengan menggunakan File Explorer.


### Spotdl
Mengunduh file dari Spotify

web: https://github.com/spotDL/spotify-downloader

```bash
# Mengunduh lagu
spotdl [trackUrl]

# Mengunduh lagu-lagu dalam album
spotdl [albumUrl]

# Mengunduh lagu-lagu dalam playlist
spotdl [playlistUrl]

# Melanjutkan unduhan yang gagal atau belum selesai:
spotdl 'Didi Kempot - Bojo Loro.spotdlTrackingFile'

# Queue (antrian)
spotdl [songQuery1] [albumUrl] [songQuery2] ... (order does not matter)
```

python-is-python3
Symlinks /usr/bin/python to python3

Penggunaan:

sudo apt install python-is-python3
Mengatasi error pada youtube-dl
/usr/bin/env: ‘python’: No such file or directory
terminator
Terminal yang lebih canggih.

Penggunaan:

sudo apt install x-terminal-emulator
Menginstall Terminator.
timidity-daemon
runs TiMidity++ as a system-wide MIDI sequencer

Penggunaan:

sudo apt purge timidity-daemon
Mengatasi Dummy Output, Ubuntu 20.04 yang tidak mengeluarkan suara.
wallch
Wallpaper changer

Penggunaan:

sudo apt install wallch
Memasang Wallch
youtube-dl
Mengunduh file video atau audio dari Youtube

Penggunaan:

sudo apt install youtube-dl
Memasang Youtube Downloader
youtube-dl htpp://url -x
Mengunduh dan mengekstrak video dari Youtube menjadi audio saja.
apt
bash
ffmpeg
gnome-shell
gnome-shell-extension
gnome-tweak-tool
gtts
hugo
inkscape
kdenlive
mpg123
openssh-server
python-is-python3
terminator
timidity-daemon
wallch
youtube-dl
