# Praktikum Sistem Terdistribusi dan Terdesentralisasi/12

**Nama : Hafidza Nur Afifah**  
**NIM : 235410012**  
**Kelas : Informatika 1**

### Modul 14

## 1. Pengantar

Smart contract merupakan program yang berjalan secara otomatis pada jaringan blockchain berdasarkan aturan yang telah ditentukan. Program ini memungkinkan proses transaksi atau aktivitas tertentu dapat dilakukan tanpa memerlukan pihak ketiga.

Pada modul ini dilakukan implementasi smart contract menggunakan blockchain **Solana** dengan bahasa pemrograman **Rust**. Solana menggunakan Rust sebagai bahasa utama dalam pengembangan smart contract karena memiliki performa tinggi, keamanan memori yang baik, serta mampu mendukung proses eksekusi program secara efisien pada jaringan blockchain.

Praktikum ini bertujuan untuk memahami konsep dasar pembuatan smart contract, proses kompilasi, pengujian, hingga deployment program pada jaringan Solana.

---

## 2. Smart Contract Solana Native Rust

### 2.1 Membuat Project Rust

Langkah pertama adalah membuat project baru menggunakan Cargo sebagai package manager bawaan Rust. Project dibuat menggunakan perintah berikut:

```bash
cargo new hello_solana --lib
cd hello_solana
cargo add solana-program
```

Perintah tersebut digunakan untuk membuat project library Rust baru bernama `hello_solana` dan menambahkan library `solana-program` agar program dapat menggunakan fitur yang disediakan oleh blockchain Solana.

<p align="center">
<img width="972" height="532" alt="gambar" src="https://github.com/user-attachments/assets/5815cd24-cd57-4df2-86a5-c04e247e324f" />
</p>

<p align="center">
  <b>Gambar 1.</b> Pembuatan project baru menggunakan Cargo.
</p>

---

### 2.2 Konfigurasi Cargo.toml

Setelah project berhasil dibuat, dilakukan konfigurasi pada file `Cargo.toml`. Konfigurasi ini bertujuan agar project dapat dikompilasi menjadi library yang dapat digunakan oleh Solana.

Tambahkan konfigurasi berikut:

```toml
[lib]
crate-type = ["cdylib", "lib"]
```

<p align="center">
<img width="676" height="410" alt="gambar" src="https://github.com/user-attachments/assets/9ea750fd-453e-4eb0-8803-0e4bc0757c31" />
</p>

<p align="center">
  <b>Gambar 2.</b> Konfigurasi file Cargo.toml.
</p>

Konfigurasi `crate-type` digunakan agar hasil kompilasi Rust dapat menghasilkan file library dengan format yang sesuai untuk deployment smart contract pada jaringan Solana.

---

### 2.3 Membuat Source Code Smart Contract

File utama smart contract berada pada `src/lib.rs`. Source code yang digunakan merupakan program yang menampilkan pesan **"Hello, world!"** ketika smart contract dijalankan.

<p align="center">
<img width="954" height="335" alt="gambar" src="https://github.com/user-attachments/assets/0c04df0c-bcbc-4352-bb61-c6dff726a23b" />
</p>

<p align="center">
  <b>Gambar 3.</b> Source code smart contract menggunakan Rust.
</p>

Pada source code tersebut terdapat fungsi `process_instruction()` yang berfungsi sebagai titik awal eksekusi program. Fungsi tersebut akan dipanggil ketika smart contract menerima instruksi dari jaringan Solana.

`entrypoint!` digunakan untuk menentukan fungsi utama yang akan dijalankan oleh Solana. Sedangkan fungsi `msg!` digunakan untuk menampilkan pesan pada log ketika program berhasil dieksekusi.

---

### 2.4 Build Smart Contract

Setelah source code selesai dibuat, tahap berikutnya adalah melakukan proses kompilasi menggunakan perintah:

```bash
cargo build-sbf
```

<p align="center">
<img width="938" height="239" alt="gambar" src="https://github.com/user-attachments/assets/c9e1e026-56da-4e3a-bc4c-6f93bf20f6c4" />
</p>
<p align="center">
<img width="748" height="992" alt="gambar" src="https://github.com/user-attachments/assets/4cc18b59-a2ec-41c3-baab-987aa724187d" />
</p>
<p align="center">
<img width="975" height="365" alt="gambar" src="https://github.com/user-attachments/assets/fbeff969-8ae1-4703-9406-9f00a384e85c" />
</p>


<p align="center">
  <b>Gambar 4.</b> Proses build smart contract menggunakan `cargo build-sbf`.
</p>

Perintah `cargo build-sbf` digunakan untuk mengubah source code Rust menjadi file yang dapat dijalankan oleh jaringan Solana. Pada proses ini mungkin muncul beberapa pesan warning, namun warning tersebut tidak memengaruhi proses kompilasi maupun hasil deployment.

Hasil dari proses build dapat dibuka pada folder `target/deploy`.

---

### 2.5 Hasil Build

