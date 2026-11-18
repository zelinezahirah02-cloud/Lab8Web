1. Menjalankan Server XAMPP & Mengakses phpMyAdmin
Langkah pertama adalah membuka XAMPP Control Panel dan mengaktifkan modul Apache serta MySQL. Setelah keduanya berjalan, buka browser dan akses http://localhost/phpmyadmin/ untuk mengelola database.
<img width="496" height="320" alt="Screenshot 2026-11-18 042459" src="https://github.com/user-attachments/assets/57aef6b1-7b51-4e76-bdad-21278edb827d" />
<img width="766" height="335" alt="Screenshot 2026-11-18 025255" src="https://github.com/user-attachments/assets/65ea51a0-c211-4463-84cd-3fff10d73f2b" />
2. Membuat Database dan Tabel
Pada halaman phpMyAdmin, dibuat database baru dengan nama latihan1, kemudian dibuat tabel data_barang beserta data awal menggunakan perintah SQL berikut:

CREATE DATABASE latihan1;

USE latihan1;

CREATE TABLE data_barang (
    id_barang int(10) auto_increment Primary Key,
    kategori varchar(30),
    nama varchar(30),
    gambar varchar(100),
    harga_beli decimal(10,0),
    harga_jual decimal(10,0),
    stok int(4)
);

INSERT INTO data_barang (kategori, nama, gambar, harga_beli, harga_jual, stok)
VALUES 
('Elektronik', 'HP Samsung Android', 'gambar/hp_samsung.jpg', 2000000, 2400000, 5),
('Elektronik', 'HP Xiaomi Android', 'gambar/hp_xiaomi.jpg', 1000000, 1400000, 5),
('Elektronik', 'HP OPPO Android', 'gambar/hp_oppo.jpg', 1800000, 2300000, 5);
<img width="956" height="470" alt="image" src="https://github.com/user-attachments/assets/f04724d3-b7bf-45fd-9981-24cb28a22807" />
3. Membuat Folder Proyek & Koneksi Database (koneksi.php)
Membuat folder proyek baru bernama lab8_php_database di dalam direktori htdocs XAMPP, serta folder gambar di dalamnya untuk menampung file gambar yang diunggah. Selanjutnya membuat file koneksi.php untuk menghubungkan PHP ke database latihan1.

<?php
$host = "localhost";
$user = "root";
$pass = "";
$db   = "latihan1";

$conn = mysqli_connect($host, $user, $pass, $db);
if ($conn == false) {
    echo "Koneksi ke server gagal.";
    die();
} #else echo "Koneksi berhasil";
?>
<img width="959" height="472" alt="Screenshot 2026-11-18 032110" src="https://github.com/user-attachments/assets/3a2b4a48-573b-41bb-844c-5070c4aba4d5" />
<img width="959" height="475" alt="Screenshot 2026-11-18 032128" src="https://github.com/user-attachments/assets/6d297497-a2da-4f5d-be44-ef82575e6790" />
4. Menampilkan Data / Read (index.php)
Membuat file index.php dan style.css untuk mengambil seluruh data dari tabel data_barang menggunakan query SELECT * FROM data_barang dan menampilkannya dalam bentuk tabel HTML.
<img width="959" height="472" alt="Screenshot 2026-11-18 034705" src="https://github.com/user-attachments/assets/7c83cf85-0dfa-48ee-b831-1a5c80dc757a" />
5. Menambah Data / Create (tambah.php)
Membuat file tambah.php yang berisi formulir input data barang baru beserta fitur upload gambar. Data yang dikirimkan akan disimpan ke database menggunakan query INSERT INTO.
<img width="959" height="475" alt="Screenshot 2026-11-18 041937" src="https://github.com/user-attachments/assets/0bf02f7a-6b89-4289-b5a1-2b5ea0fd3fd6" />
6. Mengubah Data / Update (ubah.php)
Membuat file ubah.php untuk mengedit data barang yang sudah ada berdasarkan id_barang yang dipilih. Data lama akan otomatis muncul di dalam formulir, dan perubahan akan diperbarui ke database menggunakan query UPDATE.
<img width="959" height="476" alt="Screenshot 2026-11-18 042156" src="https://github.com/user-attachments/assets/fd05cc1c-5b5a-4419-89cd-3b11e288d40c" />
7. Menghapus Data / Delete (hapus.php)
Membuat file hapus.php untuk menghapus baris data tertentu dari tabel data_barang berdasarkan id_barang menggunakan query DELETE FROM, kemudian mengarahkan halaman kembali ke index.php.
