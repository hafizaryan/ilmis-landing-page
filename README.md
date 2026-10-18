# ILMIS Landing Page

Halaman landing (landing page) untuk ILMIS, Integrated Laboratory Information System, yaitu sistem informasi laboratorium terpadu. Situs ini bersifat statis dan berperan sebagai halaman muka sebelum pengguna masuk ke aplikasi utama.

## Isi Halaman

- `index.html`, halaman utama (homepage) ILMIS
- `pilih-login.html`, halaman pemilihan jenis login pengguna
- `service-details.html`, halaman detail layanan
- `starter-page.html`, halaman awal contoh dari template
- Folder `assets` berisi CSS, JavaScript, gambar, dan library vendor pendukung template
- Folder `forms` berisi handler form kontak PHP bawaan template

Catatan: form kontak pada template ini membutuhkan library PHP Email Form versi pro dari penyedia template, dan library tersebut tidak disertakan dalam repositori, sehingga form kontak tidak aktif secara bawaan.

## Teknologi

- HTML
- CSS
- JavaScript
- PHP untuk handler form kontak bawaan template

## Struktur Proyek

```text
ilmis-landing-page/
├── assets/               # CSS, JavaScript, gambar, dan vendor template
├── forms/contact.php     # Handler form kontak bawaan template
├── index.html            # Halaman utama
├── pilih-login.html      # Halaman pilih login
├── service-details.html  # Halaman detail layanan
└── starter-page.html     # Halaman starter template
```

## Cara Menjalankan

Buka berkas `index.html` di browser, atau jalankan dengan ekstensi Live Server di editor.

## Proyek Terkait

Repositori `sitaris` berisi aplikasi Sistem Informasi Inventaris Laboratorium yang berkaitan dengan sistem laboratorium ini.
