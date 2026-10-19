# FREEDOMS — Event Running Partner

Ekspor portabel website FREEDOMS. Desain, tujuh portofolio race, profil tim, filter galeri, dialog detail race, pembesaran foto, navigasi album, dan dialog kontak dipertahankan. Foto dummy diunduh ke aset lokal. Foto tim menggunakan gambar unggahan terakhir.

## Jalankan di komputer

Pilihan 1: Python 3 (tidak perlu instal paket):

```sh
python3 -m http.server 8080 --directory dist
```

Windows dapat menggunakan `py -m http.server 8080 --directory dist`.
Buka http://localhost:8080. Hentikan dengan Ctrl+C.

Pilihan 2: Node.js 18 atau lebih baru:

```sh
npm start
```

Tidak perlu menjalankan npm install. Server bawaan untuk preview lokal, bukan server produksi.

## Deploy

- **cPanel/shared hosting:** unggah seluruh ISI folder `dist/` ke `public_html/` atau folder domain. `index.html` harus berada di akar folder publik. Aset berada di `assets/`.
- **Hosting dalam subfolder:** unggah isi `dist/` ke subfolder. Semua aset memakai path relatif. Tidak diperlukan rewrite SPA.
- **Netlify:** direktori publish `dist`, tanpa build command. `netlify.toml` disertakan.
- **Vercel:** pilih Other, output directory `dist`, tanpa build/install command; `vercel.json` disertakan.
- **Cloudflare Pages:** tanpa build command, output directory `dist`.
- **Nginx:** contoh `nginx.conf.example` disertakan; sesuaikan domain dan root, konfigurasi HTTPS melalui penyedia hosting.

## Struktur

- `dist/index.html`: seluruh HTML, CSS, JavaScript; tidak diminifikasi.
- `dist/assets/`: foto tim dan tujuh gambar ilustrasi race; disajikan lokal.
- `package.json` dan `server.mjs`: preview Node tanpa dependensi pihak ketiga.
- `DEPENDENCIES.md`: dependensi dan kompatibilitas.
- `ASSETS.md`: asal dan pemetaan gambar.
- `netlify.toml`, `vercel.json`, `nginx.conf.example`: konfigurasi deployment.
- `reference/chatgpt-sites-hosting.json`: konfigurasi asli Sites untuk referensi; tidak diperlukan hosting lain.

## Mengubah konten

1. Foto tim: ganti `dist/assets/freedoms-team.png` atau ubah src gambar dalam section `id="team"`.
2. Race: ubah array `names` di bagian script `dist/index.html`. Array `images` mengatur foto per race; fungsi `url()` memetakan ke aset lokal.
3. Hero: ubah gambar pada `.hero`, saat ini `assets/race-1.jpg`.
4. Profil tim: edit section `id="team"`.
5. Kontak: tombol `contactBtn` saat ini membuka informasi bahwa kontak belum tersedia. Setelah nomor resmi ada, ganti tombol dengan tautan WhatsApp yang benar, misalnya `https://wa.me/62NOMOR`, atau sesuaikan handler JavaScript.
6. Foto galeri: saat ini memakai array gambar dummy. Filter per race memilih tiga foto ilustrasi; ganti pemetaan `visible` pada fungsi `select()` untuk album asli tiap event.
7. Tanggal, lokasi, lingkup pekerjaan: lengkapi template dialog handler `[data-race]`.

## Ketergantungan pada ChatGPT Sites

Tidak ada SDK Sites, API ChatGPT, database, login aplikasi, token, atau backend yang digunakan dalam kode website. Semua interaksi berjalan di browser. Autentikasi pemilik pada URL Sites merupakan akses hosting, bukan fitur di kode ini. **Di hosting lain akses tidak otomatis privat**: atur proteksi melalui hosting bila diperlukan. File referensi hosting Sites tidak diterapkan di penyedia lain.

Foto eksternal yang sebelumnya berasal dari Unsplash sudah disertakan lokal. Website tidak memerlukan koneksi Unsplash saat dijalankan. Tidak ada font, library, CDN, atau analytics eksternal.

## Batasan versi saat ini

- Tidak ada dashboard admin/CMS, upload foto, formulir terkirim, pembayaran, registrasi peserta, atau database dalam versi ini.
- Kontak belum diisi dan detail race masih perlu dilengkapi, sesuai versi website sumber.
- Galeri tanpa tombol unduh. Browser tetap bisa menyimpan gambar atau mengambil tangkapan layar.
- Ilustrasi dummy dan labelnya dipertahankan; tidak mengklaim sebagai dokumentasi race asli.
- Penggunaan gambar tetap mengikuti hak/lisensi masing-masing sumber. Ganti foto dummy dengan dokumentasi yang Anda miliki sebelum peluncuran final.

## Verifikasi ekspor

Sintaks JavaScript, integritas ZIP, decoding semua gambar, referensi aset lokal, dan respons server lokal diperiksa. Verifikasi visual dan klik melalui browser belum dilakukan.
