# Modul 12 - Teknologi P2P (Peer-to-Peer)

### 0. Pengantar Teknologi P2P

Sebelum memulai praktikum, lakukan persiapan berikut.

---

### 1. Koneksi antar Node

### Menjalankan Program `simple_chat.py`

<p align="center">
<img width="625" height="978" alt="gambar" src="https://github.com/user-attachments/assets/1f6700aa-0382-4796-8a75-c1374336c156" />

<p align="center">
<b>Gambar 1.</b> Tampilan Program <code>simple_chat.py</code>
</p>

---

## Menjalankan Node Pertama

Pada CMD pertama jalankan:

```bash
python simple_chat.py
```

atau

```bash
py simple_chat.py
```

Masukkan konfigurasi berikut.

```text
PORT LOKAL : 5001
IP TARGET  : localhost
PORT TARGET: 5002
```

---

### Menjalankan Node Kedua

Pada CMD kedua jalankan:

```bash
python simple_chat.py
```

Kemudian masukkan konfigurasi berikut.

```text
PORT LOKAL : 5002
IP TARGET  : localhost
PORT TARGET: 5001
```

---

<p align="center">
  <img width="975" height="508" alt="gambar" src="https://github.com/user-attachments/assets/7524fe31-bc80-48d7-9e05-0e7fafefcdfa" />
</p>

<p align="center">
<b>Gambar 2.</b> Tampilan saat menjalankan kedua node
</p>

---

<p align="center">
<img width="975" height="508" alt="gambar" src="https://github.com/user-attachments/assets/622fb2d4-7dcf-463c-88c4-f7c575b876e1" />
</p>

<p align="center">
<b>Gambar 3.</b> Tampilan saat mengirim chat antar node
</p>

---

### Tugas

### 1. Jalankan program tersebut sehingga muncul chat antar node satu dengan node lainnya.

**Pembahasan**

Program ini merupakan simulasi komunikasi **peer-to-peer (P2P)** menggunakan socket TCP. Setiap node memiliki dua fungsi, yaitu sebagai server yang menerima koneksi dan sebagai client yang mengirim pesan ke node lain. Dengan menggunakan thread, kedua proses tersebut dapat berjalan secara bersamaan sehingga komunikasi berlangsung dua arah. Program dijalankan dengan membuka dua terminal berbeda (disimulasikan di satu mesin menggunakan port 5001 untuk node A dan port 5002 untuk node B).

---

### 2. Jelaskan bagian dalam program tersebut yang digunakan untuk

#### a. Membuka port

Fungsi `terima_pesan()` yakni pada bagian:

```python
server_socket.bind(('0.0.0.0', port_saya))
server_socket.listen(1)
```

Kode tersebut membuka port lokal, kemudian `listen(1)` membuat server siap menerima satu koneksi masuk.

---

#### b. Menerima pesan

```python
server_socket.accept()

while True:
    data = koneksi.recv(1024)
```

`accept()` menerima koneksi dari peer, sedangkan `recv(1024)` membaca data yang masuk maksimal 1024 byte.

---

#### c. Mengirim pesan

```python
client_socket.connect((ip_tujuan, port_tujuan))
client_socket.sendall(pesan.encode('utf-8'))
```

`connect()` membuat koneksi ke peer lain, sedangkan `sendall()` mengirimkan pesan yang diketik oleh pengguna.

---

### 2. DHT (Distributed Hash Table)

<p align="center">
<img width="1032" height="1210" alt="gambar" src="https://github.com/user-attachments/assets/e1ff0561-e938-4848-9461-5c6548182dd4" />
</p>

<p align="center">
<b>Gambar 4.</b> Tampilan Program <code>dht.py</code>
</p>

---

<p align="center">
<img width="975" height="599" alt="gambar" src="https://github.com/user-attachments/assets/465c1415-6daa-4521-a6d0-025fcc8c656d" />
</p>

<p align="center">
<b>Gambar 5.</b> Tampilan Output Program <code>dht.py</code>
</p>

