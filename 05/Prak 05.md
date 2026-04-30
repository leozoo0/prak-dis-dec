# Praktikum Sistem Terdistribusi dan Terdesentralisasi/05

**Nama:** Hafidza Nur Afifah  
**NIM:** 235410012  
**Kelas:** Informatika 1  

---

## FAULT TOLERANCE  
### 4.1 Load Balancing Aplikasi (Windows)

<p align="justify">
Load balancing adalah teknik dalam sistem terdistribusi yang digunakan untuk membagi beban kerja ke beberapa instance aplikasi. Tujuannya adalah agar aplikasi tetap berjalan dengan baik, tidak mudah down, dan dapat melayani banyak pengguna (high availability). Pada praktikum ini, load balancing dilakukan dengan bantuan Docker dan Nginx.
</p>

---

**1. Persiapan Software**

<p align="justify">
Pada tahap ini dipersiapkan software yang dibutuhkan, seperti Python, virtual environment, dan Docker. Virtual environment digunakan agar library yang diinstall tidak bercampur dengan sistem utama.
</p>

---

**2. Buat Folder Project**

<p align="justify">
Pada langkah ini dibuat folder sebagai tempat menyimpan seluruh file praktikum.
</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/c2486c03-c94b-45fa-a6a6-d89ee99eed22" width="975">
</p>
<p align="center"><b>Gambar 1. Pembuatan folder project</b></p>

---

**3. Buat Virtual Environment**

<p align="justify">
Virtual environment dibuat untuk memisahkan environment Python agar lebih mudah dikelola.
</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/59239ff4-760b-4a20-8933-6f8490cb4b96" width="975">
</p>
<p align="center"><b>Gambar 2. Pembuatan virtual environment</b></p>

---

**4. Install Blacksheep**

<p align="justify">
Blacksheep adalah framework Python yang digunakan untuk membuat aplikasi web pada praktikum ini.
</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/64739427-595b-40be-b38e-d6a0d06e1ff5" width="975">
</p>
<p align="center"><b>Gambar 3. Proses install Blacksheep</b></p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/4915da0c-16c7-46c2-ad5c-49bb42578f5e" width="975">
</p>
<p align="center"><b>Gambar 4. Hasil install Blacksheep</b></p>

---

**5. Buat Aplikasi Blacksheep**

<p align="justify">
Pada tahap ini dibuat aplikasi web menggunakan Blacksheep. Aplikasi ini nantinya akan digunakan untuk uji coba load balancing.
</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/f9708885-d1fb-48c9-8de0-0cc6d3529663" width="975">
</p>
<p align="center"><b>Gambar 5. Pembuatan aplikasi Blacksheep</b></p>

---

**6. Jalankan Aplikasi**  
http://localhost:44777  

<p align="justify">
Aplikasi dijalankan untuk memastikan bahwa program sudah berjalan dengan baik sebelum dilakukan proses selanjutnya.
</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/62c8f666-d397-42cf-9e72-8673e9199cec" width="975">
</p>
<p align="center"><b>Gambar 6. Menjalankan aplikasi</b></p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/4050a8a2-0c64-45df-aa47-e4f14a456eb4" width="975">
</p>
<p align="center"><b>Gambar 7. Tampilan aplikasi di browser</b></p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/05d1bb5f-b841-4e1e-af0a-6bfb60eac7d4" width="975">
</p>
<p align="center"><b>Gambar 8. Respon aplikasi</b></p>

---

**7. Siapkan Docker**

<p align="justify">
Docker digunakan untuk menjalankan aplikasi dalam container.
</p>

---

**8. Jalankan Docker Compose**

<p align="justify">
Docker Compose digunakan untuk menjalankan beberapa container sekaligus, yaitu aplikasi dan Nginx sebagai load balancer.
</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/e93ef5d9-dcbf-473f-8a94-22861d0767aa" width="975">
</p>
<p align="center"><b>Gambar 9. Menjalankan Docker Compose</b></p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/8696258c-abe4-4bba-8041-b21f102233a7" width="975">
</p>
<p align="center"><b>Gambar 10. Container berjalan</b></p>

