
# Praktikum Sistem Terdistribusi dan Terdesentralisasi/07

**Nama :** Hafidza Nur Afifah  
**NIM :** 235410012  
**Kelas :** Informatika 1  

<div align="justify">

# Modul 8 — Arsitektur Microservices untuk Sistem Terdistribusi (Versi Windows)

---

# 1. Prasyarat

## A. Install Python dan UV di Windows

### 1. Download Python

Download Python melalui website resmi Python kemudian lakukan instalasi seperti biasa. Pada saat instalasi, centang opsi **Add Python to PATH** agar Python dapat dijalankan melalui Command Prompt.

---

### 2. Cek Python

Setelah proses instalasi selesai, buka Command Prompt kemudian jalankan perintah berikut untuk memastikan Python sudah berhasil terinstall.

```bash
python --version
````

Apabila berhasil, maka akan muncul versi Python yang digunakan.

<div align="center">

<img width="698" height="205" alt="gambar" src="https://github.com/user-attachments/assets/307c4f8b-bc1b-42d6-ba70-c2ecea36ce49" />

<br>

**Gambar 1. Hasil pengecekan versi Python**

</div>

---

## B. Install UV

Selanjutnya install UV menggunakan perintah berikut.

```bash
pip install uv
```

Untuk memastikan UV berhasil terinstall, jalankan perintah berikut.

```bash
uv --version
```

<div align="center">

<img width="975" height="364" alt="gambar" src="https://github.com/user-attachments/assets/faa59a76-86dd-4d72-813e-2bb6e89c7430" />

<br>

**Gambar 2. Install dan pengecekan UV**

</div>

---

# 2. Membuat Folder Project

Buat folder project `microservices-fastapi` kemudian masuk ke dalam folder tersebut menggunakan Command Prompt.

```bash
mkdir microservices-fastapi
cd microservices-fastapi
```

---

# 3. Membuat Virtual Environment

Jalankan perintah berikut.

```bash
uv venv --python 3.14
```

Aktifkan virtual environment.

```bash
.venv\Scripts\activate
```

<div align="center">

<img width="975" height="294" alt="gambar" src="https://github.com/user-attachments/assets/80cc3bad-159e-4196-a09e-f4aad9ba1394" />

<br>

**Gambar 3. Pembuatan virtual environment**

</div>

---

# 4. Install FastAPI dan SQLModel

Install library FastAPI, Uvicorn, dan SQLModel menggunakan perintah berikut.

```bash
uv pip install fastapi uvicorn sqlmodel
```

<div align="center">

<img width="975" height="808" alt="gambar" src="https://github.com/user-attachments/assets/6f07d796-104d-4bdf-9a11-a0d473da7ad8" />

<br>

**Gambar 4. Install FastAPI dan SQLModel**

</div>

---

# 5. Install SQLite untuk Windows

Untuk memastikan SQLite berhasil terinstall, jalankan perintah berikut.

```bash
sqlite3 --version
```

<div align="center">

<img width="975" height="157" alt="gambar" src="https://github.com/user-attachments/assets/6fc258ef-6070-4750-ba04-c2d44fead82d" />

<br>

**Gambar 5. Pengecekan SQLite**

</div>

---

# 6. Membuat Database SQLite

Masuk ke SQLite menggunakan perintah berikut.

```bash
sqlite3 departemen-sdm.db
```

Kemudian buat tabel `sdm` menggunakan query berikut.

```sql
CREATE TABLE sdm (
    id INTEGER PRIMARY KEY,
    npp CHAR(6),
    nama VARCHAR(50)
);
```

Tambahkan data ke dalam tabel.

```sql
INSERT INTO sdm (npp, nama) VALUES('112233', 'Karyawan 1');
INSERT INTO sdm (npp, nama) VALUES('223344', 'Karyawan 2');
INSERT INTO sdm (npp, nama) VALUES('334455', 'Karyawan 3');
```

Lihat isi tabel.

```sql
SELECT * FROM sdm;
```

<div align="center">

<img width="975" height="848" alt="gambar" src="https://github.com/user-attachments/assets/b37710b3-4737-4546-95f3-1549ae34bcf0" />

<br>

<img width="975" height="947" alt="gambar" src="https://github.com/user-attachments/assets/1eb090c1-1497-4ad8-9ca8-7a0465e37eea" />

<br>

**Gambar 6. Pembuatan database SQLite dan tabel SDM**

</div>

---

# 7. Membuat REST API FastAPI

## service.py

<div align="center">

<img width="975" height="1005" alt="gambar" src="https://github.com/user-attachments/assets/09212c60-1318-45f8-8313-966d65ff0143" />

<br>

**Gambar 7. Source code REST API FastAPI**

</div>

Source code tersebut digunakan untuk membuat REST API endpoint `/sdm/` yang berfungsi menampilkan seluruh data SDM dari database SQLite.

---

# 8. Menjalankan REST API

Untuk menjalankan REST API FastAPI gunakan perintah berikut.

```bash
uvicorn service:app --reload
```

Jika berhasil dijalankan maka akan muncul informasi bahwa server berjalan pada alamat `http://127.0.0.1:8000`.

