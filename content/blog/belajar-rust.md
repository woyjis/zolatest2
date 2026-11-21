+++
title = "Belajar Rust Lewat Zola"
date = 2026-01-17
description = "Zola ditulis dalam Rust dan dibagikan sebagai satu binary — ini kenapa itu penting untuk demo situs statis ini."
draft = false
+++

Zola sendiri ditulis dalam [Rust](https://www.rust-lang.org/) dan dibagikan sebagai satu binary tunggal. Tidak ada runtime Node.js, tidak ada dependency manager yang perlu disetup — cukup unduh satu file dan jalankan.

## Kenapa ini relevan buat blog ini

Karena Zola adalah binary tunggal:

- `zola build` menghasilkan folder `public/` berisi HTML statis murni.
- `zola serve` menjalankan server pratinjau lokal dengan live reload.
- `zola check` memverifikasi semua link internal dan konten valid tanpa benar-benar membangun output.

## Templating dengan Tera

Zola memakai [Tera](https://keats.github.io/tera/), mesin template mirip Jinja2, untuk file-file di folder `templates/`. Template `base.html` menjadi kerangka dasar, lalu `index.html`, `section.html`, dan `page.html` saling `extends` dari situ.

Kombinasi Rust + Tera inilah yang membuat Zola cepat dibangun dan cepat disajikan, cocok untuk demo blog sederhana seperti ini.