---

### Tugas

### 1. Jalankan program tersebut.

---

### 2. Jelaskan dengan singkat apa yang dilakukan oleh program tersebut.

Program ini merupakan simulasi **Distributed Hash Table (DHT)**, yaitu metode untuk menyimpan dan mencari data pada jaringan peer-to-peer (P2P).

Pada program ini terdapat tiga node, yaitu **Node A**, **Node B**, dan **Node C**. Masing-masing node memiliki ID unik yang diperoleh dari hasil fungsi hash SHA-1. Selain node, setiap nama file juga diubah menjadi sebuah Key ID menggunakan fungsi hash yang sama.

Setelah Key ID diperoleh, program akan mencari node yang paling sesuai untuk menyimpan file tersebut. Node yang dipilih adalah node yang memiliki ID sama atau lebih besar dari Key ID. Dengan cara ini, setiap file akan memiliki lokasi penyimpanan yang sudah ditentukan sehingga pencarian menjadi lebih mudah.

Ketika pengguna mencari sebuah file, program akan menghitung kembali Key ID dari nama file, kemudian langsung menuju node yang bertanggung jawab menyimpan data tersebut. Jika file ada, maka data berhasil ditemukan. Jika tidak ada, program akan menampilkan bahwa data tidak ditemukan.

---

### 3. Jelaskan bagaimana DHT digunakan untuk proses pencarian data.

#### Algoritma Pencarian Data pada DHT

1. Pengguna memasukkan nama file yang ingin dicari.
2. Program menghitung nilai hash dari nama file sehingga menghasilkan Key ID.
3. Daftar node diurutkan berdasarkan ID sehingga membentuk sebuah ring.
4. Program mencari node pertama yang memiliki ID sama atau lebih besar dari Key ID.
5. Jika tidak ada node dengan ID yang lebih besar, pencarian kembali ke node pertama pada ring (wrap-around).
6. Request diarahkan ke node tersebut.
7. Node memeriksa apakah Key ID terdapat pada penyimpanan lokal.
8. Jika data ditemukan maka status **SUKSES**, jika tidak maka **GAGAL**.

---

### 3. Torrent

<p align="center">
<img width="756" height="719" alt="gambar" src="https://github.com/user-attachments/assets/5bac4fcd-ecbc-47c2-9b84-b8918631134d" />
</p>

<p align="center">
<b>Gambar 6.</b> Tampilan Program <code>read_torrent.py</code>
</p>

---

<p align="center">
<img width="975" height="300" alt="gambar" src="https://github.com/user-attachments/assets/ce3c51f4-3b4f-4f13-93c8-a2530c5b216a" />
</p>

<p align="center">
<b>Gambar 7.</b> Tampilan Output Program <code>read_torrent.py</code>
</p>

---

### Tugas

### 1. Jalankan program tersebut.

---

### 2. Jelaskan mengapa program tersebut memberi output seperti saat dijalankan.

Program membaca file `.torrent` menggunakan library **bcoding**, kemudian menampilkan metadata seperti **Tracker URL**, **Nama File**, **Ukuran File**, **Piece Length**, **Info Hash**, dan **Total Pieces**.

---

### 3. Ubahlah program sehingga lebih fleksibel

<p align="center">
<img width="685" height="785" alt="gambar" src="https://github.com/user-attachments/assets/e00ca22e-e9ff-4740-a859-b32a96721236" />
</p>

<p align="center">
<b>Gambar 8.</b> Tampilan Program <code>read_torrent.py</code>
</p>

---

<p align="center">
<img width="975" height="187" alt="gambar" src="https://github.com/user-attachments/assets/e6f65dd6-79e2-4c5c-9f6d-2dcdfcd97494" />
</p>

<p align="center">
<b>Gambar 9.</b> Tampilan Output Program <code>read_torrent.py</code>
</p>

Contoh menjalankan program:

```bash
python read_torrent.py "FreeBSD-15.0-RELEASE-amd64-bootonly.iso.torrent"
```
