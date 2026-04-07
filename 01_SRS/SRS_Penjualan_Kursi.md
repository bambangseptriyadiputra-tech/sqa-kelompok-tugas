# Software Requirements Specification (SRS)
## Aplikasi Penjualan Kursi Online "KursiKita"

**Versi:** 1.0  
**Tanggal:** 10 Maret 2025  
**Penulis:** Tim SQA Kelompok 17

---

## 1. Pendahuluan

### 1.1 Tujuan
Aplikasi ini bertujuan untuk memudahkan pelanggan membeli kursi secara online dan memudahkan admin mengelola penjualan.

### 1.2 Scope (Lingkup Sistem)

| No | Aktor | Hak Akses |
|----|-------|-----------|
| 1 | Pelanggan | Melihat daftar kursi, cari kursi, tambah ke keranjang, checkout, lihat riwayat pembelian, input retur |
| 2 | Admin | Mengelola data kursi (tambah, edit, hapus), verifikasi pembayaran, proses retur, lihat laporan penjualan |
| 3 | Owner | Melihat laporan penjualan, melihat laporan stok, melihat laporan keuangan |

### 1.3 User Characteristics

| User | Deskripsi |
|------|-----------|
| Pelanggan | Pengguna umum yang membeli kursi. Bisa registrasi, login, belanja, dan retur. |
| Admin | Karyawan yang mengelola toko online. Bisa mengelola produk dan pesanan. |
| Owner | Pemilik toko. Hanya melihat laporan, tidak bisa transaksi. |

### 1.4 Definisi

| Istilah | Arti |
|---------|------|
| Kursi | Produk yang dijual (kursi kantor, kursi makan, kursi tamu, sofa) |
| Retur | Pengembalian barang karena rusak/salah kirim |
| Stok | Jumlah kursi yang tersedia |

---

## 2. Functional Requirements

### FR-01: Registrasi dan Login

| No | Deskripsi | User | Sistem |
|----|-----------|------|--------|
| 1 | Pelanggan pilih menu "Daftar" | ✓ | |
| 2 | Sistem tampilkan form registrasi (nama, email, alamat, no HP, password) | | ✓ |
| 3 | Pelanggan input data diri | ✓ | |
| 4 | Sistem kirim verifikasi ke email | | ✓ |
| 5 | Pelanggan input kode verifikasi | ✓ | |
| 6 | Sistem simpan data dan alihkan ke halaman login | | ✓ |

### FR-02: Lihat Daftar Kursi

| No | Deskripsi | User | Sistem |
|----|-----------|------|--------|
| 1 | Pelanggan buka halaman utama | ✓ | |
| 2 | Sistem tampilkan semua kursi (gambar, nama, harga, stok) | | ✓ |
| 3 | Pelanggan bisa cari kursi berdasarkan nama | ✓ | |
| 4 | Sistem tampilkan hasil pencarian | | ✓ |
| 5 | Pelanggan bisa filter berdasarkan kategori (kantor, rumah, taman) | ✓ | |

### FR-03: Tambah ke Keranjang

| No | Deskripsi | User | Sistem |
|----|-----------|------|--------|
| 1 | Pelanggan klik tombol "Beli" pada kursi | ✓ | |
| 2 | Sistem tampilkan popup pilih jumlah | | ✓ |
| 3 | Pelanggan input jumlah (min 1, max stok) | ✓ | |
| 4 | Sistem tambahkan ke keranjang belanja | | ✓ |
| 5 | Sistem hitung total harga sementara | | ✓ |

### FR-04: Checkout dan Pembayaran

| No | Deskripsi | User | Sistem |
|----|-----------|------|--------|
| 1 | Pelanggan buka halaman keranjang | ✓ | |
| 2 | Sistem tampilkan daftar kursi yang dipilih | | ✓ |
| 3 | Pelanggan klik "Checkout" | ✓ | |
| 4 | Sistem tampilkan ringkasan order + total harga | | ✓ |
| 5 | Pelanggan pilih metode pembayaran (Transfer Bank, COD) | ✓ | |
| 6 | Pelanggan klik "Konfirmasi Pesanan" | ✓ | |
| 7 | Sistem simpan pesanan dengan status "Menunggu Pembayaran" | | ✓ |

### FR-05: Admin Verifikasi Pembayaran

| No | Deskripsi | User | Sistem |
|----|-----------|------|--------|
| 1 | Admin login | ✓ | |
| 2 | Admin buka menu "Pesanan" | ✓ | |
| 3 | Sistem tampilkan daftar pesanan | | ✓ |
| 4 | Admin klik "Verifikasi" pada pesanan yang sudah dibayar | ✓ | |
| 5 | Sistem ubah status menjadi "Diproses" | | ✓ |

### FR-06: Input Retur

| No | Deskripsi | User | Sistem |
|----|-----------|------|--------|
| 1 | Pelanggan buka menu "Riwayat Pembelian" | ✓ | |
| 2 | Pelanggan pilih pesanan yang sudah diterima | ✓ | |
| 3 | Pelanggan klik "Ajukan Retur" | ✓ | |
| 4 | Sistem tampilkan form alasan retur (rusak/salah ukuran/salah jenis) | | ✓ |
| 5 | Pelanggan pilih alasan dan upload foto bukti | ✓ | |
| 6 | Sistem simpan permintaan retur dengan status "Menunggu Konfirmasi Admin" | | ✓ |

### FR-07: Lihat Laporan

| No | Deskripsi | User | Sistem |
|----|-----------|------|--------|
| 1 | Admin/Owner buka menu "Laporan" | ✓ | |
| 2 | Sistem tampilkan filter (periode: hari/bulan/tahun) | | ✓ |
| 3 | User pilih filter | ✓ | |
| 4 | Sistem tampilkan grafik penjualan dan total pendapatan | | ✓ |

---

## 3. Non-Functional Requirements

| Jenis | Deskripsi |
|-------|-----------|
| Performance | Waktu muat halaman < 3 detik |
| Security | Password dienkripsi (bcrypt) |
| Availability | Website online 24 jam (99.9% uptime) |
| Usability | Bisa diakses via Chrome, Firefox, Edge, dan HP |
| Capacity | Bisa menampung 1000 user bersamaan |

---

## 4. Verification Plan

| Requirement | Metode Pengujian | Tools |
|-------------|------------------|-------|
| FR-01 | Manual & Otomatis | Postman, Selenium |
| FR-02 | Manual | Browser testing |
| FR-03 | Manual | Browser testing |
| FR-04 | Manual & Otomatis | Postman |
| FR-05 | Manual | Browser testing |
| FR-06 | Manual | Browser testing |
| FR-07 | Manual | Browser testing |

---

## 5. Referensi
- ISO/IEC/IEEE 29148:2018
