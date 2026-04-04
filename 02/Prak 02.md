# Praktikum Sistem Terdistribusi dan Terdesentralisasi

Nama : Hafidza Nur Afifah  
NIM  : 235410012  
Kelas : Informatika 1  

---

## Proses pada Satu Node

1. Tampilan berbagai proses yang ada pada komputer (Windows).

<div align="center">

<img width="827" height="465" alt="gambar" src="https://github.com/user-attachments/assets/17617090-d26a-4b43-8160-a03bda81311f" />

Gambar 1 : Proses yang ada pada Windows (Task Manager)

</div>

2. Menjalankan aplikasi (Notepad) serta melihat prosesnya.

<div align="justify">

Pada saat kita membuka atau menjalankan suatu aplikasi (misalnya Notepad) system membuat proses baru, proses tersebut muncul di Task Manager. Pada Task Manager kita dapat mengamati nama proses yang muncul (misalnya Notepad) serta CPU/Memory yang digunakan.

</div>

<div align="center">

<img width="492" height="166" alt="gambar" src="https://github.com/user-attachments/assets/3659bfba-cbe5-4d40-a632-a440a48f5523" />

Gambar 2 : Contoh aplikasi (Notepad) yang sedang dijalankan

</div>

<div align="center">

<img width="827" height="465" alt="gambar" src="https://github.com/user-attachments/assets/80fe38c4-f441-47ef-9a4b-8d7d90cce92b" />

Gambar 3 : Tampilan task manager pada saat aplikasi (Notepad) dijalankan

</div>

3. Me-restart dan mematikan proses

<div align="center">

<img width="827" height="213" alt="gambar" src="https://github.com/user-attachments/assets/1eb9f90d-8171-47e0-803e-d175e0f86d26" />

Gambar 4 : Proses mematikan aplikasi (Notepad) yang sedang berjalan.

</div>

<div align="justify">

Untuk mematikan aplikasi tersebut melalui task manager dapat menggunakan tools end task atau dengan CMD, pada bagian ini saya menggunakan end task di bagian kanan atas task manager.

4. Bagian yang saya kerjakan yakni menampilkan semua proses yang sedang berjalan untuk mengetahui aplikasi yang berjalan dan penggunaan sumber daya komputer. Selanjutnya, saya membuka Notepad, memeriksa proses baru di Task Manager, lalu mematikan proses menggunakan End Task. Proses langsung dihentikan, aplikasi tertutup, dan memori dilepaskan.

</div>

---

## Komunikasi Antar Proses pada Sistem Terdistribusi

1. Menggunakan Strawberry untuk GraphQL Server

<div align="center">

<img width="619" height="87" alt="gambar" src="https://github.com/user-attachments/assets/9ac2bce4-0155-4cd0-bb0f-409f6f564bd2" />

Gambar 5 : Tampilan pada saat cek versi Python pada CMD

</div>

<div align="center">

<img width="827" height="260" alt="gambar" src="https://github.com/user-attachments/assets/fae1083c-9e01-4d0a-8abb-c4920d8b4548" />

Gambar 6 : Tampilan pada install uv pada CMD

</div>

<div align="center">

<img width="827" height="126" alt="gambar" src="https://github.com/user-attachments/assets/5b0dc48f-ebba-434c-954c-87ffe73d693b" />

Gambar 7 : Tampilan pada saat create workspace pada CMD

</div>

<div align="center">

<img width="827" height="267" alt="gambar" src="https://github.com/user-attachments/assets/31b745f6-f627-4586-99d1-8544c4de0633" />

Gambar 8 : Tampilan pada saat mengaktifkan environment pada CMD

</div>

<div align="center">

<img width="827" height="800" alt="gambar" src="https://github.com/user-attachments/assets/59d28b00-21f5-41a6-9253-2d7fa8fc44b2" />

Gambar 9 : Tampilan pada saat instalasi Strawberry GraphQL

</div>

<div align="center">

<img width="827" height="841" alt="gambar" src="https://github.com/user-attachments/assets/3093844e-1535-450c-96f5-745f8d545fa9" />

Gambar 10 : Tampilan file schema.py pada folder C/Users/LEOZ/workspace-01

</div>

<div align="center">

<img width="827" height="324" alt="gambar" src="https://github.com/user-attachments/assets/a93425a9-a376-4b93-8bdc-e1719ffae884" />

Gambar 11 : Tampilan pada saat server dijalankan menggunakan CMD

</div>

<div align="center">

<img width="827" height="314" alt="gambar" src="https://github.com/user-attachments/assets/fd95f7db-a6f8-46f6-bc95-a00efa38aa20" />

Gambar 12 : Tampilan pada http://localhost:8000/graphql

</div>

<div align="center">

<img width="827" height="298" alt="gambar" src="https://github.com/user-attachments/assets/8c205802-b583-4927-958c-976d9574d7b8" />

Gambar 13 : Tampilan pada http://localhost:8000/graphql pada saat query dijalankan

</div>

---

## Tugas

Buat client menggunakan bahasa pemrograman bebas (di sini menggunakan Python). Instalasi library requests untuk mengirim query ke server, kemudian menampilkan hasil.
<div align="justify">
  
Pada tugas ini, saya menggunakan bahasa pemrograman Python untuk membuat client yang dapat mengakses GraphQL server. Instalasi library requests digunakan untuk mengirim query ke server, kemudian hasilnya ditampilkan melalui program yang dijalankan.
<div align="justify">

<div align="center">
<img width="827" height="760" alt="gambar" src="https://github.com/user-attachments/assets/19cd37b6-9bf7-4e17-a1d5-2d3991651d6e" />

Gambar 14 : Tampilan pada saat instalasi requests

</div>

<div align="center">

<img width="827" height="801" alt="gambar" src="https://github.com/user-attachments/assets/0abfac76-df22-426e-9212-1e391af6da4b" />

Gambar 15 : Tampilan file client.py pada folder C/Users/LEOZ/workspace-01

</div>

<div align="center">

<img width="827" height="103" alt="gambar" src="https://github.com/user-attachments/assets/2ababc01-2d6b-4b93-99bb-868d02733e0f" />

Gambar 16 : Tampilan pada saat file client.py dijalankan

</div>
