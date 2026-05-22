# 🚀 AntrianPro — Sistem Antrian Cerdas & Modern

AntrianPro adalah sistem manajemen antrian cerdas berbasis web yang dirancang dengan antarmuka modern **Glassmorphism UI** dan didukung oleh **Firebase Realtime Database**. Sistem ini memfasilitasi komunikasi dan sinkronisasi data secara *real-time* antar halaman (Display Pengunjung, Dashboard Admin, dan Grafik Analisis) tanpa memerlukan server backend kustom.

---

## 🌟 Fitur-Fitur Utama

Sistem ini terbagi menjadi tiga halaman utama dengan fungsi dan peran yang spesifik:

### 1. Halaman Display Pengunjung (`index.html`)
Halaman interaktif yang dipajang di ruang tunggu atau digunakan oleh pengunjung:
- **Live Display Antrian:** Menampilkan nomor antrian yang sedang dilayani secara *real-time* dengan efek transisi pembaruan yang halus.
- **Tujuan Loket Otomatis:** Menunjukkan loket/meja pelayanan tujuan secara dinamis (misalnya: *Meja Registrasi*, *Meja Perekaman Biometrik*).
- **Formulir Registrasi Mandiri:** Pengunjung dapat mendaftar mandiri dengan mengisi data lengkap (Nama Lengkap, Nomor KTP 16-digit, Nomor HP, Alamat).
- **Unduh Tiket Digital (Foto):** Menggunakan pustaka `html2canvas` untuk menghasilkan gambar tiket fisik berdesain elegan langsung ke penyimpanan perangkat pengunjung.
- **Sistem Pembatasan Tiket:** Menggunakan `localStorage` untuk membatasi pengunjung agar hanya dapat mengambil satu tiket antrian aktif (mencegah duplikasi).
- **Notifikasi Suara Bel Pemanggilan:** Halaman memutarkan efek suara bel panggilan secara otomatis ketika admin memanggil nomor antrian.

### 2. Dashboard Kendali Admin (`admin.html`)
Panel kendali komprehensif bagi petugas untuk mengelola alur antrian:
- **Autentikasi & Keamanan:** Akses masuk dilindungi oleh kata sandi (Default: `admin123`). Status login disimpan pada `sessionStorage` untuk keamanan sesi.
- **Pemulihan Kata Sandi dengan OTP:** Simulasi pengiriman kode OTP melalui alert ke nomor HP pemulihan yang terdaftar (Default: `081234567890`).
- **Pengaturan Profil Admin:** Pilihan untuk mengubah nomor HP pemulihan dan memperbarui kata sandi secara langsung dari dalam panel kontrol.
- **Kontrol Antrian Utama:**
  - **Panggil Berikutnya (Call Next):** Memanggil nomor antrian selanjutnya dan memicu notifikasi suara di layar pengunjung.
  - **Panggil Ulang (Recall):** Memanggil ulang nomor antrian aktif.
  - **Lewati (Skip):** Menangguhkan nomor antrian saat ini dan menyimpannya ke daftar antrian dilewati.
  - **Lompat Nomor (Custom Jump):** Berfungsi untuk mengatur nomor antrian ke angka spesifik secara manual.
  - **Reset Antrian:** Menghapus seluruh data antrian hari ini dan mengembalikan urutan ke awal (0).
- **Informasi Detail Pengunjung:** Menampilkan rincian data diri pengunjung yang sedang dipanggil secara mendetail.
- **Daftar Antrian Hari Ini:** Tabel interaktif yang menampilkan seluruh pendaftar antrian beserta status terkini mereka (`Waiting`, `Calling`, `Skipped`, `Served`).

### 3. Grafik Analisis Pengunjung (`grafik.html`)
Modul analisis data untuk meninjau efisiensi operasional layanan:
- **Security Gate:** Mencegah akses tidak sah. Pengguna yang belum login sebagai admin akan dialihkan kembali ke halaman login.
- **Ringkasan Statistik Utama:** Menampilkan metrik penting seperti *Total Pengunjung*, *Pengunjung Hari Ini*, dan *Rata-rata Kunjungan Harian*.
- **Grafik Tren Kunjungan:** Visualisasi tren kunjungan harian interaktif berupa grafik area yang menawan menggunakan **Chart.js**.
- **Tabel Rincian Harian:** Rincian tabel kronologis yang menyajikan jumlah pengunjung per hari untuk analisis data tingkat lanjut.

