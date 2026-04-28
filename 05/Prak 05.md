
MODUL 5 FAULT TOLERANCE
4.1 Load Balancing Aplikasi (Windows)

1. Persiapan Software
2. Buat Folder Project
<img width="975" height="395" alt="gambar" src="https://github.com/user-attachments/assets/c2486c03-c94b-45fa-a6a6-d89ee99eed22" />
3. Buat Virtual Environment
<img width="975" height="183" alt="gambar" src="https://github.com/user-attachments/assets/59239ff4-760b-4a20-8933-6f8490cb4b96" />
4. Install Blacksheep
<img width="975" height="737" alt="gambar" src="https://github.com/user-attachments/assets/64739427-595b-40be-b38e-d6a0d06e1ff5" />
<img width="975" height="1025" alt="gambar" src="https://github.com/user-attachments/assets/4915da0c-16c7-46c2-ad5c-49bb42578f5e" />
5. Buat Aplikasi Blacksheep 
<img width="975" height="472" alt="gambar" src="https://github.com/user-attachments/assets/f9708885-d1fb-48c9-8de0-0cc6d3529663" />
6. Jalankan Aplikasi 
http://localhost:44777
<img width="975" height="330" alt="gambar" src="https://github.com/user-attachments/assets/62c8f666-d397-42cf-9e72-8673e9199cec" />
<img width="975" height="510" alt="gambar" src="https://github.com/user-attachments/assets/4050a8a2-0c64-45df-aa47-e4f14a456eb4" />
<img width="975" height="394" alt="gambar" src="https://github.com/user-attachments/assets/05d1bb5f-b841-4e1e-af0a-6bfb60eac7d4" />
7. Siapkan Docker
8. Jalankan Docker Compose
<img width="975" height="531" alt="gambar" src="https://github.com/user-attachments/assets/e93ef5d9-dcbf-473f-8a94-22861d0767aa" />
<img width="975" height="362" alt="gambar" src="https://github.com/user-attachments/assets/8696258c-abe4-4bba-8041-b21f102233a7" />

Tampilan pada saat akses di browser
http://localhost
<img width="975" height="514" alt="gambar" src="https://github.com/user-attachments/assets/43bf5bc2-96fb-43b0-8455-842bb88f5583" />
9. Load Balancing
Tampilan docker logs nginx
<img width="975" height="448" alt="gambar" src="https://github.com/user-attachments/assets/92b4d65c-abf9-441a-9ec3-b3a3a0b4f0b8" />
10. Matikan semua Container
<img width="975" height="285" alt="gambar" src="https://github.com/user-attachments/assets/a9bb5011-1a58-4bd1-ac2d-fbf67cfc711d" />

4.2 Failure Detection (Windows)

Install Library pada folder failure-detection
<img width="975" height="886" alt="gambar" src="https://github.com/user-attachments/assets/48dbf182-b8d5-484a-a0e1-bac02c79ff07" />

 
Heartbeat (check-server.py)
<img width="975" height="235" alt="gambar" src="https://github.com/user-attachments/assets/3a525eff-b798-4a61-87de-b112fcff2bad" />
<img width="975" height="421" alt="gambar" src="https://github.com/user-attachments/assets/5e80a860-5503-46ab-bd35-17a874e405e8" />
Pada percobaan pertama, script dijalankan ketika aplikasi BlackSheep tidak aktif pada port 44777. Hasil yang diperoleh adalah “Server DOWN”, yang menunjukkan bahwa tidak ada layanan yang merespon permintaan sehingga koneksi gagal dilakukan. Selanjutnya, aplikasi BlackSheep diaktifkan menggunakan Uvicorn pada port 44777, kemudian script dijalankan kembali. Pada kondisi ini, hasil yang diperoleh adalah “Server UP”, yang menandakan bahwa server berhasil diakses, hasil ini menunjukkan bahwa metode heartbeat dapat digunakan untuk mendeteksi apakah suatu server dalam kondisi aktif atau tidak berdasarkan keberhasilan koneksi.

Retry (check-retry.py)
<img width="975" height="342" alt="gambar" src="https://github.com/user-attachments/assets/537b8996-b2a7-4499-bcae-ff8ba417b694" /> 
Pada percobaan retry, ketika server tidak aktif, script akan mencoba melakukan koneksi sebanyak beberapa kali sesuai konfigurasi. Setiap percobaan akan menampilkan pesan hingga akhirnya gagal karena server tidak merespon. Sebaliknya, ketika server dalam kondisi aktif, script berhasil terhubung pada percobaan pertama dan menampilkan hasil seperti pada gambar. Dapat disimpulkan bahwa mekanisme retry memungkinkan sistem untuk mencoba kembali koneksi yang gagal.

Circuit Breaker (check-circuit-breaker.py)
Pada percobaan circuit breaker, ketika server tidak aktif, script akan mengalami kegagalan koneksi secara berulang. Setelah jumlah kegagalan mencapai batas tertentu, sistem akan mengubah status menjadi “OPEN”, yang berarti permintaan ke server akan dihentikan sementara untuk mencegah beban berlebih. Setelah beberapa waktu, sistem mencoba kembali dalam kondisi “HALF-OPEN” untuk mengecek apakah server sudah pulih. Jika server aktif, maka status akan kembali ke “CLOSED” dan koneksi berjalan normal. 