<p align="center">
<img width="706" height="169" alt="gambar" src="https://github.com/user-attachments/assets/2c9cddaf-4581-46e6-82af-38ddee6ddff1" />
</p>

<p align="center">
  <b>Gambar 5.</b> Hasil file build smart contract.
</p>

Dari proses build dihasilkan dua file utama, yaitu:

1. **hello_solana.so**
   File ini merupakan hasil kompilasi smart contract yang akan digunakan saat proses deployment.

2. **hello_solana-keypair.json**
   File ini berisi pasangan kunci yang digunakan untuk menghasilkan Program ID dari smart contract.

---

### 2.6 Pengujian Smart Contract

Pengujian dilakukan menggunakan library **LiteSVM** untuk memastikan smart contract dapat dijalankan dengan baik.

Perintah pengujian:

```bash
cargo test -- --show-output
```

<p align="center">
<img width="975" height="730" alt="gambar" src="https://github.com/user-attachments/assets/954ceaa0-5130-4b00-aba7-6a9be127f7e4" />
</p>

<p align="center">
  <b>Gambar 6.</b> Hasil pengujian smart contract menggunakan LiteSVM.
</p>

Berdasarkan hasil pengujian, program berhasil dijalankan dengan status **passed**. Hal tersebut menunjukkan bahwa file smart contract berhasil dikompilasi dan dapat dieksekusi dengan baik.

---

### 2.7 Deployment Smart Contract

Sebelum melakukan deployment, jaringan Solana diubah menjadi jaringan lokal menggunakan perintah:

```bash
solana config set -ul
```

Kemudian validator lokal dijalankan dan smart contract di-deploy menggunakan:

```bash
solana program deploy target/deploy/hello_solana.so
```

<p align="center">
<img width="867" height="223" alt="gambar" src="https://github.com/user-attachments/assets/2a16fbda-0a8a-4f6a-94ba-c0cc6b4a3f33" />
</p>

<p align="center">
<img width="975" height="516" alt="gambar" src="https://github.com/user-attachments/assets/e4e0e6b7-94c8-4d99-8ead-fa7523b55fdf" />
</p>

<p align="center">
<img width="975" height="482" alt="gambar" src="https://github.com/user-attachments/assets/04eeae2f-332f-49c5-a93e-c2509b7ba4bd" />
</p>

<p align="center">
  <b>Gambar 7.</b> Proses deployment smart contract ke jaringan lokal Solana.
</p>

Setelah proses deployment berhasil, Solana menghasilkan sebuah **Program ID** yang menjadi identitas unik dari smart contract tersebut pada blockchain.

Program ID tersebut dapat digunakan untuk melihat informasi program melalui **Solana Explorer**.

<p align="center">
<img width="924" height="64" alt="gambar" src="https://github.com/user-attachments/assets/6ee4099e-a4d7-494d-9be0-f57ab5b9d554" />
</p>

<p align="center">
  <b>Gambar 8.</b> Tampilan ID Program
</p>

---

## 3. Smart Contract Solana Menggunakan Anchor Framework

Selain menggunakan metode native Rust, pengembangan smart contract Solana juga dapat dilakukan menggunakan framework **Anchor**.

Anchor merupakan framework yang membantu proses pembuatan smart contract menjadi lebih mudah dengan menyediakan struktur project, library, serta fitur testing yang lebih sederhana.

---

### 3.1 Membuat Project Anchor

<p align="center">
<img width="975" height="906" alt="gambar" src="https://github.com/user-attachments/assets/f9cc51ca-9e09-4863-a81d-fa18daf00100" />
</p>

<p align="center">
<img width="900" height="876" alt="gambar" src="https://github.com/user-attachments/assets/9895d7ed-36da-4fbd-9fe7-93a3d3f8b88a" />
</p>

<p align="center">
<img width="653" height="231" alt="gambar" src="https://github.com/user-attachments/assets/9e63cda9-da18-4395-8461-69028e55670b" />
</p>

<p align="center">
  <b>Gambar 8.</b> Pembuatan project menggunakan Anchor Framework.
</p>

Project Anchor dibuat untuk menyediakan struktur dasar pengembangan smart contract. Framework ini membantu developer dalam mengatur program, melakukan build, testing, serta deployment ke jaringan Solana.

---

### 3.2 Build dan Testing Program Anchor

Proses build dilakukan untuk menghasilkan file program yang siap digunakan.

<p align="center">
<img width="975" height="505" alt="gambar" src="https://github.com/user-attachments/assets/9a1ad36a-b307-4f49-8d66-1d18d62d40c1" />
</p>

<p align="center">
  <b>Gambar 9.</b> Hasil build program menggunakan Anchor.
</p>

---

### 3.3 Deployment ke Devnet

Deployment dilakukan menggunakan jaringan **Devnet Solana**.

Perintah deployment:

```bash
anchor deploy
```

<p align="center">
<img width="975" height="354" alt="gambar" src="https://github.com/user-attachments/assets/89368315-655b-42fe-92bd-789244a21e5b" />
</p>

<p align="center">
  <b>Gambar 11.</b> Deployment smart contract ke jaringan Devnet.
</p>

