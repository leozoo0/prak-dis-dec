# Praktikum Sistem Terdistribusi dan Terdesentralisasi/10

**Nama : Hafidza Nur Afifah**  
**NIM : 235410012**  
**Kelas : Informatika 1**

<div align="justify">

# 0. Unduh YugabyteDB

<div align="center">
<img width="975" height="500" alt="gambar" src="https://github.com/user-attachments/assets/dc8392e8-38cd-4b77-94d3-744eca26b5ed" />

**Gambar 0.1 Halaman Unduhan YugabyteDB**
</div>

YugabyteDB diunduh melalui terminal langsung menggunakan perintah wget yang menyalin URL dari situs resmi. Terlihat pada screenshot bahwa file yang diunduh adalah yugabyte-2025.2.3.0-b149-linux-x86_64.tar.gz dengan ukuran 457 MB. Proses unduhan selesai dalam 1 menit 41 detik dengan kecepatan rata-rata 5.61 MB/s, dan diakhiri dengan konfirmasi yugabyte-2025.2.3.0-b149-linux-x86_64.tar.gz: OK yang menandakan file berhasil diunduh

# 1. Instalasi

## 1.1 Ekstraksi File

<div align="center">
<img width="608" height="651" alt="gambar" src="https://github.com/user-attachments/assets/17fa1e93-3fde-436c-8d70-1e0afa8aee73" />

**Gambar 1.1 Proses Ekstraksi YugabyteDB**
</div>

Pada langkah ini file hasil unduhan diekstrak sehingga seluruh komponen YugabyteDB dapat digunakan. Hasil ekstraksi menghasilkan direktori yang berisi file executable, tools, dan library yang diperlukan untuk menjalankan database.

## 1.2 Memindahkan ke Subdirektori

<div align="center">
<img width="975" height="524" alt="gambar" src="https://github.com/user-attachments/assets/869b8a8e-f0d7-4f9f-b779-326094d0f6d5" />

**Gambar 1.2 Pemindahan Direktori YugabyteDB**
</div>

Direktori hasil ekstraksi dipindahkan ke lokasi penyimpanan khusus agar lebih terorganisir. Pada bagian ini terlihat adanya error berupa Check failure stack trace yang muncul saat proses pemindahan direktori. Error ini berasal dari komponen yb::tserver::TabletServerMain yang menunjukkan ada masalah saat node tablet server mencoba berjalan. Setelah dilakukan pengecekan log dengan perintah tail -50 yugabyted.log, masalah dapat diidentifikasi dan proses dilanjutkan ke tahap berikutnya.

## 1.3 Menjalankan post_install.sh

<div align="center">
<img width="763" height="819" alt="gambar" src="https://github.com/user-attachments/assets/c5554d83-30da-4ab8-bfc6-63b9ede4c505" />

**Gambar 1.3 Menjalankan Script post_install.sh**
</div>

Script post_install.sh dijalankan untuk melakukan konfigurasi tambahan yang dibutuhkan oleh YugabyteDB. Proses ini memastikan seluruh dependensi dan pengaturan sistem telah siap digunakan. Semua komponen menampilkan status Pass dan diakhiri dengan INSTALL PASSED, yang berarti instalasi YugabyteDB telah berhasil dan semua dependensi berjalan dengan baik.

## 1.4 Membuat Environment Variables

<div align="center">
<img width="975" height="452" alt="gambar" src="https://github.com/user-attachments/assets/b9fe09eb-a680-456d-9529-dc9c1a750011" />

**Gambar 1.4 Konfigurasi Environment Variables**
</div>

Environment variable dibuat agar perintah YugabyteDB dapat dijalankan dari terminal tanpa perlu menuliskan path lengkap. Konfigurasi ini mempermudah penggunaan YugabyteDB pada setiap sesi shell.

## 1.5 Mengubah Ulimit

