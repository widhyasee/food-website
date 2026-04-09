# Food Website - Local Setup

Project ini adalah website PHP (tanpa framework) dan membutuhkan database MySQL/MariaDB.

## 1) Requirement

- PHP 8.x (sudah terpasang di mesin ini: `PHP 8.4.4`)
- MySQL atau MariaDB server
- Browser

## 2) Konfigurasi Database

File koneksi ada di `components/connect.php`:

- host: `localhost`
- database: `food_db`
- user: `root`
- password: kosong (`''`)

### Opsi A (disarankan): pakai XAMPP + phpMyAdmin

1. Install XAMPP (kalau belum ada), lalu jalankan **Apache** dan **MySQL**.
2. Buka `http://localhost/phpmyadmin`.
3. Import file `food_db.sql`.
4. Selesai, database `food_db` akan otomatis dibuat.

### Opsi B: lewat CLI MySQL

Jalankan:

```bash
mysql -u root -p < food_db.sql
```

Jika root tanpa password:

```bash
mysql -u root < food_db.sql
```

> Catatan: file `food_db.sql` sudah saya update agar otomatis membuat database `food_db` saat import.

## 3) Jalankan Website

Dari folder project ini, jalankan:

```bash
php -S localhost:8000
```

Lalu buka:

- `http://localhost:8000/home.php` (halaman user)
- `http://localhost:8000/admin/admin_login.php` (halaman admin)

## 4) Akun awal

Dari data SQL bawaan:

- username admin: `admin`
- password di database disimpan dalam bentuk hash SHA1

Jika login gagal, buat akun admin baru melalui halaman register admin:

- `http://localhost:8000/admin/register_admin.php`

## 5) Troubleshooting cepat

- Error `could not find driver` -> aktifkan ekstensi PDO MySQL di `php.ini` (`extension=pdo_mysql`).
- Error koneksi DB -> pastikan service MySQL/MariaDB berjalan dan kredensial di `components/connect.php` sesuai.
- `mysql: command not found` -> gunakan phpMyAdmin (XAMPP) atau tambahkan MySQL ke PATH sistem.