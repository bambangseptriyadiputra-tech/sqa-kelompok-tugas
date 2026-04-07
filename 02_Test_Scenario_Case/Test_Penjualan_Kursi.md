# Test Scenario & Test Case
## Aplikasi Penjualan Kursi Online "KursiKita"

---

## Modul 1: Registrasi & Login

### TS-REG-01: Registrasi Pelanggan Baru

#### TC-REG-01-01: Registrasi dengan data valid
**Precondition:** Pelanggan belum punya akun

| Langkah | Data | Expected Result |
|---------|------|-----------------|
| 1. Buka halaman registrasi | - | Form registrasi tampil |
| 2. Input nama | "Budi Santoso" | Data masuk |
| 3. Input email | "budi@email.com" | Data masuk |
| 4. Input alamat | "Jl. Mawar No.5 Jakarta" | Data masuk |
| 5. Input no HP | "08123456789" | Data masuk |
| 6. Input password | "budi12345" | Data masuk (tersembunyi) |
| 7. Klik "Daftar" | - | Muncul notifikasi "Cek email untuk verifikasi" |
| 8. Input kode verifikasi | Kode dari email | Verifikasi berhasil |
| 9. Redirect ke login | - | Halaman login tampil |

**Status:** [ ] Pass [ ] Fail

#### TC-REG-01-02: Registrasi dengan email sudah terdaftar
| Langkah | Data | Expected Result |
|---------|------|-----------------|
| Input email yang sudah ada | "budi@email.com" | Muncul pesan "Email sudah terdaftar" |
| Klik "Daftar" | - | Registrasi gagal |

**Status:** [ ] Pass [ ] Fail

---

### TS-LOGIN-01: Login Pelanggan

#### TC-LOGIN-01-01: Login dengan data valid
**Precondition:** Pelanggan sudah terdaftar

| Langkah | Data | Expected Result |
|---------|------|-----------------|
| Buka halaman login | - | Form login tampil |
| Input email | "budi@email.com" | Data masuk |
| Input password | "budi12345" | Data masuk |
| Klik "Login" | - | Redirect ke halaman utama |

**Status:** [ ] Pass [ ] Fail

#### TC-LOGIN-01-02: Login dengan password salah
| Langkah | Expected Result |
|---------|-----------------|
| Input email benar, password salah | Muncul pesan "Password salah" |
| Klik Login | Tetap di halaman login |

**Status:** [ ] Pass [ ] Fail

---

## Modul 2: Lihat Daftar Kursi

### TS-PRODUK-01: Melihat dan Mencari Kursi

#### TC-PRODUK-01-01: Menampilkan semua kursi
| Langkah | Expected Result |
|---------|-----------------|
| Buka halaman utama | Tampil daftar kursi (minimal 5 kursi) |
| Setiap kursi tampil gambar, nama, harga, stok | Semua info lengkap |

**Status:** [ ] Pass [ ] Fail

#### TC-PRODUK-01-02: Mencari kursi berdasarkan nama
| Langkah | Data | Expected Result |
|---------|------|-----------------|
| Klik kolom pencarian | - | Kursor aktif |
| Ketik "kursi kantor" | "kursi kantor" | Muncul daftar kursi kantor saja |
| Ketik kursi yang tidak ada | "kursi terbang" | Muncul pesan "Tidak ada kursi ditemukan" |

**Status:** [ ] Pass [ ] Fail

#### TC-PRODUK-01-03: Filter berdasarkan kategori
| Langkah | Data | Expected Result |
|---------|------|-----------------|
| Klik filter "Kantor" | - | Hanya tampil kursi kantor |
| Klik filter "Rumah" | - | Hanya tampil kursi rumah |
| Klik filter "Taman" | - | Hanya tampil kursi taman |

**Status:** [ ] Pass [ ] Fail

---

## Modul 3: Keranjang dan Checkout

### TS-CART-01: Menambah ke Keranjang

#### TC-CART-01-01: Tambah kursi ke keranjang
| Langkah | Data | Expected Result |
|---------|------|-----------------|
| Klik tombol "Beli" pada kursi | - | Popup pilih jumlah muncul |
| Input jumlah | 2 | Total harga = 2 x harga |
| Klik "Tambah ke Keranjang" | - | Notifikasi "Berhasil ditambahkan" |

**Status:** [ ] Pass [ ] Fail

#### TC-CART-01-02: Tambah melebihi stok
| Langkah | Data | Expected Result |
|---------|------|-----------------|
| Pilih kursi dengan stok 5 | - | Maksimal jumlah = 5 |
| Input jumlah | 10 | Muncul pesan "Stok tidak mencukupi" |
| Tombol tambah disable | - | Tidak bisa tambah |

**Status:** [ ] Pass [ ] Fail

---

### TS-CHECKOUT-01: Proses Checkout

#### TC-CHECKOUT-01-01: Checkout dengan metode Transfer Bank
**Precondition:** Keranjang sudah berisi kursi

