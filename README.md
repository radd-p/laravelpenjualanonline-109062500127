# Laravel Online Sales

Aplikasi praktikum penjualan online (Admin dan Pelanggan) berbasis Laravel 13.

## Kebutuhan
- PHP 8.3 atau lebih baru, Composer, MySQL/MariaDB, Git

## Instalasi
git clone (url-repository) laravel-online-sales
cd laravel-online-sales
composer install
copy .env.example .env        (di Linux/macOS: cp .env.example .env)
php artisan key:generate
(buat database laravel_online_sales lalu atur DB_* pada .env)
php artisan migrate --seed
php artisan storage:link
php artisan serve

Pastikan file public/css/store.css tersedia.

## Akun latihan
- Admin: admin@example.com / Admin12345!
- Pelanggan: daftar melalui /register

## Pengujian
1. 
Customer registrasi
Akun tersimpan role=customer dan langsung login.

2.
Customer membuka /admin
HTTP 403.

3.
Admin login
Masuk dashboard admin.

4.
Admin tambah kategori dan produk
Produk tampil pada admin dan katalog jika aktif.

5.
Admin upload gambar
Gambar tersimpan pada public storage dan tampil pada katalog.

6.
Admin stock-in 10 unit
Saldo stock +10 dan movement IN tercatat.

7.
Pelanggan filter produk
Hasil sesuai keyword/kategori/harga/stok/sort.

8.
Tambah cart melebihi stok
Validasi menolak.

9.
Checkout 2 unit
Order pending dibuat, stock -2, movement OUT tercatat.

10.
Admin confirm
Status menjadi confirmed, validator dan waktu validasi tersimpan.

11.
Admin cancel pending/confirmed
Status cancelled, stok kembali, movement IN tercatat.

12.
Status order
Hanya urutan confirmed→processed→shipped→completed yang diterima.

13.
Jalankan php artisan migrate:fresh --seed pada database yang sudah ada
Semua migration berjalan berurutan tanpa error. Admin, kategori, 3 ekspedisi, dan 15 produk contoh terbentuk.

14.
Tamu membuka /keranjang, /checkout, dan /pesanan
Dialihkan ke halaman login.

15.
Admin membuka /keranjang atau /checkout
HTTP 403.

16.
Pelanggan membuka detail pesanan milik pelanggan lain
HTTP 403.

17.
Dua pelanggan memperebutkan sisa stok yang sama saat checkout
Checkout kedua ditolak dengan pesan stok berubah. Tidak ada order atau movement baru, dan stok tidak negatif.

18.
Admin mengubah harga produk setelah ada order
Detail order lama tetap menampilkan harga saat checkout (snapshot).