Setelah deployment berhasil, program akan memiliki **Program ID** yang dapat digunakan untuk melihat informasi smart contract melalui **Solana Explorer Devnet**. Tetapi pada praktikum ini deploy gagal, dikarenakan saldo SOL 0.

---

## 4. Smart Contract Ethereum Menggunakan Hardhat

### 4.1 Deskripsi

Repository ini dibuat untuk memenuhi tugas praktikum **Smart Contract pada Blockchain** dengan mereplikasi tahapan pengembangan smart contract menggunakan blockchain **Ethereum** sebagai alternatif dari implementasi Solana pada modul praktikum.

Pengembangan smart contract dilakukan menggunakan **Hardhat** sebagai framework pengembangan Ethereum dan bahasa pemrograman **Solidity**. Smart contract yang dibuat merupakan contoh sederhana berupa kontrak **HelloWorld** yang menyimpan sebuah pesan (`message`) dan menyediakan fungsi untuk memperbarui isi pesan tersebut.

---

### Struktur Repository

```text
tugas_ethereum/
│
├── contracts/
│   └── HelloWorld.sol
│
├── scripts/
├── hardhat.config.ts
├── package.json
├── package-lock.json
├── tsconfig.json
├── README.md
└── screenshots/
```

---

### 4.2 Membuat Proyek Hardhat

Langkah pertama yakni membuat proyek baru menggunakan Hardhat.

```bash
mkdir tugas_ethereum
cd tugas_ethereum
npm init -y
npm install --save-dev hardhat
npx hardhat --init
```

Pada proses inisialisasi dipilih template **Minimal Hardhat Project** sehingga dihasilkan struktur proyek dasar yang siap digunakan untuk pengembangan smart contract.

<p align="center">
<img width="975" height="549" alt="gambar" src="https://github.com/user-attachments/assets/abb183b8-cffe-4ab7-97f3-6ede2f96888c" />
</p>

<p align="center">
<b>Gambar 12.</b> Proses inisialisasi proyek Hardhat.
</p>

Gambar 12 memperlihatkan proses pembuatan proyek menggunakan Hardhat. Setelah proses inisialisasi selesai, Hardhat secara otomatis menghasilkan beberapa file konfigurasi seperti `hardhat.config.ts`, `package.json`, dan direktori yang akan digunakan selama proses pengembangan.

---

### 4.3 Membuat Smart Contract

Setelah proyek berhasil dibuat, langkah selanjutnya adalah membuat direktori `contracts` dan menambahkan file **HelloWorld.sol**.

```text
contracts/
└── HelloWorld.sol
```

Isi smart contract adalah sebagai berikut.

<p align="center">
<img width="975" height="564" alt="gambar" src="https://github.com/user-attachments/assets/b8f8296a-34d2-41db-b070-ac1d1de7691d" />

</p>

<p align="center">
<b>Gambar 13.</b> isi file HelloWorld.sol
</p>

Gambar 13 menunjukkan proses penulisan smart contract menggunakan bahasa Solidity. Smart contract tersebut memiliki sebuah variabel bertipe string bernama `message` yang digunakan untuk menyimpan pesan, serta fungsi `setMessage()` yang berfungsi memperbarui isi pesan tersebut.

---

### 4.4 Konfigurasi Hardhat

Hardhat memerlukan file konfigurasi agar mengetahui versi compiler Solidity yang digunakan.

<p align="center">
<img width="559" height="153" alt="gambar" src="https://github.com/user-attachments/assets/95e1088a-f2d9-41f7-8b70-b8d0e43ff9ed" />
</p>

<p align="center">
<b>Gambar 14.</b> Tampilan file hardhat.config.ts
</p>

Gambar 14 menunjukkan konfigurasi Hardhat dengan compiler Solidity versi **0.8.28**. Penentuan versi compiler bertujuan agar proses kompilasi menggunakan versi Solidity yang sesuai dengan source code yang telah dibuat.

---

### 4.5 Kompilasi Smart Contract

Setelah smart contract selesai dibuat, langkah berikutnya adalah melakukan kompilasi menggunakan Hardhat.

```bash
npx hardhat compile --force
```

Hasil kompilasi yang berhasil akan menghasilkan pesan:

```text
Compiled 1 Solidity file with solc 0.8.28 (evm target: cancun)
```

<p align="center">
<img width="929" height="191" alt="gambar" src="https://github.com/user-attachments/assets/cb7dbc5c-6c33-40d1-9dc2-9df7ee82a3e6" />
</p>

<p align="center">
<b>Gambar 15.</b> Hasil kompilasi smart contract.
</p>

Gambar 15 menunjukkan bahwa source code dapat diterjemahkan menjadi bytecode Ethereum.

---

### Kesimpulan

Implementasi smart contract menggunakan Ethereum berhasil dilakukan menggunakan framework Hardhat. Tahapan yang dilakukan meliputi pembuatan proyek, penulisan smart contract menggunakan Solidity, konfigurasi compiler, serta proses kompilasi. Hasil kompilasi menunjukkan bahwa smart contract berhasil dibangun.
