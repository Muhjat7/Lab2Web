# lab2web
Idris Syahrudin 312210467 TI.22.A5

## Belajar PHP Dasar
![Code_EcuixSMOoV](https://github.com/steprtm/lab2web/assets/129705802/a5dded82-7a92-49bc-9d3e-fb7a32bd45b3)


Hasil:


![firefox_NLBlF7Z6rR](https://github.com/steprtm/lab2web/assets/129705802/bc3adfcf-c6b5-44bd-85bc-a0cf7da6cf47)

## Menggunakan Variable
![Screenshot (217)](https://github.com/IdrisSyahrudin/Lab2Web/assets/129921422/99d2c3d8-9ae1-4377-b5ff-20a607cf940b)

Hasil:

![Screenshot (215)](https://github.com/IdrisSyahrudin/Lab2We/assets/129921422/fa43b29b-23e8-4079-8bae-ef23191bd847)

## Form Input
![Code_8pCIUg5wi3](https://github.com/steprtm/lab2web/assets/129705802/a06d70eb-ac57-499b-aa90-8adaeca21364)

Hasil:

![Screenshot (216)](https://github.com/IdrisSyahrudin/Lab2We/assets/129921422/7940f7a4-5e9d-460b-9687-7850f7e353dd)


## Tugas
![Code_k4QL8UveeF](https://github.com/steprtm/lab2web/assets/129705802/35797c5a-5da3-4716-b973-01370e6899d4)

Hasil:


![Screenshot (213)](https://github.com/IdrisSyahrudin/Lab2We/assets/129921422/d116d645-397f-4a81-b617-ff439eb5c607)


## Penjelasan
1. Struktur HTML
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>PHP Dasar</title>
</head>
<body>
    <h2>Form Input</h2>
    <form method="post">
        <label>Nama: </label>
        <input type="text" name="nama">
        <label>Tanggal Lahir: </label>
        <input type="date" name="tanggal_lahir">
        <label>Pekerjaan: </label>
        <select name="pekerjaan">
            <option value="Operator">Operator</option>
            <option value="Developer">Developer</option>
            <option value="Manager">Manager</option>
        </select>
        <input type="submit" value="Kirim">
    </form>
```
**Input Nama:** Pengguna memasukkan nama mereka.

**Input Tanggal Lahir:** Pengguna memilih tanggal lahir menggunakan kontrol input tanggal.

**Pilihan Pekerjaan:** Pengguna memilih pekerjaan dari dropdown, yang akan mempengaruhi perhitungan gaji.

2. Logika PHP, Proses Formulir
```
<?php
if ($_SERVER["REQUEST_METHOD"] == "POST" && isset($_POST['nama']) && isset($_POST['tanggal_lahir']) && isset($_POST['pekerjaan'])) {
    $nama = htmlspecialchars($_POST['nama']);
    $tanggal_lahir = $_POST['tanggal_lahir'];
    $pekerjaan = $_POST['pekerjaan'];
```
**Pengecekan Metode dan Data:** Memeriksa apakah formulir telah dikirim menggunakan metode POST dan semua data yang diperlukan ada.

**Sanitisasi Input:** Fungsi htmlspecialchars digunakan untuk menghindari serangan XSS (Cross-Site Scripting) dengan membersihkan input nama dari tag HTML atau karakter khusus.

3. Kalkulasi Umur
```
    $birthdate = new DateTime($tanggal_lahir);
    $today = new DateTime('today');
    $age = $birthdate->diff($today)->y;
```
**Objek DateTime:** Digunakan untuk memanipulasi tanggal dengan mudah.

**Perhitungan Selisih Tahun:** Menghitung selisih tahun antara tanggal lahir dan hari ini untuk mendapatkan umur.

4. Perhitungan Gaji dan Pajak
```
    $salaries = [
        "Operator" => 1000000,
        "Developer" => 3000000,
        "Manager" => 5000000
    ];
    $taxRates = [
        "Operator" => 0.1,
        "Developer" => 0.15,
        "Manager" => 0.2
    ];
    $gaji = isset($salaries[$pekerjaan]) ? $salaries[$pekerjaan] : 0;
    $pajak = isset($taxRates[$pekerjaan]) ? $taxRates[$pekerjaan] : 0;
    $thp = $gaji - ($gaji * $pajak);
```

**Array:** Menyimpan nilai gaji dan pajak berdasarkan jenis pekerjaan.

**Kalkulasi Gaji Bersih:** Menghitung gaji bersih dengan mengurangkan pajak dari gaji kotor.

5. Menampilkan Hasil
```
    echo "Selamat Datang $nama<br>";
    echo "Usia Anda: $age tahun<br>";
    echo "Pekerjaan: $pekerjaan<br>";
    echo "Gaji sebelum pajak = Rp. " . number_format($gaji, 0, ',', '.') . "<br>";
    echo "Gaji yang dibawa pulang = Rp. " . number_format($thp, 0, ',', '.');
}
?>
</body>
</html>
```
**Output:** Menggunakan echo untuk menampilkan teks dan data yang diproses ke pengguna.




