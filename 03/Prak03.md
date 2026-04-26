# Praktikum Sistem Terdistribusi dan Terdesentralisasi/03

Nama : Hafidza Nur Afifah  
NIM  : 235410012  
Kelas : Informatika 1  <p>

<p>Sebelumnya siapkan Folder Project</p>

<pre>
cd C/Users/LEOZ/praktikum_modul13
</pre>

<p align="center">
  <img width="975" height="444" alt="gambar" src="https://github.com/user-attachments/assets/658317e4-c13c-43db-bb53-5161b7d368a1" />
</p>

<h3>3.1 Sinkronisasi Waktu (Windows - NetTime)</h3>

<p><b>1. Proses Sinkronisasi</b></p>

<p align="center">
  <img width="975" height="551" alt="gambar" src="https://github.com/user-attachments/assets/6491fea3-60ea-4b7c-8a47-2561adb36b62" />
  <br><br>
  <img width="794" height="570" alt="gambar" src="https://github.com/user-attachments/assets/bd58bebf-71ed-43ef-bc40-e502b453340e" />
</p>

<p><b>2. Penjelasan Proses Sinkronisasi</b></p>

<p align="justify">
Sinkronisasi waktu menggunakan NetTime dilakukan dengan cara komputer menghubungi server waktu menggunakan Network Time Protocol untuk meminta waktu yang akurat. Server kemudian mengirimkan waktu saat ini, lalu NetTime menghitung selisih antara waktu server dan waktu pada komputer. Setelah itu, sistem akan menyesuaikan waktu komputer agar sesuai dengan server, baik secara langsung maupun bertahap. Tujuan dari proses ini adalah agar semua komputer dalam sistem memiliki waktu yang sama sehingga urutan kejadian dapat dicatat dengan benar dan tidak terjadi kesalahan dalam sistem terdistribusi.
</p>

<h3>3.2 Vector Clock</h3>

<p align="center">
  <img width="975" height="629" alt="gambar" src="https://github.com/user-attachments/assets/062951b7-7b12-4c9e-a590-bf6b120cb51c" />
</p>

<p align="justify">
<b>1.</b> Berdasarkan hasil eksekusi program, terdapat tiga proses yaitu P0, P1, dan P2 yang masing-masing memiliki vector clock awal [0,0,0].  
Proses P0 melakukan dua event sehingga nilai vector clock menjadi [2,0,0]. Selanjutnya, P1 menerima pesan dari P0 sehingga nilai vector clock diperbarui menjadi [2,1,0].  
Proses P2 awalnya berjalan sendiri dengan nilai [0,0,1], namun setelah menerima pesan dari P1, vector clock diperbarui menjadi [2,2,2].
</p>

<p align="justify">
Dari hasil perbandingan:  
</p>• VC0 terjadi sebelum VC1 (True), karena semua elemen VC0 lebih kecil atau sama dengan VC1.  
</p>• VC1 tidak terjadi sebelum VC0 (False).  
</p>• VC0 dan VC2 tidak bersifat concurrent karena terdapat hubungan komunikasi antar proses.
</p>

<p><b>2. Buat file baru,</b></p>

<h3>3.3 Multithread (Tanpa Sinkronisasi)</h3>

<p align="center">
  <img width="819" height="716" alt="gambar" src="https://github.com/user-attachments/assets/bd09f160-a59f-4223-820a-f73b10004e65" />
</p>

<p align="justify">
<b>1.</b> Hasil Percobaan, program dijalankan sebanyak 2 kali dan menghasilkan output yang berbeda urutan penyelesaiannya, meskipun waktu setiap task sama (5 detik).
</p>

<p align="justify">
Dari gambar:  
</p>• Percobaan 1: Task D selesai lebih dulu, lalu C, A, B, E  
</p>• Percobaan 2: Task B selesai lebih dulu, lalu A, C, D, E
</p>

<p align="justify">
<b>2.</b> Perbedaan output tersebut terjadi karena program menggunakan multithreading. Semua task (A, B, C, D, E) dijalankan secara bersamaan (concurrent). Setiap thread berjalan independen dan dijadwalkan oleh sistem operasi. Urutan eksekusi dan penyelesaian thread tidak selalu sama setiap kali program dijalankan.
</p>

<h4>3.3.1 Race Condition</h4>

<p>race-conditions-01.py</p>

<p align="center">
  <img width="975" height="814" alt="gambar" src="https://github.com/user-attachments/assets/11ee6f10-54df-4733-a09d-cbf0c6a35250" />
</p>

<p>python race-conditions-02.py</p>

<p align="center">
  <img width="975" height="276" alt="gambar" src="https://github.com/user-attachments/assets/a7dd0e08-68d4-49f3-89ee-f2caf07e3ead" />
</p>

<p align="justify">
Race condition tidak terjadi pada program tersebut karena digunakan mekanisme lock (threading.Lock) yang berfungsi mengatur akses ke variabel bersama (balance). Dengan adanya with counter_lock, hanya satu thread yang dapat menjalankan proses pengecekan dan pengurangan saldo dalam satu waktu, sementara thread lainnya harus menunggu.
</p>

<h4>3.3.2 Deadlock</h4>

<p>python deadlock-01.py</p>

<p align="center">
  <img width="975" height="236" alt="gambar" src="https://github.com/user-attachments/assets/37ffa813-dca0-4d25-b32d-4e147c7c2241" />
</p>

<p align="justify">
Yang terjadi yakni Thread 1 menunggu resource A, Thread 2 menunggu resource B
</p>

<p>python deadlock-02.py</p>

<p align="center">
  <img width="975" height="394" alt="gambar" src="https://github.com/user-attachments/assets/4257241c-5ed6-4bee-9a2d-0b15dcc2976f" />
</p>

<p align="justify">
Deadlock tidak terjadi karena urutan akses resource diatur serta tidak saling tunggu
</p>

<h3>3.4 Algoritma Raft</h3>

<p>python raft.py</p>

<p align="center">
  <img width="975" height="1064" alt="gambar" src="https://github.com/user-attachments/assets/4132ff95-2d71-4559-92cb-55ca256d1047" />
  <br><br>
  <img width="829" height="1350" alt="gambar" src="https://github.com/user-attachments/assets/4f078816-baa3-4df2-b0c5-242f056b4f8a" />
  <br><br>
  <img width="844" height="1330" alt="gambar" src="https://github.com/user-attachments/assets/2b602689-db05-4f49-adf0-ded895e269cf" />
  <br><br>
  <img width="828" height="730" alt="gambar" src="https://github.com/user-attachments/assets/4c3aeb4d-c531-46f4-80fd-2e752c941ddf" />
</p>

<p align="justify">
Berdasarkan keluaran program, pada awalnya seluruh node berada dalam state follower. Ketika suatu node tidak menerima heartbeat dalam interval waktu tertentu, node tersebut bertransisi menjadi candidate dan memulai proses pemilihan dengan meminta suara (vote) dari node lain.
</p>

<p align="justify">
Dalam simulasi ini, kandidat memperoleh dukungan mayoritas sehingga ditetapkan sebagai leader. Setelah terpilih, leader mengirimkan heartbeat secara berkala kepada node lain untuk mempertahankan kepemimpinannya dan mencegah terjadinya pemilihan ulang.
</p>
