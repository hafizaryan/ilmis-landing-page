# ILMIS Landing Page

Landing page statis untuk **ILMIS (Integrated Laboratory Management Information System)**, yaitu halaman muka Laboratorium Program Studi Sistem Informasi, Fakultas Sains dan Teknologi, UIN Sultan Syarif Kasim Riau.

Halaman ini bukan aplikasi laboratorium itu sendiri. Tugasnya memperkenalkan laboratorium dan sistem yang terintegrasi, lalu mengarahkan pengguna ke halaman pemilihan aplikasi. Seluruh halaman dibangun dengan HTML, CSS, dan JavaScript tanpa proses build.

> **Status:** situs statis. Tidak ada `package.json`, bundler, framework JavaScript, database, test suite, linter, formatter, atau pipeline CI di repositori ini.

## Daftar Isi

- [Halaman yang Tersedia](#halaman-yang-tersedia)
- [Fitur per Halaman](#fitur-per-halaman)
- [Teknologi](#teknologi)
- [Struktur Proyek](#struktur-proyek)
- [Menjalankan Secara Lokal](#menjalankan-secara-lokal)
- [Konfigurasi dan Kustomisasi](#konfigurasi-dan-kustomisasi)
- [Catatan CSS dan JavaScript](#catatan-css-dan-javascript)
- [Deployment](#deployment)
- [Batasan dan Known Issues](#batasan-dan-known-issues)
- [Alur Kerja Perubahan](#alur-kerja-perubahan)
- [Lisensi dan Atribusi](#lisensi-dan-atribusi)
- [Proyek Terkait](#proyek-terkait)

## Halaman yang Tersedia

| Berkas | Status | Fungsi |
| --- | --- | --- |
| `index.html` | Halaman utama | Homepage ILMIS: hero, statistik, daftar sistem, FAQ, kontak, dan footer. Tombol **Login** membuka `pilih-login.html` di tab baru. |
| `pilih-login.html` | Halaman aktif | Halaman "Pilih Aplikasi" berisi tautan ke LAB-SI, SITARIS, LABVIS, dan LARIS. Halaman ini berdiri sendiri dan memakai stylesheet sendiri. |
| `service-details.html` | Tidak ditautkan | Halaman contoh detail layanan dari template. Isinya masih teks contoh dan tidak bisa diakses dari navigasi situs. |
| `starter-page.html` | Tidak ditautkan | Halaman starter kosong dari template, berguna sebagai titik awal halaman baru. |
| `forms/contact.php` | Tidak aktif | Handler form kontak bawaan template. Membutuhkan library PHP Email Form versi pro yang tidak disertakan. |

Catatan: `service-details.html` dan `starter-page.html` adalah sisa template. Jangan menganggap keduanya halaman produksi tanpa menautkannya terlebih dahulu.

## Fitur per Halaman

### `index.html`

Navigasi utama berisi tautan ke `#hero`, `#services`, `#faq`, dan `#contact`. Tautan About dan Features masih dikomentari.

- **Hero** — judul ILMIS, sapaan laboratorium, gambar `assets/img/uin-suska.jpeg`, dan tombol "Lihat Lebih Lanjut".
- **Statistik** — empat angka animasi PureCounter: 503 Barang, 5 Sistem, 4 Pendanaan, dan 7 Dokumentasi.
- **Sistem Terintegrasi** — empat kartu layanan: LAB SI Website, SITARIS (inventaris), LABVIS (pengunjung laboratorium), dan LARIS (registrasi asisten laboratorium). Tautan "Selengkapnya" pada kartu masih mengarah ke `#`.
- **FAQ** — lima pertanyaan dengan accordion yang dibuka/ditutup oleh `assets/js/main.js`.
- **Kontak** — alamat laboratorium, email `sif.labor@uin-suska.ac.id`, peta Google Maps, dan form kontak.
- **Footer** — identitas laboratorium, alamat, email, serta daftar tautan. Sebagian besar tautan footer masih berupa placeholder `#`.

### `pilih-login.html`

Halaman pemilihan aplikasi dengan kartu untuk setiap sistem:

| Aplikasi | Deskripsi | Tujuan tautan |
| --- | --- | --- |
| LAB-SI | Website Laboratorium Program Studi Sistem Informasi | `http://lab-si.uin-suska.ac.id` |
| SITARIS | Laboratory Inventory Information System | `http://sitaris.lab-si.uin-suska.ac.id` |
| LABVIS | Laboratory Visitor Information System | `http://labvis.lab-si.uin-suska.ac.id` |
| LARIS | Laboratory Assistant Registration Information System | `http://laris.lab-si.uin-suska.ac.id` |

Halaman ini memakai `assets/css/style.css`, ikon Font Awesome dari CDN, dan logo di `assets/img/sistem/`. Halaman ini **tidak** memuat Bootstrap, AOS, atau `assets/js/main.js`.

## Teknologi

| Bagian | Keterangan |
| --- | --- |
| Markup | HTML5 |
| Styling | CSS3; `main.css` untuk halaman template, `style.css` untuk halaman pilih aplikasi |
| JavaScript | JavaScript vanilla untuk interaksi halaman; tanpa framework |
| UI framework | Bootstrap 5.3.3 (disertakan di `assets/vendor/bootstrap`) |
| Ikon | Bootstrap Icons (halaman utama) dan Font Awesome 6.0.0-beta3 via CDN (halaman pilih aplikasi) |
| Animasi | AOS, Swiper, GLightbox, dan PureCounter, semuanya disertakan di `assets/vendor` |
| Font | Google Fonts: Roboto, Inter, dan Nunito (dimuat dari CDN di `index.html`) |
| Form handler | PHP, memakai library PHP Email Form versi pro (tidak disertakan) |

Semua library pihak ketiga disimpan langsung di repositori. Tidak ada langkah `npm install` atau kompilasi aset.

## Struktur Proyek

```text
ilmis-landing-page/
├── index.html                  # Homepage ILMIS
├── pilih-login.html            # Halaman pemilihan aplikasi
├── service-details.html        # Contoh halaman detail layanan (tidak ditautkan)
├── starter-page.html           # Halaman starter template (tidak ditautkan)
├── forms/
│   └── contact.php             # Handler form kontak (butuh library pro)
├── assets/
│   ├── css/
│   │   ├── main.css            # CSS utama halaman template
│   │   └── style.css           # CSS khusus pilih-login.html
│   ├── js/
│   │   └── main.js             # Inisialisasi AOS, Swiper, FAQ, scrollspy, dll.
│   ├── img/
│   │   ├── logo.png            # Logo utama dan favicon
│   │   └── sistem/             # Logo LAB-SI, SITARIS, LABVIS, LARIS
│   ├── scss/
│   │   └── Readme.txt          # Sumber SCSS hanya tersedia di versi pro
│   └── vendor/                 # Bootstrap, Bootstrap Icons, AOS, GLightbox,
│                               # Swiper, PureCounter, dan validate.js
├── .gitattributes
├── .gitignore
└── README.md
```

Folder `assets/img` juga masih menyimpan gambar contoh template (misalnya `clients/`, `testimonials/`, `bg.webp`, `bgg.mp4`, dan ilustrasi) yang tidak dipakai oleh halaman saat ini.

## Menjalankan Secara Lokal

Tidak ada proses instalasi atau build. Yang dibutuhkan hanya browser modern.

### Opsi 1: Server statis Python (disarankan)

Jalankan dari **root repositori**, bukan dari dalam `assets`:

```bash
python -m http.server 8000
```

Lalu buka:

- Homepage: <http://localhost:8000/>
- Pilih aplikasi: <http://localhost:8000/pilih-login.html>

Jika port 8000 sudah dipakai, ganti angkanya, misalnya `python -m http.server 8080`.

### Opsi 2: Live Server di editor

Buka folder repositori di VS Code, lalu jalankan ekstensi **Live Server** pada `index.html`. Pastikan server dijalankan dari root repositori agar path `assets/...` tetap valid.

### Opsi 3: Membuka berkas langsung

`index.html` bisa dibuka langsung lewat browser karena semua path aset bersifat relatif. Cara ini cukup untuk melihat tampilan, tetapi tidak menjalankan PHP. Untuk pengujian yang lebih mendekati produksi, tetap gunakan server statis.

### Yang tidak diperlukan

- Tidak ada `npm install`, `composer install`, atau langkah build.
- PHP hanya relevan jika handler form ingin diaktifkan; halaman statis tetap bisa dibuka tanpa PHP.
- Form kontak tidak akan mengirim email pada checkout ini karena library PHP Email Form tidak tersedia (lihat [Batasan dan Known Issues](#batasan-dan-known-issues)).

## Konfigurasi dan Kustomisasi

### Identitas, alamat, dan kontak

Ubah teks di `index.html` pada bagian kontak dan footer. Data yang saat ini dipakai:

- Laboratorium Program Studi Sistem Informasi, Fakultas Sains dan Teknologi, UIN Sultan Syarif Kasim Riau
- Jl. HR. Soebrantas Km. 18, No. 155, Tuahmadani, Tampan, Pekanbaru 28129
- Email: `sif.labor@uin-suska.ac.id`

Peta berada di iframe Google Maps pada section kontak. Ganti URL `src` iframe jika lokasi berubah.

### Statistik homepage

Angka statistik menggunakan atribut PureCounter:

```html
<span
  data-purecounter-start="0"
  data-purecounter-end="503"
  data-purecounter-duration="1"
  class="purecounter"
></span>
```

Ubah `data-purecounter-end` untuk mengganti nilai akhir animasi. Label berada di elemen `<p>` setelahnya.

### Daftar sistem di homepage

Kartu layanan berada di section `#services` pada `index.html`. Setiap kartu memakai struktur `.service-card`. Judul, deskripsi, ikon Bootstrap Icons, dan tautan "Selengkapnya" dapat diubah per kartu. Saat ini tautan tersebut masih placeholder (`href="#"`) dan belum terhubung ke `service-details.html`.

### Halaman pilih aplikasi

Semua tautan aplikasi berada di `pilih-login.html`, di dalam elemen `<a>` yang membungkus `.app-item`. Untuk menambah aplikasi:

1. Tambahkan logo ke `assets/img/sistem/`.
2. Duplikasi satu blok `<a>` beserta `.app-item`.
3. Ganti `href`, `src`, `.app-name`, dan `.app-desc`.

Tautan saat ini memakai `http://`; pertimbangkan `https://` jika seluruh layanan tujuan sudah mendukungnya. Perubahan di halaman ini langsung menentukan tujuan pengguna setelah menekan tombol Login.

### Logo, favicon, dan gambar

- Logo header dan favicon: `assets/img/logo.png`.
- Apple touch icon: `assets/img/apple-touch-icon.png`.
- Logo aplikasi: `assets/img/sistem/labsi.png`, `sitaris.png`, `labvis.png`, `laris.png`.
- Gambar hero: `assets/img/uin-suska.jpeg`.
- Gambar contoh lain di `assets/img` sebagian besar merupakan sisa template dan aman dihapus jika tidak dipakai.

Gunakan nama berkas baru yang deskriptif dan perbarui referensinya di HTML terkait.

### Warna dan font

Warna dan variabel desain utama didefinisikan di bagian `:root` pada `assets/css/main.css`. Font Google dimuat melalui tag `<link>` di `index.html`. Halaman `pilih-login.html` tidak memakai variabel atau font tersebut; gayanya diatur terpisah di `assets/css/style.css`.

### Form kontak

Form di `index.html` mengirim POST ke `forms/contact.php` dengan field `name`, `email`, `subject`, dan `message`.

Agar berfungsi:

1. Letakkan library PHP Email Form versi pro di `assets/vendor/php-email-form/php-email-form.php`.
2. Ganti `$receiving_email_address` di `forms/contact.php`.
3. Buka blok konfigurasi SMTP di berkas yang sama dan isi kredensial yang valid jika server memerlukan SMTP.
4. Jalankan situs di server yang mendukung PHP.

`assets/vendor/php-email-form/validate.js` hanya melakukan validasi di sisi browser. Berkas itu tidak menggantikan handler PHP yang hilang.

Alternatif tanpa PHP adalah mengganti `action` form dengan layanan seperti Formspree atau endpoint backend sendiri, lalu menyesuaikan JavaScript yang menangani status loading/success/error.

## Catatan CSS dan JavaScript

- `assets/css/main.css` adalah CSS hasil kompilasi template. Sumber SCSS tidak disertakan; `assets/scss/` hanya berisi `Readme.txt` yang menjelaskan bahwa SCSS tersedia di versi pro. Edit `main.css` secara langsung dan jangan mengharapkan proses kompilasi Sass.
- `assets/css/style.css` hanya dipakai oleh `pilih-login.html` dan tidak bergantung pada Bootstrap. Jangan mencampur aturan khusus halaman login ke `main.css`.
- `assets/js/main.js` menginisialisasi perilaku template: header saat scroll, navigasi mobile, scroll-to-top, AOS, GLightbox, Swiper, PureCounter, FAQ, hash scroll, dan scrollspy.
- Urutan script di halaman template harus dipertahankan: Bootstrap, `validate.js`, AOS, GLightbox, Swiper, PureCounter, lalu `main.js`.
- `main.js` memanggil `GLightbox(...)` dan `new PureCounter()` secara langsung, serta memanggil `scrollTop.addEventListener(...)` tanpa pengecekan null. Halaman yang memuat `main.js` harus menyertakan library vendor terkait dan elemen `.scroll-top`.
- Konfigurasi Swiper ditulis sebagai JSON di dalam elemen `.swiper-config`; `main.js` membaca dan mem-parse elemen tersebut.
- Animasi masuk memakai atribut `data-aos`, misalnya `data-aos="fade-up"` dan `data-aos-delay="200"`.

## Deployment

Karena situs statis, seluruh isi repositori dapat diunggah apa adanya ke hosting statis seperti GitHub Pages, Netlify, Vercel, Cloudflare Pages, atau web server Nginx/Apache.

Langkah umum:

1. Tidak ada perintah build; root publikasi adalah root repositori.
2. Pertahankan struktur folder `assets/`, `forms/`, dan seluruh berkas HTML.
3. Pastikan file `index.html` berada di root sehingga menjadi halaman default.
4. Semua path aset relatif, sehingga situs dapat di-host di domain utama maupun subdirektori.
5. Jika form kontak ingin diaktifkan, host harus mendukung PHP dan library pro harus tersedia. Hosting statis murni tidak dapat menjalankan `forms/contact.php`.

Repositori ini belum menyertakan konfigurasi deployment, workflow CI, atau berkas `CNAME`.

## Batasan dan Known Issues

- **Form kontak tidak aktif.** `forms/contact.php` akan berhenti dengan pesan `Unable to load the "PHP Email Form" Library!` karena `assets/vendor/php-email-form/php-email-form.php` tidak ada.
- **Banyak tautan masih placeholder.** Tautan "Selengkapnya" pada kartu sistem, sebagian besar tautan footer, dan tautan di `service-details.html` masih memakai `#`.
- **Tombol hero mengarah ke section yang tidak ada.** Tombol "Lihat Lebih Lanjut" menuju `#features-cards`, sementara section Features dikomentari di `index.html`.
- **`id="faq"` duplikat.** Atribut yang sama dipakai pada `<section>` dan `<h2>` di dalamnya. Navigasi masih berfungsi, tetapi markup tidak valid dan berpotensi membingungkan selector.
- **Halaman template tidak terhubung.** `service-details.html` dan `starter-page.html` tidak ditautkan dari halaman mana pun.
- **Belum ada pengujian otomatis.** Verifikasi dilakukan manual di browser pada ukuran desktop dan mobile.
- **Belum ada konfigurasi deployment.** Deploy masih dilakukan manual ke hosting statis.

## Alur Kerja Perubahan

Tidak ada aturan branch atau PR khusus yang tercatat di repositori; riwayat pengembangan saat ini berada di branch `main`.

Alur yang disarankan:

1. Edit HTML/CSS/JS secara langsung.
2. Jalankan server statis dari root repositori.
3. Periksa halaman di desktop dan mobile, termasuk Console browser untuk error JavaScript.
4. Uji navigasi anchor, accordion FAQ, animasi, tautan login, dan tampilan form.
5. Commit dengan pesan yang menjelaskan perubahan, lalu push ke remote.

Contoh commit yang sudah dipakai di repositori ini: `docs: rewrite README based on code review`.

## Lisensi dan Atribusi

- Template: **iLanding** oleh [BootstrapMade](https://bootstrapmade.com/), halaman produk <https://bootstrapmade.com/ilanding-bootstrap-landing-page-template/>.
- Lisensi template: <https://bootstrapmade.com/license/>.
- Sumber SCSS dan library PHP Email Form merupakan aset versi pro dan tidak disertakan dalam repositori ini.
- Repositori ini tidak memiliki berkas `LICENSE` tersendiri. Hubungi pemilik repositori untuk kebutuhan penggunaan ulang.
- Logo, foto, dan konten laboratorium tetap menjadi milik pihak terkait.

## Proyek Terkait

- `sitaris` — aplikasi Sistem Informasi Inventaris Laboratorium yang terkait dengan ekosistem laboratorium ini.

## Kontak

Laboratorium Program Studi Sistem Informasi
Fakultas Sains dan Teknologi, Universitas Islam Negeri Sultan Syarif Kasim Riau
Jl. HR. Soebrantas Km. 18, No. 155, Tuahmadani, Tampan, Pekanbaru 28129
Email: `sif.labor@uin-suska.ac.id`
