---
title: Panduan Lengkap Install Jekyll di Windows/Linux
date: 2026-02-22 17:30:00 +0700
categories: [Teknologi, Tutorial]
tags: [jekyll, ruby, web-development, tutorial]
pin: true
image:
  path: https://raw.githubusercontent.com/jekyll/brand/refs/heads/master/jekyll-logo-light-solid.png
  alt: Logo Jekyll.
comments: true
---

## Persiapan Instalasi Jekyll

Setelah sebelumnya saya memperkenalkan blog ini, banyak yang penasaran: *Bagaimana sih cara membangun blog statis menggunakan Jekyll?* Jekyll adalah generator situs statis yang dibangun dengan bahasa pemrograman **Ruby**. Sebelum bisa menjalankan tema seperti **Chirpy**, kamu perlu menyiapkan lingkungan (environment) di perangkatmu.

---

### 1. Prasyarat (Prerequisites)

Sebelum melangkah lebih jauh, pastikan kamu sudah menginstal komponen dasar berikut:
* **Ruby**: Bahasa utama penggerak Jekyll.
* **RubyGems**: Package manager untuk Ruby.
* **GCC dan Make**: Dibutuhkan untuk mengompilasi beberapa library.

### 2. Langkah-Langkah Instalasi

Tergantung sistem operasi yang kamu gunakan, ikuti perintah di bawah ini melalui Terminal atau Command Prompt:

#### **Untuk Pengguna Linux (Ubuntu/Debian)**
```bash
# Update package list
sudo apt update

# Install Ruby dan dependencies
sudo apt install ruby-full build-essential zlib1g-dev

# Konfigurasi path agar tidak perlu sudo saat install gem
echo '# Install Ruby Gems to ~/gems' >> ~/.bashrc
echo 'export GEM_HOME="$HOME/gems"' >> ~/.bashrc
echo 'export PATH="$HOME/gems/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
```

#### **Untuk Pengguna Windows**

Cara termudah adalah menggunakan **RubyInstaller for Windows**:

1. Download di [rubyinstaller.org](https://rubyinstaller.org/).
2. Pilih versi **Ruby+Devkit**.
3. Jalankan `ridk install` pada langkah terakhir instalasi untuk mengonfigurasi MSYS2.

---

### 3. Menginstal Jekyll dan Bundler

Setelah Ruby siap, saatnya menginstal bintang utamanya:

```bash
gem install jekyll bundler
```

> **Catatan:** Jika kamu menggunakan Linux tanpa konfigurasi path di atas, kamu mungkin perlu menggunakan `sudo`, namun sangat disarankan untuk menggunakan konfigurasi user-path agar lebih aman.
> {: .prompt-info }

### 4. Membuat Blog Pertama Kamu

Sekarang, mari kita tes apakah semuanya berjalan lancar dengan membuat proyek baru:

```bash
# Buat proyek baru bernama 'myblog'
jekyll new myblog

# Masuk ke direktori
cd myblog

# Jalankan server lokal
bundle exec jekyll serve
```

Buka browsermu di alamat `http://localhost:4000`. Jika muncul halaman default Jekyll, selamat! Kamu sudah berhasil.

---

### Mengapa Menggunakan Jekyll?

Berdasarkan pengalaman saya membangun blog ini:

1. **Kecepatan**: Tidak ada database, hanya file HTML statis yang sangat ringan.
2. **Keamanan**: Tanpa database berarti tidak ada celah SQL Injection.
3. **Gratis Hosting**: Bisa langsung di-deploy ke **GitHub Pages** tanpa biaya sepeser pun.

### Apa Selanjutnya?

Setelah berhasil menginstal Jekyll, langkah berikutnya adalah memasang tema keren seperti **Chirpy** agar tampilan blogmu terlihat profesional seperti blog IshikawaUta ini.
