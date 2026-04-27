# Praktikum Sistem Terdistribusi dan Terdesentralisasi/04

**Nama:** Hafidza Nur Afifah  
**NIM:** 235410012  
**Kelas:** Informatika 1  

## 4.1 Streaming Replication PostgreSQL

### 4.1.1 Prasyarat
<div align="center">
<img width="975" alt="Prasyarat" src="https://github.com/user-attachments/assets/4b43707a-4b93-4fde-87d0-352490413113"/>
<br>
<b>Gambar 1. Tampilan Prasyarat</b>
</div>

<br><br>

### 4.1.2 Struktur Direktori dan File
<div align="center">
<img width="975" alt="Struktur Folder" src="https://github.com/user-attachments/assets/cf7ff0d4-3518-44bf-9a41-dcaf8624726e"/>
<br>
<b>Gambar 2. Tampilan Struktur Folder</b>
</div>

<br><br>

<div align="center">
<img width="975" alt="Docker Compose" src="https://github.com/user-attachments/assets/47d26700-cf36-4860-8808-11d7e2feed9e"/>
<br>
<b>Gambar 3. Tampilan File docker-compose.yaml</b>
</div>

<br><br>

<div align="center">
<img width="975" alt="env.ps1" src="https://github.com/user-attachments/assets/b4c1e105-5aba-4fc4-856c-3af07504e60d"/>
<br>
<b>Gambar 4. Tampilan File env.ps1</b>
</div>

### 4.1.3 Menjalankan Docker Compose
<div align="center">
<img width="975" height="472" alt="gambar" src="https://github.com/user-attachments/assets/18a2ae99-6ca4-40e5-aa4f-1ffcd4b8c5de" />
<br>
<b>Gambar 5. Tampilan Docker Compose yang sudah running/b>
</div>

### 4.1.4 Pengujian Replikasi (Postgres)
<div align="center">
<img width="975" height="147" alt="gambar" src="https://github.com/user-attachments/assets/b34ccbf5-4377-4f3b-a8e1-b09dd2650665" />
<br>
<b>Gambar 6. Tampilan pengujian replikasi/b>
</div>

<div align="center">
<img width="975" height="279" alt="gambar" src="https://github.com/user-attachments/assets/26c81823-46a0-41bf-a91f-147aa82aac32" />
<br>
<b>Gambar 7. Tampilan pada saat pengujian replikasi terhubung/b>
</div>

<div align="center">
<img width="845" height="419" alt="gambar" src="https://github.com/user-attachments/assets/caed3602-3d71-45c6-b9e7-65498ec166d1" />
<br>
<b>Gambar 8. Tampilan pada saat mencoba create dan insert pada Primary/b>
</div>

<div align="center">
<img width="975" height="411" alt="gambar" src="https://github.com/user-attachments/assets/7878ef1a-65bf-462a-8095-44e602d0e3f8" />
<br>
<b>Gambar 9. Tampilan pada saat cek status replikasi/b>
</div>

<div align="center">
<img width="975" height="411" alt="gambar" src="https://github.com/user-attachments/assets/8c0c6cfb-411c-4aab-b609-58d2727664b3" />
<br>
<b>Gambar 10. Tampilan pada saat cek data hasil replikasi/b>
</div>

### 4.1.5 High Availability
<div align="center">
<img width="975" height="240" alt="gambar" src="https://github.com/user-attachments/assets/1dfcd2c9-2fc9-424b-8fdb-a9efb7ffd327" />
<br>
<b>Gambar 11. Tampilan pada saat Primary di non aktifkan/b>
</div>

<div align="center">
<img width="975" height="441" alt="gambar" src="https://github.com/user-attachments/assets/dc89e77a-75e0-45be-b1bb-999d0ed7a188" />
<br>
<b>Gambar 12. Tampilan pada saat Primary di non aktifkan/b>
</div>

### 4.2.5 Eksekusi Perintah SQL
<div align="center">
<img width="975" height="350" alt="gambar" src="https://github.com/user-attachments/assets/325409ba-d6ab-461e-bff2-67288249a8e3" />
<br>
<div align="center">
<img width="975" height="394" alt="gambar" src="https://github.com/user-attachments/assets/a2fd5451-bf56-4425-923d-648b7b7ef30d" />
<br>
<b>Gambar 13. Tampilan koneksi ke http://localhost:10300/b>
</div>

<div align="center">
<img width="975" height="201" alt="gambar" src="https://github.com/user-attachments/assets/00710362-4ad0-476b-aeab-a23489ac71bc" />
<br>
<b>Gambar 14. Tampilan pada saat file schema.sql belum running/b>
</div>

<div align="center">
<img width="975" height="232" alt="gambar" src="https://github.com/user-attachments/assets/bff893dc-5916-4e1b-b5ca-d563c3f20cd7" />
<br>
<b>Gambar 15. Tampilan pada saat file schema.sql sudah running/b>
</div>
