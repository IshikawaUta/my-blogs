---
title: Membuat Website Portofolio Dengan Jekyll Theme
date: 2026-02-25 18:00:00 +0700
categories: [Teknologi, Tutorial]
tags: [jekyll, theme, tutorial]
pin: true
image:
  path: https://raw.githubusercontent.com/IshikawaUta/jekyll-uta-folio/refs/heads/main/assets/img/bg-wht.png
  alt: Gambar Demo Project.
comments: true
---

# 🚀 Jekyll Uta Folio - Modern Gradient Theme

Tema portofolio Jekyll yang modern, responsif, dan sangat ringan. Dirancang khusus untuk developer dan kreatif yang menginginkan tampilan profesional dengan **Tailwind CSS**, tanpa perlu setup Node.js yang rumit.

[![Use this template](https://img.shields.io/badge/Use_this_template-238636?style=for-the-badge&logo=github&logoColor=white)](https://github.com/new?template_name=jekyll-uta-folio&template_owner=IshikawaUta)

---

## ✨ Fitur Utama
* 🎨 **Desain Modern & Glassmorphism**: Estetika premium dengan aksen gradient indigo & purple.
* 🌓 **Dark Mode Ready**: Mendukung mode gelap otomatis sesuai sistem atau toggle manual.
* 📲 **WhatsApp Contact Integration**: Pengunjung bisa mengirim pesan langsung ke WA tanpa backend.
* ⚡ **Ultra Fast**: Menggunakan Tailwind CSS via CDN dan nol framework JavaScript berat.
* 📂 **Collection-Based Projects**: Kelola portofolio Anda dengan mudah melalui file Markdown.
* 🧩 **Zero Configuration Pages**: Halaman About, Contact, dan Project sudah termasuk dalam tema.

---

## 📂 Struktur Folder Tema
Untuk bekerja sebagai tema, pastikan struktur folder Anda mengikuti standar berikut:
```text
.
├── _layouts/          # Template (default, page, post, project)
├── _projects/         # Tempat file .md karya Anda
├── assets/            # File gambar dan aset statis
├── _config.yml        # Pusat pengaturan konten & profile
├── index.md           # Halaman utama (Dinamis)
├── about.md           # Halaman tentang saya (Dinamis)
└── contact.md         # Halaman kontak (WhatsApp ready)
```

---

## 🚀 Memulai (Quick Start)

Gunakan metode ini jika Anda ingin membuat portofolio baru dengan cepat tanpa harus melakukan fork manual:

1. **Gunakan Template**: Klik tombol hijau **"Use this template"** di bagian atas halaman repositori ini.
2. **Buat Repositori Baru**: Pilih akun pemilik dan beri nama repositori Anda (contoh: `my-portfolio`).
3. **Konfigurasi**: Buka file `_config.yml` dan sesuaikan data diri Anda:
   - Ubah `author.name`, `author.role`, dan `author.whatsapp`.
   - Sesuaikan `email` dan `url` situs Anda.
4. **Aktifkan GitHub Pages**:
   - Masuk ke tab **Settings** > **Pages** di repositori baru Anda.
   - Pada bagian **Build and deployment**, pilih source "GitHub Actions".
5. **Selesai**: Tunggu proses build selesai, dan portofolio Anda siap diakses!

---

## 🚀 Cara Instalasi

### Sebagai Remote Theme (GitHub Pages)

Jika Anda menggunakan GitHub Pages, ini adalah cara tercepat:

1. Tambahkan plugin `jekyll-remote-theme` ke `Gemfile` Anda:
```ruby
group :jekyll_plugins do
  gem "jekyll-remote-theme"
end
```


2. Di file `_config.yml` Anda, tambahkan:
```yaml
remote_theme: ishikawauta/jekyll-uta-folio
plugins:
  - jekyll-remote-theme
  - jekyll-seo-tag
  - jekyll-feed
```



### Sebagai Gem-based Theme

1. Tambahkan baris berikut ke `Gemfile` proyek Jekyll Anda:
```ruby
gem "jekyll-uta-folio"
```


2. Jalankan:
```bash
bundle install
```


3. Tambahkan di `_config.yml`:
```yaml
theme: jekyll-uta-folio
```



---

## ⚙️ Kustomisasi (The Magic of _config.yml)

Keunggulan tema ini adalah Anda tidak perlu menyentuh kode HTML. Cukup edit `_config.yml`:

```yaml
# Profil Penulis
author:
  name: "Nama Anda"
  role: "Pekerjaan Anda"
  whatsapp: "62895xxxxx" # Kode negara tanpa +
  image: "/assets/images/profile.jpg"

# Pengaturan Hero Section
hero_title: "Membangun Masa Depan Lewat Baris Kode."
hero_description: "Halo! Saya [name], seorang [role] yang fokus pada web."

# Daftar Keahlian (Skills)
skills:
  - name: "Web Development"
    icon: "💻"
    description: "HTML5, CSS3, JavaScript, dan React."
```

---

## 📄 Lisensi

Proyek ini dilisensikan di bawah [**MIT License**](https://github.com/IshikawaUta/jekyll-uta-folio/blob/main/LICENSE). Anda bebas menggunakan, memodifikasi, dan mendistribusikannya kembali.