Pada tahap ini dilakukan penyesuaian nilai ulimit sesuai petunjuk modul. Pengaturan tersebut diperlukan agar YugabyteDB dapat menggunakan sumber daya sistem secara optimal, terutama terkait jumlah file dan proses yang dapat dibuka secara bersamaan.

# 2. Membuat Kluster

<div align="center">
<img width="975" height="383" alt="gambar" src="https://github.com/user-attachments/assets/70aa9d46-098f-4722-94de-a3c123d5c0b4" />

**Gambar 2.1 Persiapan Kluster YugabyteDB**
</div>

Pada praktikum ini dibuat kluster yang terdiri dari tiga node. Sebelum menjalankan node, direktori penyimpanan data untuk setiap node dibuat terlebih dahulu dengan perintah mkdir -p ~/var/node1, mkdir -p ~/var/node2, dan mkdir -p ~/var/node3. Hasil pengecekan dengan ls ~/var menampilkan direktori conf, data, logs, node1, node2, dan node3 yang sudah siap digunakan.

## 2.1 Node 1

<div align="center">
<img width="975" height="429" alt="gambar" src="https://github.com/user-attachments/assets/fe8dfb81-3100-42d1-8148-42b6cbcd67c9" />

**Gambar 2.2 Pembuatan Node 1**
</div>

Node pertama dijalankan sebagai node utama dalam kluster. Node ini menjadi titik awal yang akan digunakan oleh node lainnya untuk bergabung ke dalam sistem terdistribusi. Output menunjukkan YugabyteDB Started, UI ready, dan Data placement constraint successfully verified. Terdapat beberapa peringatan (WARNINGS) seperti transparent hugepages yang belum diaktifkan dan ntp/chrony yang belum terpasang, namun tidak menghalangi node berjalan. Status akhir menunjukkan Status: Running, YSQL Status: Ready, Replication Factor: 1, dan YugabyteDB UI tersedia di http://127.0.0.1:15433. Data disimpan di /root/var/node1/data.

## 2.2 Node 2

<div align="center">
<img width="975" height="469" alt="gambar" src="https://github.com/user-attachments/assets/18ff2b29-84b2-4aa3-992c-41a9bfb9fd20" />

**Gambar 2.3 Pembuatan Node 2**
</div>

Node kedua ditambahkan ke kluster menggunakan parameter join yang mengarah ke node pertama. Dengan bergabungnya node kedua, proses distribusi dan replikasi data mulai dapat dilakukan. Terlihat pada output bahwa node berhasil mendeteksi konfigurasi dari node pertama melalui parameter --join dengan pesan Fetching configs from join IP... dan Node joined a running cluster with UUID d0fe38cb-7c5f-4a68-914d-7bf4e17cd0b4. Status menunjukkan Running dan Ready dengan Replication Factor yang masih 1, serta data tersimpan di /root/var/node2/data.

## 2.3 Node 3

<div align="center">
<img width="975" height="472" alt="gambar" src="https://github.com/user-attachments/assets/94abd00d-88ba-4f71-addc-267b17a5397b" />

**Gambar 2.4 Pembuatan Node 3**
</div>

Node ketiga ditambahkan untuk melengkapi konfigurasi kluster tiga node. Konfigurasi ini mendukung fault tolerance sehingga sistem tetap tersedia walaupun salah satu node mengalami gangguan. Setelah node ketiga bergabung, Replication Factor otomatis naik menjadi 3, artinya setiap data kini direplikasi ke ketiga node sekaligus. Status menunjukkan Running dan Ready, data tersimpan di /root/var/node3/data, dan Universe UUID sama dengan node sebelumnya yaitu d0fe38cb-7c5f-4a68-914d-7bf4e17cd0b4 yang membuktikan ketiganya tergabung dalam satu kluster yang sama.

## 2.4 Data Placement

<div align="center">
<img width="975" height="280" alt="gambar" src="https://github.com/user-attachments/assets/817466a4-6b14-4d37-96d7-679e6d2a4385" />

**Gambar 2.5 Konfigurasi Data Placement**
</div>