<div align="center">

<img width="975" height="210" alt="gambar" src="https://github.com/user-attachments/assets/bbf15652-8a59-49fa-88df-8b9965aaec2f" />

<br>

**Gambar 8. Menjalankan server FastAPI**

</div>

---

# 9. Mengakses REST API

Buka browser kemudian akses alamat berikut.

```text
http://127.0.0.1:8000/sdm/
```

REST API akan menampilkan data SDM dalam format JSON.

<div align="center">

<img width="975" height="585" alt="gambar" src="https://github.com/user-attachments/assets/1c6a5d4f-4529-4628-8568-c3aa51f2a1cf" />

<br>

**Gambar 9. Hasil REST API pada browser**

</div>

---

# 10. Menampilkan dengan CURL

Buka CMD baru kemudian jalankan perintah berikut.

```bash
curl http://127.0.0.1:8000/sdm/
```

Perintah curl digunakan untuk mengakses endpoint REST API melalui terminal.

<div align="center">

<img width="975" height="62" alt="gambar" src="https://github.com/user-attachments/assets/67bc8a27-3660-4be0-9587-85313f8b9ddb" />

<br>

<img width="975" height="188" alt="gambar" src="https://github.com/user-attachments/assets/594f17bf-0544-455c-a790-08a2a069d9b8" />

<br>

**Gambar 10. Hasil REST API menggunakan curl**

</div>

---

# 11. Struktur Folder Project

Berikut struktur folder project yang digunakan.

```text
microservices-fastapi/
│
├── .venv
├── service.py
├── requirements
├── departemen-sdm.db
├── .python-version
```

---

# Tugas Tambahan

## 1. Membuat Tabel Baru Menggunakan SQLite

Pada tugas ini dibuat tabel baru bernama `produk` yang memiliki tipe data INT, CHAR, VARCHAR, BOOLEAN, dan FLOAT.

```sql
CREATE TABLE produk (
    id INTEGER PRIMARY KEY,
    kode CHAR(5),
    nama VARCHAR(50),
    stok INT,
    tersedia BOOLEAN,
    harga FLOAT
);
```

<div align="center">

<img width="975" height="387" alt="gambar" src="https://github.com/user-attachments/assets/55331ca2-96e2-4c77-b2e1-cefe3f3d8700" />

<br>

**Gambar 11. Pembuatan tabel produk**

</div>

---

## 2. Mengisi 5 Data Menggunakan Script Python

Buat file `insert_produk.py` untuk mengisikan data ke tabel produk.

<div align="center">

<img width="975" height="845" alt="gambar" src="https://github.com/user-attachments/assets/7a59816b-d483-4a05-9198-0e90fce79af0" />

<br>

**Gambar 12. Tampilan file insert_produk.py**

</div>

Jalankan script berikut.

```bash
python insert_produk.py
```

<div align="center">

<img width="975" height="136" alt="gambar" src="https://github.com/user-attachments/assets/673d9281-3e66-4874-b92a-bf5e26cd0e36" />

<br>

**Gambar 13. Menambahkan data produk**

</div>

---

## 3. Membuat RESTful API Endpoint

Buat endpoint baru `/produk/` pada FastAPI dengan nama file `main.py` untuk menampilkan seluruh data produk.

<div align="center">

<img width="975" height="923" alt="gambar" src="https://github.com/user-attachments/assets/63f892a5-c251-4ba2-b9fd-fea41019f6ec" />

<br>

**Gambar 14. Tampilan file main.py endpoint REST API produk**

</div>

---

## 4. Menampilkan REST API Menggunakan Curl

Gunakan perintah berikut untuk menampilkan endpoint produk menggunakan curl.

```bash
curl http://127.0.0.1:8000/produk/
```

Hasil endpoint akan tampil dalam format JSON.

<div align="center">

<img width="975" height="94" alt="gambar" src="https://github.com/user-attachments/assets/1e5f0216-aadc-4255-b008-2f736ad84dc3" />

<br>

**Gambar 15. Hasil endpoint produk menggunakan curl**

<br><br>

<img width="975" height="1241" alt="gambar" src="https://github.com/user-attachments/assets/ba308896-a52c-45ec-9807-33bb5bd4d41e" />

<br><br>

<img width="975" height="359" alt="gambar" src="https://github.com/user-attachments/assets/c862ad6c-15c7-4d03-bd59-0e322bbacb78" />

<br>

**Gambar 16. Tampilan pada browser [http://127.0.0.1:8000/produk/](http://127.0.0.1:8000/produk/)**

</div>

---

# Kesimpulan

Pada praktikum ini berhasil dibuat sebuah REST API sederhana menggunakan FastAPI dan SQLite pada sistem operasi Windows. REST API dapat digunakan untuk menampilkan data SDM maupun data produk menggunakan endpoint tertentu. Selain itu, pengujian endpoint juga dapat dilakukan menggunakan browser maupun command line menggunakan curl.

</div>
```
