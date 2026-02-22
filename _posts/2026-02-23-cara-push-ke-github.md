---
title: Cara Push Proyek Lokal ke GitHub
date: 2026-02-22 21:00:00 +0700
categories: [Teknologi, Tutorial]
tags: [git, github, tutorial]
pin: true
image:
  path: https://miro.medium.com/v2/resize:fit:720/format:webp/0*DIm2MFmfMytxg8wW.png
  alt: Panduan Git dan GitHub.
comments: true
---

# 🚀 Panduan Lengkap Git & GitHub

Panduan ini mencakup seluruh alur kerja, mulai dari pengaturan identitas hingga mengirim kode ke repositori remote.

## 1. Konfigurasi Identitas (Satu Kali)

Langkah pertama agar Git tahu siapa yang melakukan perubahan.

```bash
git config --global user.name "Nama Kamu"
git config --global user.email "email@kamu.com"
```

---

## 2. Inisialisasi Proyek (Lokal)

Jalankan perintah ini di dalam folder proyek kamu jika belum ada folder `.git`.

```bash
# Masuk ke folder proyek
cd nama-proyek-kamu

# Inisialisasi git
git init

# (Opsional) Mengubah branch default menjadi main
git branch -M main
```

---

## 3. Menghubungkan ke GitHub

Pastikan kamu sudah membuat repository kosong di GitHub, lalu salin URL-nya.

```bash
# Menambahkan alamat remote repository
git remote add origin https://github.com/username/nama-repo.git

# Verifikasi koneksi remote
git remote -v
```

---

## 4. Alur Kerja Rutin (The Big Three)

Gunakan urutan ini setiap kali kamu selesai melakukan perubahan pada kode.

### A. Menandai Perubahan

Pilih file mana yang ingin dimasukkan ke dalam "keranjang" (Staging Area).

```bash
# Menambahkan semua file yang berubah
git add .

# ATAU menambahkan file tertentu saja
git add nama_file.php
```

### B. Menyimpan Perubahan (Commit)

Berikan pesan singkat tentang apa yang kamu ubah.

```bash
git commit -m "Fitur: Menambahkan halaman login"
```

### C. Mengirim ke GitHub (Push)

Kirim hasil kerja kerasmu ke server GitHub.

```bash
git push origin main
```

---

## 5. Perintah Berguna Lainnya

| Perintah | Fungsi |
| --- | --- |
| `git status` | Melihat file mana yang sudah di-add atau belum. |
| `git log` | Melihat riwayat commit (siapa, kapan, dan pesan apa). |
| `git pull origin main` | Mengambil update terbaru dari GitHub ke laptop. |
| `git diff` | Melihat detail baris kode mana yang berubah. |
| `git remote set-url origin <URL>` | Mengubah alamat URL repository jika salah. |

---

## 💡 Tips Tambahan: File `.gitignore`

Sangat disarankan untuk membuat file bernama `.gitignore` di folder utama agar file sampah tidak ikut ter-upload. Contoh isinya:

```text
# Mengabaikan folder library/dependensi
node_modules/
vendor/

# Mengabaikan file konfigurasi rahasia
.env

# Mengabaikan file sistem
.DS_Store
Thumbs.db
```