Data placement digunakan untuk mengatur lokasi penyimpanan replika data pada setiap node. Hasilnya menampilkan Status: Configuration successful dan Fault Tolerance: Primary Cluster can survive at most any 1 availability zone failure. Artinya kluster ini sudah terkonfigurasi untuk tetap bisa beroperasi meskipun salah satu dari tiga zone (node) mengalami kegagalan.
Setelah semua node aktif, Web UI YugabyteDB dapat diakses di http://localhost:15433. Tampilan dashboard menunjukkan 3 nodes running, 13 tablets, Replication Factor 3, database version v2025.2.3.0, dan terdapat peringatan transparent hugepages yang disabled namun tidak berdampak pada jalannya sistem.

<div align="center">
<img width="975" height="473" alt="gambar" src="https://github.com/user-attachments/assets/1467101c-eebe-41da-a60d-7170312e547a" />

**Gambar 2.6 Tampilan Web UI YugabyteDB**
</div>

Setelah seluruh node aktif, status kluster dapat dipantau melalui web YugabyteDB. Halaman ini menampilkan informasi node, tablet, dan kondisi kluster secara keseluruhan.

# 3. Sharding

## 3.1 Range Sharding

<div align="center">
<img width="958" height="1209" alt="gambar" src="https://github.com/user-attachments/assets/f4d50b83-c725-40aa-8b0b-f00fb8ddff05" />

**Gambar 3.1 Implementasi Range Sharding**
</div>

Range sharding membagi data berdasarkan rentang nilai primary key. Primary key bertipe ASC menandakan penggunaan range sharding. Data kemudian diisi dengan 6 baris (user range 1 hingga user range 6) menggunakan perintah INSERT, dan hasil SELECT menampilkan data tersimpan berurutan sesuai id dari 1 sampai 6.

## 3.2 Range Sharding dengan Split

<div align="center">
<img width="975" height="294" alt="gambar" src="https://github.com/user-attachments/assets/ba6dc4d8-d34a-4417-98ab-e95a93e97f9b" />

**Gambar 3.2 Range Sharding Menggunakan Split**
</div>

Perintah SPLIT digunakan untuk membagi tabel menjadi beberapa tablet sejak awal pembuatan tabel. Pembagian ini membuat distribusi data lebih merata dan mempercepat query pada rentang nilai tertentu.

## 3.3 Explain Query Semua Data

<div align="center">
<img width="975" height="884" alt="gambar" src="https://github.com/user-attachments/assets/69472c1e-80fa-4679-aeaf-d081d366dcb2" />

**Gambar 3.3 Query Seluruh Data pada Range Sharding**
</div>

Perintah EXPLAIN (ANALYZE, DIST, COSTS OFF) SELECT * FROM user_range menghasilkan query plan dengan Seq Scan (sequential scan). Terlihat nilai Storage Table Rows Scanned: 6 yang berarti sistem membaca semua 6 baris. Hal ini wajar karena tidak ada kondisi filter, sehingga seluruh tablet perlu dipindai. Execution Time tercatat 450.142 ms.

## 3.4 Explain Query Satu Data

<div align="center">
<img width="892" height="712" alt="gambar" src="https://github.com/user-attachments/assets/16efafd1-95ae-465a-bea8-62860d2aafe3" />

**Gambar 3.4 Query Satu Data pada Range Sharding**
</div>

Perintah EXPLAIN untuk SELECT * FROM user_range WHERE id=1 menghasilkan query plan dengan Index Scan using user_range_pkey. Nilai Storage Table Rows Scanned: 1 membuktikan hanya 1 baris yang dibaca. Range sharding sangat efisien untuk pencarian data spesifik karena sistem langsung menuju lokasi tablet yang sesuai berdasarkan primary key, dengan Execution Time hanya 1.203 ms.

## 3.5 Explain Query Range

<div align="center">
<img width="797" height="633" alt="gambar" src="https://github.com/user-attachments/assets/c6f40ee2-9016-413b-bb8d-1f8c6d138f77" />

