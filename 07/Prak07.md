# Praktikum Sistem Terdistribusi dan Terdesentralisasi/07

Nama : Hafidza Nur Afifah  
NIM : 235410012  
Kelas : Informatika 1  

# A. PERSIAPAN AWAL
## 1. Install Tools

Pada tahap awal praktikum, dilakukan instalasi beberapa tools yang dibutuhkan untuk menjalankan aplikasi berbasis Python dan Flask. Tools yang digunakan meliputi:

* Python 3.14.4
* Git
* Docker Desktop

Setelah proses instalasi selesai, dilakukan pengecekan versi untuk memastikan seluruh tools telah terpasang dengan baik menggunakan perintah berikut:

```bash
python --version
git --version
docker --version
```

<img width="844" height="491" alt="gambar" src="https://github.com/user-attachments/assets/fdf4490a-8e63-4c91-a75e-475376323f51" />

<p align="center"><b>Gambar 1. Hasil pengecekan versi Python, Git, dan Docker</b></p>

<p align="justify">
Gambar di atas menunjukkan bahwa Python, Git, dan Docker telah berhasil terinstal pada sistem. Pengecekan versi dilakukan untuk memastikan environment pengembangan siap digunakan sebelum melanjutkan ke tahap berikutnya.
</p>

---

## 2. Menyiapkan Folder Project

Tahap berikutnya adalah membuat folder project sebagai tempat penyimpanan seluruh file dan source code aplikasi Flask yang akan dikembangkan.

<img width="675" height="280" alt="gambar" src="https://github.com/user-attachments/assets/15458ed8-1bf9-4ea6-ac32-cfc26313d6e4" />

<p align="center"><b>Gambar 2. Pembuatan folder project</b></p>

<p align="justify">
Folder project digunakan untuk mengorganisasi file aplikasi sehingga lebih terstruktur dan mudah dikelola.
</p>

---

# B. SOURCE CODE

<p align="justify">
Pada tahap ini source code aplikasi Flask disiapkan. Source code akan dijalankan menggunakan environment Python yang telah dibuat sebelumnya.
</p>

---

# C. MEMBUAT ENVIRONMENT PYTHON

## 1. Membuat Virtual Environment
Perintah untuk membuat virtual environment:

```bash
python -m venv venv
```

Aktivasi virtual environment:

```bash
venv\Scripts\activate
```

<img width="975" height="264" alt="gambar" src="https://github.com/user-attachments/assets/78456506-ee9d-413f-ac84-814495e4a07f" />

<p align="center"><b>Gambar 3. Pembuatan dan aktivasi virtual environment</b></p>

<p align="justify">
Gambar di atas menunjukkan proses pembuatan virtual environment dan aktivasi environment Python.

---

## 2. Install

```bash
uv pip install -e .
```

<img width="975" height="615" alt="gambar" src="https://github.com/user-attachments/assets/b9a1df80-bcd7-491f-af6c-77416febf03e" />

<p align="center"><b>Gambar 4. Proses instalasi aplikasi</b></p>

<p align="justify">
Proses instalasi dilakukan untuk memastikan seluruh library dan package yang diperlukan aplikasi Flask tersedia dan dapat digunakan saat pengujian aplikasi.
</p>

---

# D. MENJALANKAN APLIKASI FLASK (LOCAL TEST)

## 1. Inisialisasi Database

Sebelum aplikasi dijalankan, database perlu diinisialisasi terlebih dahulu menggunakan perintah berikut:

```bash
flask --app flaskr init-db
```

## 2. Menjalankan Aplikasi

Setelah database berhasil dibuat, aplikasi Flask dapat dijalankan menggunakan perintah:

```bash
flask --app flaskr run
```

<img width="975" height="507" alt="gambar" src="https://github.com/user-attachments/assets/f0b317fc-2e01-45cd-9220-52b1169f42ad" />

<p align="center"><b>Gambar 5. Menjalankan aplikasi Flask</b></p>

<p align="justify">
Gambar di atas menunjukkan bahwa aplikasi Flask berhasil dijalankan pada local server. Server berjalan pada alamat localhost dengan port default 5000.
</p>

---

## 3. Mengakses Aplikasi pada Browser

Aplikasi dapat diakses melalui browser menggunakan alamat berikut:

```bash
http://127.0.0.1:5000
```

<img width="975" height="438" alt="gambar" src="https://github.com/user-attachments/assets/e7cce9a7-49b2-4118-902e-24229cc4f3a6" />

<p align="center"><b>Gambar 6. Tampilan awal aplikasi Flask pada browser</b></p>

<p align="justify">
Tampilan di atas menunjukkan halaman utama aplikasi Flask berhasil ditampilkan melalui browser. Hal ini menandakan aplikasi telah berjalan dengan baik pada local server.
</p>

---

# E. TESTING APLIKASI

## 1. Register User

Tahap pertama pengujian dilakukan dengan membuat akun baru melalui menu register.

<img width="975" height="668" alt="gambar" src="https://github.com/user-attachments/assets/db372160-d448-40a6-a6cc-8d346dc58887" />

<p align="center"><b>Gambar 7. Halaman register user</b></p>

<p align="justify">
Halaman register digunakan untuk menambahkan akun pengguna baru ke dalam sistem aplikasi blog Flask.
</p>

---

## 2. Login User

Setelah akun berhasil dibuat, pengguna dapat melakukan login menggunakan username dan password yang telah didaftarkan.

<img width="975" height="668" alt="gambar" src="https://github.com/user-attachments/assets/d2b434b8-1ac1-4c44-8045-246623c8d48f" />

<p align="center"><b>Gambar 8. Halaman login user</b></p>

<p align="justify">
Halaman login digunakan untuk melakukan autentikasi pengguna sebelum mengakses fitur aplikasi yang lebih lengkap.
</p>

---

## 3. Membuat Posting Blog

Tahap terakhir pengujian dilakukan dengan mencoba membuat postingan blog baru melalui aplikasi Flask.

<img width="975" height="909" alt="gambar" src="https://github.com/user-attachments/assets/ee47567e-d702-482c-96d1-e1ea6298a033" />

<p align="center"><b>Gambar 9. Proses membuat posting blog</b></p>

<p align="justify">
Gambar di atas menunjukkan proses pembuatan posting blog berhasil dilakukan. Hal ini menandakan bahwa fitur utama aplikasi Flask telah berjalan dengan baik.
</p>