| Langkah | Expected Result |
|---------|-----------------|
| Buka halaman keranjang | Tampil daftar kursi yang dipilih |
| Klik "Checkout" | Tampil ringkasan order |
| Pilih metode "Transfer Bank" | Muncul nomor rekening tujuan |
| Klik "Konfirmasi Pesanan" | Pesanan tersimpan, muncul nomor order |

**Status:** [ ] Pass [ ] Fail

#### TC-CHECKOUT-01-02: Checkout dengan metode COD
| Langkah | Expected Result |
|---------|-----------------|
| Pilih metode "COD (Bayar di Tempat)" | Tidak perlu transfer |
| Klik "Konfirmasi Pesanan" | Pesanan tersimpan dengan status "Menunggu Konfirmasi" |

**Status:** [ ] Pass [ ] Fail

#### TC-CHECKOUT-01-03: Checkout dengan keranjang kosong
| Langkah | Expected Result |
|---------|-----------------|
| Buka halaman keranjang (kosong) | Tampil pesan "Keranjang Anda kosong" |
| Tombol checkout tidak ada/disable | Tidak bisa checkout |

**Status:** [ ] Pass [ ] Fail

---

## Modul 4: Retur

### TS-RETUR-01: Pengajuan Retur

#### TC-RETUR-01-01: Ajukan retur dengan alasan valid
**Precondition:** Pelanggan sudah login dan punya riwayat pembelian

| Langkah | Expected Result |
|---------|-----------------|
| Buka menu "Riwayat Pembelian" | Tampil daftar pesanan |
| Pilih pesanan status "Selesai" | Detail pesanan tampil |
| Klik "Ajukan Retur" | Form retur tampil |
| Pilih alasan "Barang Rusak" | Alasan terekam |
| Upload foto bukti | Foto terupload |
| Klik "Kirim Retur" | Muncul notifikasi "Permintaan retur dikirim" |

**Status:** [ ] Pass [ ] Fail

#### TC-RETUR-01-02: Retur melebihi batas waktu (14 hari)
| Langkah | Expected Result |
|---------|-----------------|
| Pilih pesanan yang sudah >14 hari | Tombol "Ajukan Retur" tidak aktif |
| Hover ke tombol | Muncul tooltip "Melebihi batas retur 14 hari" |

**Status:** [ ] Pass [ ] Fail

---

## Modul 5: Admin

### TS-ADMIN-01: Admin Verifikasi Pembayaran

#### TC-ADMIN-01-01: Verifikasi pembayaran
**Precondition:** Admin sudah login

| Langkah | Expected Result |
|---------|-----------------|
| Buka menu "Pesanan" | Tampil daftar pesanan |
| Filter status "Menunggu Pembayaran" | Hanya pesanan yang belum dibayar |
| Klik "Verifikasi" pada pesanan | Status berubah menjadi "Diproses" |
| Pelanggan mendapat notifikasi | Notifikasi muncul di akun pelanggan |

**Status:** [ ] Pass [ ] Fail

---

### TS-ADMIN-02: Admin Kelola Kursi

#### TC-ADMIN-02-01: Tambah kursi baru
| Langkah | Data | Expected Result |
|---------|------|-----------------|
| Buka menu "Kelola Kursi" | - | Tampil daftar kursi |
| Klik "Tambah Kursi" | - | Form tambah tampil |
| Input nama | "Kursi Gaming" | Data masuk |
| Input harga | "1500000" | Data masuk |
| Input stok | "10" | Data masuk |
| Upload gambar | file.jpg | Gambar terupload |
| Klik "Simpan" | - | Kursi baru muncul di daftar |

**Status:** [ ] Pass [ ] Fail

#### TC-ADMIN-02-02: Edit kursi
| Langkah | Expected Result |
|---------|-----------------|
| Klik tombol "Edit" pada kursi | Form edit tampil dengan data lama |
| Ubah harga dari 1.500.000 jadi 1.200.000 | Data berubah |
| Klik "Simpan" | Harga kursi berubah |

**Status:** [ ] Pass [ ] Fail

#### TC-ADMIN-02-03: Hapus kursi
| Langkah | Expected Result |
|---------|-----------------|
| Klik tombol "Hapus" pada kursi | Muncul konfirmasi "Yakin hapus?" |
| Klik "Ya" | Kursi hilang dari daftar |

**Status:** [ ] Pass [ ] Fail

---

## Modul 6: Laporan

### TS-LAPORAN-01: Lihat Laporan

#### TC-LAPORAN-01-01: Laporan penjualan hari ini
**Precondition:** Admin/Owner login

| Langkah | Expected Result |
|---------|-----------------|
| Buka menu "Laporan" | Grafik penjualan tampil |
| Pilih filter "Hari Ini" | Data penjualan hari ini tampil |
| Total pendapatan tampil | Angka sesuai perhitungan |

**Status:** [ ] Pass [ ] Fail

#### TC-LAPORAN-01-02: Laporan stok kursi
| Langkah | Expected Result |
|---------|-----------------|
| Pilih menu "Laporan Stok" | Tampil daftar kursi dengan stok |
| Kolom stok menunjukkan sisa | Angka stok sesuai database |
| Ada warning jika stok < 5 | Tanda peringatan muncul |

**Status:** [ ] Pass [ ] Fail
