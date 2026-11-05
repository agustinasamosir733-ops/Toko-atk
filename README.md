# TOKO ATK — Inventory Management System

Project Mini Project 3 berdasarkan PPT Pertemuan 4: Relational Database + Advanced PHP.

## Teknologi
- PHP Native (disarankan PHP 8.0+)
- MySQL/MariaDB
- PDO + Prepared Statement
- Bootstrap 5

## Cara menjalankan di XAMPP
1. Ekstrak folder `toko_atk_inventory` ke `C:\xampp\htdocs\`.
2. Jalankan Apache dan MySQL dari XAMPP Control Panel.
3. Buka `http://localhost/phpmyadmin`.
4. Pilih menu **Import**, lalu impor file `database/schema.sql`.
   - File SQL akan membuat database `toko_atk_inventory` sekaligus tabel dan data contoh.
5. Pastikan pengaturan database pada `config/database.php` sesuai XAMPP Anda (default user `root`, password kosong).
6. Buka `http://localhost/toko_atk_inventory/public/`.
7. Login awal:
   - Username: `admin`
   - Password: `password`

## Struktur folder
- `config/database.php`: koneksi PDO.
- `helpers/`: autentikasi, validasi, escaping, CSRF.
- `public/`: halaman aplikasi.
- `views/`: layout header/footer.
- `database/schema.sql`: database, relasi, foreign key, dan data awal.

## Role dan hak akses
- **Admin**: akses dashboard, kategori, produk, supplier, transaksi, laporan, dan manajemen pengguna.
- **Staff**: akses dashboard, produk, transaksi stok, dan laporan. Tidak dapat membuka halaman administrasi kategori/supplier/pengguna.

## Fitur yang diterapkan
- Login/logout, session regeneration, password hashing dan verifikasi.
- Relasi one-to-one (`users` ke `user_profiles`), one-to-many (`categories` ke `products`), many-to-many (`products` ke `suppliers` melalui `product_suppliers`).
- Foreign key dan aturan referential integrity.
- JOIN, WHERE, LIKE, ORDER BY, GROUP BY, COUNT, SUM, AVG.
- Search nama/SKU, filter kategori, sorting allowlist, pagination 10 data.
- Barang masuk/keluar dengan PDO transaction, `SELECT ... FOR UPDATE`, COMMIT/ROLLBACK.
- Validasi server-side, prepared statement, output escaping, dan token CSRF.
- Dashboard total produk, total stok, nilai inventory, stok rendah, barang masuk/keluar.
- Histori transaksi disimpan dan produk yang sudah memiliki histori tidak dapat dihapus.

## Business rules
- SKU unik.
- Harga tidak boleh negatif.
- Quantity transaksi harus lebih dari nol.
- Barang keluar tidak boleh melebihi stok.
- Stok tidak boleh negatif.
- Produk dengan histori transaksi tidak boleh dihapus.
- Halaman internal membutuhkan login.
- Staff tidak boleh mengakses administrasi user.
- Sorting hanya memakai kolom yang diizinkan.

## Catatan
- Bootstrap dimuat dari CDN, jadi koneksi internet diperlukan untuk tampilan Bootstrap.
- Tabel `user_profiles` disiapkan untuk menunjukkan relasi one-to-one sesuai materi; form profil dapat dikembangkan terpisah.
- Gunakan akun admin awal hanya untuk instalasi lokal/tugas. Ganti password sebelum aplikasi dipakai sungguhan.
