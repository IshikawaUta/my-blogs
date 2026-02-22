---
title: "Panduan Deploy Jekyll: Menggunakan Docker dan Cloudflare Tunnel"
date: 2026-02-23 00:30:00 +0700
categories: [Teknologi, Tutorial]
tags: [jekyll, docker, cloudflare, tutorial]
pin: true
image:
  path: https://miro.medium.com/v2/resize:fit:1100/format:webp/1*Eci7tXrSQNgCW2isfiLPDA.jpeg
  alt: Logo cloudflare.
comments: true
---

Punya project Jekyll di lokal dan ingin mempublikasikannya ke internet tanpa pusing urusan port forwarding atau konfigurasi Nginx yang ribet? 

Kombinasi **Docker** dan **Cloudflare Tunnel** adalah solusi "set and forget" yang sangat aman. Kamu tidak perlu membuka port di router, dan situsmu akan terlindungi oleh infrastruktur Cloudflare.

## Persiapan
Sebelum mulai, pastikan kamu sudah menginstal:
1. **Docker** & **Docker Compose**
2. Akun **Cloudflare** dengan domain yang sudah aktif.

---

## 1. Struktur File
Pastikan struktur direktori project Jekyll kamu terlihat seperti ini:

```text
my-jekyll-site/
├── _posts/
├── _config.yml
├── Gemfile
├── Dockerfile
└── docker-compose.yml
```

---

## 2. Membuat Dockerfile

Kita akan menggunakan Dockerfile yang efisien untuk melakukan *build* Jekyll dan menyajikannya.

```dockerfile
# Gunakan image ruby yang ringan
FROM ruby:3.2-slim

# Install dependencies sistem
RUN apt-get update && apt-get install -y \
    build-essential \
    git \
    && rm -rf /var/lib/apt/lists/*

# Set working directory
WORKDIR /srv/jekyll

# Copy Gemfile
COPY Gemfile* ./
RUN bundle install

# Copy seluruh project
COPY . .

# Jalankan Jekyll secara default
CMD ["bundle", "exec", "jekyll", "serve", "--host", "0.0.0.0"]
```

---

## 3. Konfigurasi Docker Compose

Di sini kita akan menjalankan dua layanan: **jekyll** (aplikasi kita) dan **tunnel** (jembatan ke internet).

```yaml
version: '3.8'

services:
  jekyll:
    build: .
    volumes:
      - .:/srv/jekyll
    ports:
      - "4000:4000"

  tunnel:
    image: cloudflare/cloudflared:latest
    restart: always
    command: tunnel --no-autoupdate run --token ${CF_TUNNEL_TOKEN}
    depends_on:
      - jekyll
```

> **Catatan:** `${CF_TUNNEL_TOKEN}` akan kita ambil dari dashboard Cloudflare.

---

## 4. Setup Cloudflare Tunnel

1. Buka [Cloudflare Zero Trust Dashboard](https://one.dash.cloudflare.com/).
2. Pergi ke **Networks** > **Tunnels** > **Create a Tunnel**.
3. Beri nama tunnel kamu (misal: `jekyll-home-server`) dan Save.
4. Di bagian **Install connector**, pilih Docker. Kamu akan melihat kode token yang panjang. Ambil bagian tokennya saja.
5. Di bagian **Route**, masukkan:
* **Public Hostname:** `blog.domainkamu.com`
* **Service Type:** `HTTP`
* **URL:** `jekyll:4000` (Gunakan nama service docker, bukan localhost).



---

## 5. Menjalankan Project

Buat file `.env` di folder yang sama untuk menyimpan token agar aman:

```bash
CF_TUNNEL_TOKEN=masukkan_token_cloudflare_disini
```

Sekarang, jalankan perintah sakti:

```bash
docker-compose up -d
```

---

## Kesimpulan

Situs Jekyll kamu sekarang sudah online! Docker menangani lingkungan Ruby yang seringkali merepotkan, sementara Cloudflare Tunnel menangani keamanan dan akses publik tanpa perlu mengekspos IP publik rumah/server kamu.