---

<p align="justify">
Tampilan pada saat akses di browser http://localhost menunjukkan bahwa aplikasi sudah berjalan melalui Nginx. Port yang digunakan adalah port 80 karena Nginx berfungsi sebagai proxy.
</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/43bf5bc2-96fb-43b0-8455-842bb88f5583" width="975">
</p>
<p align="center"><b>Gambar 11. Tampilan load balancing</b></p>

---

**9. Load Balancing**  
Tampilan docker logs nginx  

<p align="justify">
Load balancing bekerja dengan cara membagi request ke beberapa container aplikasi. Hal ini dapat dilihat dari log yang menunjukkan request masuk ke container yang berbeda.
</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/92b4d65c-abf9-441a-9ec3-b3a3a0b4f0b8" width="975">
</p>
<p align="center"><b>Gambar 12. Log load balancing</b></p>

---

**10. Matikan semua Container**

<p align="justify">
Setelah praktikum selesai, semua container dihentikan untuk mengakhiri proses yang berjalan.
</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/a9bb5011-1a58-4bd1-ac2d-fbf67cfc711d" width="975">
</p>
<p align="center"><b>Gambar 13. Menghentikan container</b></p>

---

## 4.2 Failure Detection (Windows)

<p align="justify">
Failure Detection adalah proses untuk mengetahui apakah suatu server atau sistem sedang aktif atau mengalami kegagalan.
</p>

---

**Install Library pada folder failure-detection**

<p align="justify">
Pada tahap ini dilakukan instalasi library yang diperlukan untuk mendukung program deteksi kegagalan.
</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/48dbf182-b8d5-484a-a0e1-bac02c79ff07" width="975">
</p>
<p align="center"><b>Gambar 14. Install library</b></p>

---

### Heartbeat (check-server.py)

<p align="justify">
Heartbeat digunakan untuk mengecek apakah server aktif dengan cara mengirim request secara berkala.
</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/3a525eff-b798-4a61-87de-b112fcff2bad" width="975">
</p>
<p align="center"><b>Gambar 15. Script heartbeat</b></p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/5e80a860-5503-46ab-bd35-17a874e405e8" width="975">
</p>
<p align="center"><b>Gambar 16. Hasil heartbeat</b></p>

<p align="justify">
Jika server tidak aktif, maka akan muncul “Server DOWN”. Jika server aktif, maka akan muncul “Server UP”. Ini menunjukkan bahwa metode heartbeat dapat digunakan untuk mengecek kondisi server.
</p>

---

### Retry (check-retry.py)

<p align="justify">
Retry adalah cara untuk mencoba kembali koneksi jika terjadi kegagalan.
</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/537b8996-b2a7-4499-bcae-ff8ba417b694" width="975">
</p>
<p align="center"><b>Gambar 17. Percobaan retry</b></p>

<p align="justify">
Pada percobaan retry, ketika server tidak aktif, script akan mencoba melakukan koneksi sebanyak beberapa kali sesuai konfigurasi. Setiap percobaan akan menampilkan pesan hingga akhirnya gagal karena server tidak merespon. Sebaliknya, ketika server dalam kondisi aktif, script berhasil terhubung pada percobaan pertama dan menampilkan hasil seperti pada gambar. Dapat disimpulkan bahwa mekanisme retry memungkinkan sistem untuk mencoba kembali koneksi yang gagal.
</p>

---

### Circuit Breaker (check-circuit-breaker.py)

<p align="justify">
Pada percobaan circuit breaker, ketika server tidak aktif, script akan mengalami kegagalan koneksi secara berulang. Setelah jumlah kegagalan mencapai batas tertentu, sistem akan mengubah status menjadi “OPEN”, yang berarti permintaan ke server akan dihentikan sementara untuk mencegah beban berlebih. Setelah beberapa waktu, sistem mencoba kembali dalam kondisi “HALF-OPEN” untuk mengecek apakah server sudah pulih. Jika server aktif, maka status akan kembali ke “CLOSED” dan koneksi berjalan normal. 

---
