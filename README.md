**⚡ Preprocessing Data Listrik Global (Ember)**
File ini menjelaskan langkah-langkah pembersihan data dari dataset Ember Global Electricity. Tujuannya adalah memastikan data siap pakai, akurat, dan tidak bikin komputer berat saat dijalankan.

📋 Ringkasan Langkah & Alasan
1. Persiapan & Backup
Aksi: Import library dan copy data asli.
Alasan: Menjaga agar data original tidak rusak jika kita melakukan kesalahan saat pembersihan.

2. Merapikan Nama Kolom
Aksi: Mengubah nama kolom menjadi huruf kecil semua dan mengganti spasi dengan garis bawah (contoh: Area Type → area_type).
Alasan: Memudahkan penulisan kode dan mencegah error akibat salah ketik spasi atau huruf kapital.

3. Optimasi Memori (Hemat RAM)
Aksi: Mengubah tipe data teks yang berulang menjadi category dan angka kecil menjadi int8.
Alasan: Menghemat penggunaan memori hingga 70%, sehingga proses analisis jadi jauh lebih cepat.

4. Pengolahan Waktu (Time-Series)
Aksi: Mengubah kolom date ke format tanggal dan memecahnya menjadi tahun, bulan, dan kuartal.
Alasan: Agar kita bisa melihat tren bulanan atau tahunan dengan mudah (misal: "Apakah pemakaian listrik naik setiap musim panas?").

5. Pembersihan Data Kosong & Duplikat
Aksi: Menghapus baris yang tidak ada nilai listriknya dan membuang data ganda.
Alasan: Menghindari hasil analisis yang "ngaco" atau angka yang terlihat lebih besar dari aslinya karena terhitung dua kali.

6. Penandaan Data Sementara (Provisional)
Aksi: Membuat kolom is_provisional untuk menandai data 12 bulan terakhir.
Alasan: Data terbaru biasanya masih bisa berubah (revisi). Penanda ini berfungsi sebagai peringatan agar kita lebih berhati-hati saat menyimpulkan data terbaru.

7. Pemisahan Data (Filter)
Aksi: Memisahkan data negara dengan data wilayah (region) serta memisahkan satuan (TWh, %, emisi).
Alasan: Sangat Penting! Agar tidak terjadi double counting (misal: data Indonesia tidak sengaja dijumlahkan lagi dengan data total ASEAN).

8. Validasi Akhir (Sanity Check)
Aksi: Mengecek apakah jumlah semua bahan bakar (batu bara, surya, dll) sudah sama dengan total pembangkitan.
Alasan: Memastikan preprocessing kita sudah benar secara logika matematika sebelum masuk ke tahap visualisasi atau AI.

------------------------------------------------------------------------------------------------------------------------------------------------------------------------
📈 **Hasil Akhir**
Data Berhasil Dibersihkan: Sekitar 498 ribu baris.

File Output: ember_cleaned.csv (Siap digunakan untuk membuat grafik atau model prediksi).
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------
**Tips Singkat:**
"Gunakan data yang berlabel is_provisional = 0 jika kamu ingin hasil analisis yang paling akurat dan sudah final."
