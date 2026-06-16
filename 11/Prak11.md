# Modul 11

## Tugas 1

### Cara Kerja Blockchain

<div align="center">

<img width="754" height="401" alt="gambar" src="https://github.com/user-attachments/assets/8bad5d2e-2d14-452b-93e2-2f8c69c2a1ea" />

**Gambar 1. Tampilan Program hash_demo.py**

</div>

<div align="center">

<img width="975" height="98" alt="gambar" src="https://github.com/user-attachments/assets/c0f65593-521f-411b-9bd1-6407fced60ea" />

**Gambar 2. Tampilan Output Program hash_demo.py**

</div>

### Kesimpulan:

<div align="justify">

Dari program tersebut dapat disimpulkan bahwa SHA-256 mengubah sebuah teks menjadi deretan karakter yang tampak acak dan unik. Teks "UTDI" dan "Fakultas Teknologi Informasi" menghasilkan hash yang berbeda karena isi teksnya berbeda. Hal ini menunjukkan bahwa hash dapat digunakan sebagai identitas digital suatu data. Jika isi teks diubah sedikit saja, hash yang dihasilkan juga akan berubah secara signifikan. Oleh karena itu, SHA-256 sering digunakan untuk membantu menjaga keaslian dan keamanan data pada berbagai sistem, termasuk blockchain.

</div>

---

## Tugas 2

### Source Code

<div align="center">

<img width="975" height="835" alt="gambar" src="https://github.com/user-attachments/assets/263b48d2-c832-4e7d-a13b-235c57fb5428" />

**Gambar 3. Tampilan Program CoreBlokchain.py**

</div>

<div align="center">

<img width="975" height="575" alt="gambar" src="https://github.com/user-attachments/assets/de14625f-f2a4-4054-889f-5b48156c80c9" />

**Gambar 4. Tampilan Program UtdiBlokchain.py**

</div>

<div align="center">

<img width="975" height="438" alt="gambar" src="https://github.com/user-attachments/assets/29a36b2c-9548-49b1-989e-6849de8dadce" />

**Gambar 5. Tampilan Program blokchain_demo_01.py**

</div>

<div align="center">

<img width="975" height="444" alt="gambar" src="https://github.com/user-attachments/assets/0bed89b0-a11d-4023-8650-c46353ca3883" />

**Gambar 6. Tampilan Demo**

</div>

### Penjelasan Source Code :

<div align="justify">

#### Block.py

Pada file Block.py, import hashlib digunakan untuk membuat hash atau kode unik yang berfungsi mengamankan data dalam blok. import time digunakan untuk mencatat waktu pembuatan blok. Method __init__() berfungsi membuat blok baru dan menyimpan informasi seperti nomor blok, waktu, data transaksi, hash sebelumnya, dan nonce. Nilai nonce diatur menjadi 0 sebagai nilai awal. Setelah itu, program langsung membuat hash melalui self.hash = self.count_hash(). Method count_hash() bertugas mengubah seluruh isi blok menjadi hash unik menggunakan algoritma SHA-256.

#### UtdiBlockchain.py

Pada file UtdiBlockchain.py, self.chain = [] digunakan untuk membuat tempat penyimpanan seluruh blok dalam blockchain. Method init_genesis_block() berfungsi membuat blok pertama atau Genesis Block. Method add_block() digunakan untuk menambahkan blok baru sekaligus menghubungkannya dengan blok sebelumnya menggunakan hash. Setelah itu, self.chain.append(new_block) digunakan untuk memasukkan blok baru ke dalam rantai blockchain.

#### blockchain_demo_01.py

Pada file blockchain_demo_01.py, UtdiBlockchain.UtdiBlockchain() digunakan untuk membuat blockchain baru yang otomatis memiliki Genesis Block. Method add_block(...) digunakan untuk menambahkan data transaksi ke dalam blockchain. Selanjutnya, perulangan for block in blockchain.chain digunakan untuk menampilkan isi setiap blok, seperti nomor blok, data transaksi, hash sebelumnya, dan hash saat ini.

</div>

---

## Pengenalan Blockchain dan Ethereum

<div align="center">
  
<img width="975" height="701" alt="gambar" src="https://github.com/user-attachments/assets/28482b07-a5b0-47dd-be42-e03a042c710e" />

**Gambar 7. Tampilan Wallet MetaMask**

Simpan MetaMask untuk digunakan di praktikum Smart Contracts berikutnya

</div>

---

## Tugas 3

### Soal 1

<div align="justify">

#### a. DApps (Decentralized Applications)

DApps adalah aplikasi yang dibuat menggunakan teknologi blockchain. DApps berjalan di jaringan yang tersebar sehingga tidak dikendalikan oleh satu pihak saja. Karena itu, data dan proses di dalamnya lebih transparan dan sulit dimanipulasi.

#### b. NFT (Non-Fungible Token)

NFT merupakan aset digital yang memiliki identitas unik di blockchain. Setiap NFT berbeda dan tidak bisa disamakan dengan NFT lainnya.

#### c. DEX (Decentralized Exchange)

DEX adalah platform untuk menukar aset kripto secara langsung antar pengguna tanpa bantuan pihak ketiga. Semua transaksi dilakukan melalui smart contract sehingga pengguna tetap memegang kendali atas aset yang dimilikinya selama proses transaksi berlangsung.

#### d. Tokenization

Tokenization adalah proses mengubah suatu aset menjadi bentuk token digital yang dicatat di blockchain.

#### e. Stablecoins

Stablecoins adalah jenis mata uang kripto yang dirancang agar nilainya relatif stabil. Nilainya biasanya mengikuti aset tertentu, seperti dolar Amerika Serikat.

</div>

---

### Soal 2

<div align="justify">

saya akan menggunakan beberapa peranti untuk membangun DApps yakni Next.js (antarmuka), RainbowKit & Wagmi (koneksi dompet), dan Hardhat atau Foundry (pengembangan smart contract) . Alasannya, Next.js memastikan aplikasi web memuat data blockchain dengan cepat dengan fitur server side rendering, RainbowKit dan Wagmi digunakan untuk interaksi dompet digital seperti MetaMask, sementara Hardhat atau Foundry digunakan untuk simulasi lokal yang menguji smart contract secara gratis dan aman sebelum diterbitkan ke jaringan asli.

</div>
