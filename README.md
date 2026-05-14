# Sistem Antrian Cerdas (AntrianPro)

Sistem Antrian Cerdas berbasis web sederhana yang menggunakan HTML, CSS (Glassmorphism UI), dan JavaScript murni. Proyek ini mendemonstrasikan bagaimana kita dapat menggunakan `localStorage` API pada browser untuk melakukan komunikasi dan sinkronisasi data antar halaman secara *real-time* tanpa memerlukan server backend.

## 🌟 Fitur-Fitur Utama

Sistem ini memiliki dua antarmuka yang dirancang untuk kebutuhan yang berbeda: **Display Pengunjung** dan **Dashboard Admin**.

### 1. Halaman Display Pengunjung (`index.html`)
Halaman ini berfungsi sebagai layar informasi yang biasanya diletakkan di ruang tunggu.
- **Live Display Antrian**: Menampilkan nomor antrian yang saat ini sedang dipanggil atau dilayani secara *real-time*.
- **Ambil Nomor Antrian Mandiri (1 Kali per Pengguna)**: Dilengkapi dengan tombol interaktif bagi pengunjung untuk mengambil tiket antrian. Sistem mencegah pengguna untuk mengambil lebih dari satu nomor antrian untuk menghindari penyalahgunaan tiket.
- **Simpan Tiket sebagai Foto**: Pengunjung dapat mengunduh dan menyimpan gambar tiket nomor antrian mereka ke dalam perangkat (laptop/HP) dalam format foto, memudahkan untuk melihat nomor tanpa harus menghafal.
- **Efek Suara Pemanggilan**: Ketika admin memanggil nomor baru atau melakukan panggilan ulang, halaman ini akan otomatis memutar suara bel pemanggilan (audio notification).
- **Animasi & Umpan Balik Visual**: Dilengkapi dengan efek transisi menarik (*pulse*, penyorotan) saat terjadi pergantian nomor antrian.

### 2. Dashboard Kendali Admin (`admin.html`)
Halaman panel kontrol khusus untuk petugas atau admin yang bertugas mengelola antrian.
- **Sistem Login & Keamanan**: Dilengkapi dengan halaman login (Password default: `admin123`) untuk membatasi akses. Terdapat fitur **Lupa Password** yang menggunakan simulasi pengiriman OTP ke nomor HP terdaftar (default: `081234567890`) untuk mereset kata sandi.
- **Pengaturan Akun**: Di dalam dasbor, admin dapat mengakses menu "Info Akun" untuk mengubah nomor HP pemulihan dan mengganti password login.
- **Panggil Berikutnya (Call Next)**: Menambah urutan nomor antrian saat ini ke nomor berikutnya dan secara langsung membunyikan bel di layar pengunjung.
- **Panggil Ulang (Recall)**: Membunyikan bel kembali di halaman pengunjung untuk mengingatkan atau memanggil ulang nomor antrian yang sama.
- **Lewati & Simpan Antrian Tertunda**: Jika pengunjung dengan nomor tersebut tidak hadir, admin dapat menekan tombol "Lewati". Nomor tersebut akan disimpan dalam "Daftar Antrian Dilewati" dan dapat dipanggil kembali kapan saja pengunjung tersebut datang.
- **Ubah/Lompat Nomor (Custom Jump)**: Fitur yang memberikan keleluasaan untuk melompat atau mengubah nomor antrian ke angka tertentu secara manual jika terdapat kondisi khusus.
- **Reset Sistem Antrian**: Opsi untuk mereset seluruh urutan antrian dan riwayat tiket kembali ke awal (0). Sangat berguna saat pergantian shift atau hari kerja baru.
- **Statistik Antrian**: Memantau statistik dasar seperti "Nomor Saat Ini" dan "Total Antrian Hari Ini".

## 🛠️ Teknologi
- **HTML5 & CSS3** untuk layout web.
- **Desain Glassmorphism** untuk tampilan antarmuka yang modern, bersih, dan estetik.
- **Vanilla JavaScript** sebagai logika utama penggerak.
- **Local Storage API (`window.addEventListener('storage')`)** untuk mengirim sinyal/pesan pembaruan antrian secara instan antara jendela Admin dan jendela Display.

---
**&copy; 2026 by kenzo_project**
