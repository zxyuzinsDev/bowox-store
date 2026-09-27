# BOWOX STORE — Website Pembeli & Admin

Paket ini berisi **2 website** yang saling terhubung:

| File | Fungsi |
|---|---|
| `index.html` | Website untuk **PEMBELI** (buat akun/masuk, pilih paket, order, isi saldo, kirim bukti transfer) |
| `admin.html` | Website untuk **ADMIN** (buat akun/masuk, ACC order, cek bukti transfer, kirim link join / tandai selesai, ACC isi saldo) |
| `assets/qris.jpeg` | Gambar QRIS pembayaran toko Anda — **belum termasuk**, lihat bagian "QR Belum Muncul" di bawah |

---

## ⚠️ QR Belum Muncul / Rusak

Gambar QRIS asli toko Anda belum pernah saya terima, jadi di halaman Pembayaran QR-nya tampil patah (ikon gambar rusak). Ini **bukan bug kode**, filenya memang belum ada.

**Cara paling gampang:** kirim/upload foto QRIS toko Anda (jpg/png) di chat ini, nanti saya tempelkan langsung ke dalam file HTML-nya (jadi tidak perlu folder `assets` terpisah lagi — tinggal 2 file saja yang perlu diupload ke GitHub).

**Kalau mau atur sendiri:** buat folder bernama `assets` persis di sebelah `index.html`, lalu taruh gambar QRIS Anda di dalamnya dengan nama file persis `qris.jpeg`.

---

## Alur Sistem

1. Pembeli buka `index.html` → **Buat Akun** (username, email, password, ulangi password) kalau baru pertama kali, atau **Masuk** kalau sudah punya akun.
2. Pembeli pilih paket → tekan **ORDER**:
   - Untuk layanan *suntik* (Followers/Views/Likes TikTok & Instagram): **wajib** isi link/username akun yang mau di-suntik.
   - Untuk layanan lain (MurSC, Akun Telegram, Jasa Website): kolom target opsional.
   - Order masuk ke admin dengan status *MENUNGGU ACC*.
3. Admin buka `admin.html` → **Masuk** (atau **Buat Akun** jika admin baru) → tekan **ACC** atau **TOLAK**.
4. Setelah di-ACC, pembeli **transfer ke QRIS** lalu tekan **KIRIM BUKTI** (upload screenshot).
5. Admin cek bukti, lalu:
   - Layanan *suntik* → admin proses ke akun target, lalu tekan **TANDAI SELESAI** (tidak perlu link).
   - Layanan lain → admin tekan **KIRIM LINK JOIN**, isi link → langsung muncul di menu *Pesanan Saya* milik pembeli.
6. **Isi Saldo**: pembeli isi nominal → tekan **ISI SALDO SEKARANG** → QR & nominal transfer muncul di layar → transfer → tekan **SAYA SUDAH TRANSFER** → form kirim bukti langsung terbuka → admin tekan **ACC** → saldo pembeli bertambah otomatis.

---

## Login Pembeli & Admin

Baik pembeli maupun admin sekarang pakai **akun sendiri** (username + password), bukan sekadar ketik nama:

- **Buat Akun**: username, email, password, ulangi password. Username tidak boleh dobel, jadi saldo & histori pesanan pasti aman tersimpan di akun masing-masing.
- **Masuk**: username + password.
- **Lupa Password**: masukkan username + email yang didaftarkan → langsung bisa set password baru. Karena situs ini statis (tanpa server), resetnya lewat pencocokan username+email, bukan email sungguhan yang terkirim.
- **Akun admin default**: username `bowox`, password `bowox2024` — langsung bisa dipakai. Akun ini belum punya email; login dulu → tab **AKUN SAYA** → isi email supaya "Lupa Password" bisa dipakai untuk akun ini juga.
- Tombol dengan nama akun di pojok kanan atas (pembeli) berfungsi untuk **keluar/logout** dari akun.

---

## Cara Menjalankan di GitHub Pages (Gratis)

1. Buat akun di [github.com](https://github.com) jika belum punya.
2. Klik tombol **New** (atau **New repository**) → beri nama misalnya `bowox-store` → pilih **Public** → klik **Create repository**.
3. Di halaman repo, klik **uploading an existing file**.
4. Seret/upload `index.html`, `admin.html`, dan `README.md`. Kalau sudah punya gambar QRIS, buat juga folder `assets` berisi `qris.jpeg` lalu upload sekalian.
5. Klik **Commit changes** di bagian bawah.
6. Masuk ke tab **Settings** (di repo yang sama) → menu **Pages** di sidebar kiri.
7. Di bagian **Branch**, pilih **main** dan folder **/ (root)** → klik **Save**.
8. Tunggu 1–2 menit, lalu website Anda aktif di:
   - Pembeli: `https://USERNAME.github.io/bowox-store/`
   - Admin: `https://USERNAME.github.io/bowox-store/admin.html`

   (Ganti `USERNAME` dengan username GitHub Anda, dan `bowox-store` kalau nama repo-nya beda.)

### Kalau mau coba dulu tanpa GitHub
Cukup taruh `index.html`, `admin.html`, dan folder `assets` dalam satu folder yang sama di komputer/HP, lalu buka `index.html` langsung dua kali klik. Semua fitur jalan normal, hanya saja data hanya tersimpan di browser itu saja (lihat catatan di bawah).

---

## Catatan Penting

- Data order, saldo, dan akun tersimpan di **browser (localStorage)**. Website pembeli dan admin **harus diakses dari domain & browser yang sama** agar datanya nyambung (contoh: admin dan pembeli sama-sama lewat link GitHub Pages Anda, dan admin tidak memakai mode incognito).
- File bukti transfer maksimal ±800KB (screenshot biasa sudah cukup).
- Untuk reset semua data (akun, order, saldo): buka browser → tekan F12 → tab Console → ketik `localStorage.clear()` → Enter.
- Ini semua berjalan di sisi browser (client-side), jadi cocok untuk skala kecil-menengah. Kalau nanti ingin data tersimpan online dan sinkron lintas perangkat (HP pembeli ↔ laptop admin secara real-time), perlu backend seperti Firebase — bisa minta dibuatkan versi itu terpisah.

© 2026 BOWOX STORE
