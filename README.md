# Knowledge
# Manajemen Barang Masuk & Keluar

## 1. Manajemen Barang Masuk & Keluar

### Input Data Barang Masuk
1. Admin gudang memasukkan data barang yang baru datang ke formulir input barang masuk.
2. Sistem memverifikasi data yang dimasukkan.
3. Data barang masuk disimpan ke dalam tabel Transaksi dengan jenis transaksi "Masuk".
4. Kuantitas barang pada tabel Barang diperbarui.

### Monitoring Barang Masuk
1. Admin dapat melihat laporan barang masuk pada dashboard sistem.
2. Laporan menampilkan detail data barang yang masuk, termasuk tanggal, kuantitas, dll.

### Laporan dan Monitoring Stok
#### a) Laporan Stok Barang
1. Sistem menghasilkan laporan stok barang secara real-time.
2. Admin dapat memonitor jumlah stok yang tersedia di gudang.

#### b) Laporan Riwayat Transaksi
1. Sistem menyimpan riwayat transaksi barang masuk dan keluar.
2. Admin dapat melihat riwayat transaksi untuk melacak pergerakan barang.

## 2. Penjelasan REST API dan Job Queue

### a. REST API
Menurut saya, REST API (Representational State Transfer Application Programming Interface) adalah arsitektur yang berfungsi untuk membangun layanan web yang dapat berinteraksi dengan sistem lain melalui protokol HTTP (Hypertext Transfer Protocol). REST juga menggunakan aturan yang konsisten untuk membuat, membaca, memperbarui, dan menghapus sumber daya.

Metode HTTP: `GET`, `POST`, `PUT`, `DELETE`, `HEAD`, `OPTIONS`, `PATCH`.

### b. Job Queue dalam Laravel
Menurut saya, Job queue dalam Laravel adalah sebuah antrian tempat menunggu pekerjaan untuk dieksekusi. Job adalah tugas atau pekerjaan tertentu yang perlu dijalankan, seperti mengirim email, memproses gambar, atau mengupdate database. Tujuan dari penggunaan Job queue ini adalah untuk meningkatkan performa sistem dan mengurangi waktu respon.

## 3. Source Code

```php
<?php
$merchant = [
    [
        'id' => 1,
        'name' => 'RM Madang Geden'
    ],
    [
        'id' => 2,
        'name' => 'RM Pokwe'
    ]
];

$product = [
    [
        'category' => 'food',
        'created_at' => '2023-10-30 13:39:49',
        'name' => 'Baso Aci',
        'merchant_id' => 1
    ],
    [
        'category' => 'drink',
        'created_at' => '2023-10-12 13:30:49',
        'name' => 'Es Jeruk',
        'merchant_id' => 2
    ],
    [
        'category' => 'desert',
        'created_at' => '2023-11-30 13:39:49',
        'name' => 'ice cream',
        'merchant_id' => 1
    ],
    [
        'category' => 'food',
        'created_at' => '2023-10-11 13:39:49',
        'name' => 'Mie Ayam',
        'merchant_id' => 1
    ],
    [
        'category' => 'drink',
        'created_at' => '2023-05-30 13:39:49',
        'name' => 'Teh',
        'merchant_id' => 2
    ],
    [
        'category' => 'food',
        'created_at' => '2023-01-02 13:39:49',
        'name' => 'Nasi Goreng',
        'merchant_id' => 2
    ],
];

function sortProductsByDateDesc($products) {
    usort($products, function($a, $b) {
        return strtotime($b['created_at']) - strtotime($a['created_at']);
    });
    return $products;
}

$sortedProducts = sortProductsByDateDesc($product);

// Output hasil sorting
echo "<pre>";
print_r($sortedProducts);
echo "</pre>";
?>

Penjelasan : 
1. Fungsi sortProductsByDateDesc: Fungsi ini menerima array $products dan menggunakan usort untuk mengurutkannya berdasarkan created_at dari yang terbaru ke yang terlama.
2. usort: Fungsi ini mengurutkan array menggunakan callback yang membandingkan timestamp dari created_at.
3. strtotime: Fungsi ini mengkonversi string tanggal menjadi timestamp sehingga mudah untuk dibandingkan.
4. Penggunaan Fungsi: Array $product diurutkan dengan memanggil sortProductsByDateDesc dan hasilnya disimpan di $sortedProducts.
5. Output Hasil: Menggunakan print_r untuk menampilkan hasil sorting dalam format yang mudah dibaca.
