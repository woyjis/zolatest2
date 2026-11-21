+++
title = "Kenapa Website Statis"
date = 2026-01-24
description = "Perbandingan singkat website statis versus stack dengan backend dan database, dan kapan masing-masing cocok dipakai."
draft = false
+++

Website statis adalah kumpulan file HTML, CSS, dan aset yang sudah jadi sebelum ada permintaan dari pengunjung. Tidak ada query database saat halaman diakses, tidak ada proses render di server pada setiap request.

## Kapan statis cukup

Website statis cocok untuk:

- Blog, dokumentasi, dan halaman marketing yang isinya jarang berubah secara real-time.
- Situs yang ingin dihosting murah atau bahkan gratis lewat CDN/static hosting.
- Proyek yang ingin menghindari ketergantungan pada database seperti PostgreSQL atau layanan seperti Supabase.

## Kapan perlu backend

Kalau butuh data personal per pengguna, transaksi, atau pembaruan konten yang sangat sering dari banyak penulis sekaligus secara kolaboratif real-time, static site generator biasa bukan pilihan ideal sendirian — biasanya dikombinasikan dengan API terpisah.

Untuk demo ini, kombinasi Zola (generator statis) dan Sveltia CMS (editor berbasis browser dengan backend `test-repo`) cukup untuk menunjukkan alur menulis dan membaca artikel tanpa server tambahan apa pun.
