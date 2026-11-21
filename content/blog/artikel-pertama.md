+++
title = "Artikel Pertama"
date = 2026-01-10
description = "Catatan pembuka blog ini: kenapa dibangun dengan Zola dan bagaimana isinya dikelola lewat Sveltia CMS."
draft = false
+++

Ini adalah artikel pertama di blog demo ini. Situs ini dibangun dengan [Zola](https://www.getzola.org/), generator situs statis yang ditulis dalam Rust, dan kontennya dikelola lewat [Sveltia CMS](https://github.com/sveltia/sveltia-cms) — editor rich-text berbasis browser yang bisa dijalankan tanpa server Node.js tambahan.

## Mengapa situs statis

Situs statis punya beberapa keuntungan dibanding stack dengan database dan backend:

- Tidak ada server aplikasi yang perlu dijaga uptime-nya.
- Setiap halaman sudah berupa HTML jadi, jadi sangat cepat disajikan.
- Isi kontennya disimpan sebagai file Markdown biasa yang mudah dibaca dan diaudit.

## Bagaimana Sveltia CMS masuk ke alur ini

Sveltia CMS memberi antarmuka editor di `/admin/` tanpa memaksa kita memasang backend seperti PostgreSQL atau Supabase. Dalam demo ini CMS memakai backend `test-repo`, yang berarti perubahan tersimpan di penyimpanan browser (local storage) saja, bukan ditulis balik ke file Markdown di repo. Ini cocok untuk mencoba-coba editor tanpa menyentuh git.

Artikel berikutnya akan membahas Rust dan cara kerja situs statis ini secara teknis.