**Gambar 3.5 Query Range pada Range Sharding**
</div>

Perintah EXPLAIN untuk SELECT * FROM user_range WHERE id > 2 AND id < 6 menghasilkan Index Scan dengan kondisi ((id > 2) AND (id < 6)). Nilai Storage Table Rows Scanned: 3 membuktikan sistem hanya membaca 3 baris yang sesuai rentang, tidak memindai semua data. Ini adalah keunggulan utama range sharding: efisien untuk query berbasis rentang nilai dengan Execution Time 0.714 ms.

## 3.6 Hash Sharding - Query Semua Data

<div align="center">
<img width="975" height="1088" alt="gambar" src="https://github.com/user-attachments/assets/699ca4b5-c0db-4232-9a54-36e9f18f1269" />

**Gambar 3.6 Query Seluruh Data pada Hash Sharding**
</div>

Tabel user_hash dibuat dengan primary key tanpa ASC/DESC (id INT PRIMARY KEY) yang berarti menggunakan hash sharding secara default. Pada hash sharding saat seluruh data diminta, sistem akan mengakses seluruh tablet yang tersedia. Data diisi dengan 6 baris (id 1–6 dengan username A–F). Perintah EXPLAIN SELECT * FROM user_hash menghasilkan Seq Scan dengan Storage Table Rows Scanned: 6. Sama seperti range sharding, query tanpa filter membaca seluruh data dengan Execution Time 0.678 ms.

## 3.7 Hash Sharding - Query Satu Data

<div align="center">
<img width="802" height="548" alt="gambar" src="https://github.com/user-attachments/assets/ac702885-d613-492b-ac48-dfd71353d240" />

**Gambar 3.7 Query Satu Data pada Hash Sharding**
</div>

Perintah EXPLAIN untuk SELECT * FROM user_hash WHERE id=1 menghasilkan Index Scan using user_hash_pkey dengan Storage Table Rows Scanned: 1. Hash sharding tetap efisien untuk pencarian berdasarkan primary key karena lokasi tablet dapat langsung dihitung dari fungsi hash nilai id tersebut, dengan Execution Time 1.265 ms.

## 3.8 Hash Sharding - Query Range

<div align="center">
<img width="790" height="622" alt="gambar" src="https://github.com/user-attachments/assets/90e74d1b-4a56-48c8-907a-b818c4536bc5" />

**Gambar 3.8 Query Range pada Hash Sharding**
</div>

Hasil EXPLAIN menunjukkan bahwa query rentang kurang efisien pada hash sharding karena sistem perlu membaca data dari banyak tablet. Meskipun yang dibutuhkan hanya 3 baris, sistem tetap memindai semua 6 baris karena hash mengacak lokasi data di tablet sehingga tidak ada cara efisien untuk langsung menemukan data dalam suatu rentang nilai. Execution Time tercatat 1.566 ms.

# 4. Shutdown YugabyteDB

<div align="center">
<img width="975" height="255" alt="gambar" src="https://github.com/user-attachments/assets/9b724553-16ce-48f0-9424-06c61c03ac7b" />

**Gambar 4.1 Proses Shutdown YugabyteDB**
</div>

Setelah seluruh pengujian selesai dilakukan, YugabyteDB dihentikan menggunakan perintah shutdown. Langkah ini memastikan seluruh layanan database berhenti dengan aman dan data tetap tersimpan dengan baik.

# Kesimpulan

Berdasarkan praktikum yang telah dilakukan, YugabyteDB berhasil digunakan untuk membangun sistem basis data terdistribusi dengan tiga node. Pengujian menunjukkan bahwa range sharding lebih efektif untuk query berbasis rentang karena hanya membaca data yang diperlukan, sedangkan hash sharding lebih baik dalam pemerataan distribusi data namun kurang efisien untuk query rentang. Praktikum ini memberikan pemahaman mengenai klaster, replikasi, data placement, serta mekanisme sharding pada sistem basis data terdistribusi.

</div>