---

## 🛠️ Arsitektur & Teknologi

- **Frontend Core:** HTML5, CSS3 murni (Vanilla CSS), dan Vanilla JavaScript (ES6 Modules).
- **Tema Desain:** Modern Glassmorphism UI dengan efek cahaya latar belakang (*background glow*), pembatas semi-transparan, filter buram (*backdrop-filter*), serta tipografi menggunakan font *Outfit* dan *Inter*.
- **Pustaka Pihak Ketiga (CDN):**
  - **Chart.js** (Visualisasi data analitik)
  - **html2canvas** (Konversi kartu tiket HTML menjadi file gambar PNG)
  - **Font Awesome 6.4.0** (Ikonografi antarmuka)
- **Database & Sinkronisasi:** **Firebase Realtime Database** untuk sinkronisasi data instan berbasis soket antar jendela browser dan perangkat.

---

## ⚙️ Petunjuk Setup & Konfigurasi

Agar aplikasi dapat berjalan dengan normal dan terhubung ke server database Anda, ikuti langkah-langkah konfigurasi Firebase berikut:

1. Buat proyek baru di [Firebase Console](https://console.firebase.google.com/).
2. Aktifkan **Realtime Database** pada proyek Anda.
3. Buka pengaturan proyek (Project Settings) dan salin konfigurasi Web App SDK Anda.
4. Perbarui variabel `firebaseConfig` pada bagian skrip modul di file-file berikut:
   - [`index.html`](file:///e:/gabutnyasaya.html/NOMOR%20ANTRIAN/index.html)
   - [`admin.html`](file:///e:/gabutnyasaya.html/NOMOR%20ANTRIAN/admin.html)
   - [`grafik.html`](file:///e:/gabutnyasaya.html/NOMOR%20ANTRIAN/grafik.html)

Struktur konfigurasi yang perlu disesuaikan:
```javascript
const firebaseConfig = {
    apiKey: "YOUR_API_KEY",
    authDomain: "YOUR_PROJECT_ID.firebaseapp.com",
    databaseURL: "https://YOUR_PROJECT_ID-default-rtdb.firebasedatabase.app",
    projectId: "YOUR_PROJECT_ID",
    storageBucket: "YOUR_PROJECT_ID.firebasestorage.app",
    messagingSenderId: "YOUR_SENDER_ID",
    appId: "YOUR_APP_ID",
    measurementId: "YOUR_MEASUREMENT_ID"
};
```

---

## 📂 Struktur Proyek

```text
NOMOR ANTRIAN/
│
├── index.html       # Tampilan antrian pengunjung & registrasi tiket
├── admin.html       # Dashboard kontrol admin & data antrian harian
├── grafik.html      # Grafik analitik pengunjung (Chart.js)
├── style.css        # Berkas gaya global & desain Glassmorphism
└── README.md        # Panduan dan dokumentasi proyek (Berkas ini)
```

---

<div align="center">
    <a href="https://kenzodchjandcuh.github.io/Web-Nomor-Antrian-By-Kenzo_Project/">Nomor Antrian </a> © 2026 by <a href="https://kenzodchjandcuh.github.io/cv/">Kenzo_Project</a> is licensed under <a href="https://creativecommons.org/licenses/by-nc-nd/4.0/">Creative Commons Attribution-NonCommercial-NoDerivatives 4.0 International</a><img src="https://mirrors.creativecommons.org/presskit/icons/cc.svg" alt="" style="max-width: 1em;max-height:1em;margin-left: .2em;"><img src="https://mirrors.creativecommons.org/presskit/icons/by.svg" alt="" style="max-width: 1em;max-height:1em;margin-left: .2em;"><img src="https://mirrors.creativecommons.org/presskit/icons/nc.svg" alt="" style="max-width: 1em;max-height:1em;margin-left: .2em;"><img src="https://mirrors.creativecommons.org/presskit/icons/nd.svg" alt="" style="max-width: 1em;max-height:1em;margin-left: .2em;">
</div>
