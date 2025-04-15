# 📘 DevOps Task - Day 2
## 🔍 Apa itu DevOps ?
DevOps adalah penghubung antara tim development dan operations agar mempercepat proses development hingga rilis ke publik.

Salah satu istilah dalam DevOps adalah continuous, yang berarti segala sesatu yang berkelanjutan. biasanya ada istilah CI/CD yaitu :

- **Continuous integration (CI)** merupakan praktik pada proses pengembangan aplikasi di mana Developer dengan rutin dan teratur memasukkan (commit) atau menggabungkan (merge) setiap perubahan kode (code changes) mereka ke sebuah repositori terpusat (central repository) dan/atau ke mainline trunk (seperti branch master/main), setelah itu proses build dan unit test secara otomatis pun dijalankan.

- **Continuous delivery (CD)** adalah praktik pada proses pengembangan aplikasi di mana perubahan kode (code changes) secara otomatiss dipersiapkan sebelum nantinya dikirim ke lingkungan production.

- **Continuous Deployment (CD)** pada hakikatnya adalah proses yang “serupa tapi tak sama”. Perbedaannya, continuous delivery memiliki proses persetujuan manual (manual approval) sebelum aplikasi di-deploy ke production, sementara continuous deployment tidak memiliki hal tersebut.

## 🖥️ Virtual Machine Setup 
- Pertama kita perlu memiliki dan menjalankan VirtualBox.
  
  <img width="954" alt="image" src="https://github.com/user-attachments/assets/4aa8d262-f93b-42de-8842-24a9feab24a4" />

- Kemudian, klik New untuk membuat Virtual Machine baru.
- Lalu, beri nama untuk virtual machine dan pilih Os Image yang ingin di install pada VM di sini kita gunakan Ubuntu Server. Janggan lupa centang pada pilihan Skip Unattended Installation agar tidak dibuatkan host otomatis.
  
  <img width="567" alt="image" src="https://github.com/user-attachments/assets/0b1d5a18-6627-4d90-a833-f17d5e1bf1b2" />

- Klik pada Hardware lalu konfigurasi untuk memory dan core processor. saya atur memory di 2GB dan processor di 2 core.

  <img width="567" alt="image" src="https://github.com/user-attachments/assets/7e573e17-ff8b-4f0c-9b09-01bcda544d80" />

- Klik pada Hard Disk lalu konfigurasi untuk membuat Virtual Hard Disk. saya atur di 10GB.

  <img width="569" alt="image" src="https://github.com/user-attachments/assets/63be9ef7-c9ad-4964-8019-4c4fdea75627" />

- Lalu, klik Finish.
- Selanjutnya, klik start pada VM yang sudah kita buat untuk melanjutkan ke proses installasi Ubuntu Server.

   <img width="959" alt="image" src="https://github.com/user-attachments/assets/db02400c-29b1-49ef-8c83-10002c60da5c" />

- Pilih Try or Install Ubuntu Server.

   <img width="362" alt="image" src="https://github.com/user-attachments/assets/9eb80b95-4163-4e02-9ce7-5813b8648d1d" />

- Pilih bahasa yang ingin digunakan.

  <img width="404" alt="image" src="https://github.com/user-attachments/assets/1e60e564-1868-4fbd-95ff-fbfa47b5750e" />

- Pilih Continue without updating.

  <img width="402" alt="image" src="https://github.com/user-attachments/assets/ff96017a-7ab7-4d77-b95a-31de219ca278" />

- Langsung tekan done jika tidak ada perubahan pada keyboard configuration.
  
  <img width="398" alt="image" src="https://github.com/user-attachments/assets/285c5016-a9b1-4e1f-a646-f71e5f0bc456" />

- Lalu pilih ubuntu server untuk tipe installasi.

  <img width="400" alt="image" src="https://github.com/user-attachments/assets/a5ebe7c5-e844-4243-8383-08e1c0f6d25c" />

- Selanjutnya, kita masuk pada proses network configuration. Kita pilih edit IPV4 dan gunakan metode manual.

  <img width="402" alt="image" src="https://github.com/user-attachments/assets/8ba29bde-587d-4ff2-8772-8e271369fb55" />

  <img width="400" alt="image" src="https://github.com/user-attachments/assets/7a5c38e4-d0ad-4ee8-bcc8-41c8ae2f24a0" />

- Kemudian, buka cmd dan ketikan perintah `ipconfig`. cari jaringan internet yang terhubung ke perangkat kita, disini saya menggunakan wifi.

  <img width="653" alt="image" src="https://github.com/user-attachments/assets/2d7be215-5b4d-4f64-8365-1ecbd759d8d3" />

- Lalu, masukan IPv4 Addres ke network configuration seperti berikut. Kemudian, klik save.

  <img width="403" alt="image" src="https://github.com/user-attachments/assets/492ef31e-c7d9-44c8-8c0b-036b24101b84" />

- Kemudian, langsung pilih done pada **Proxy Configuration**.
- lalu, klik done pada **Ubuntu Archive Mirror Configuration**.
- Pada **Storage Configuration**, kita pilih custom storage layout, lalu done.

  <img width="401" alt="image" src="https://github.com/user-attachments/assets/4d8d975e-ad35-4901-8c5b-4f206f49d6c6" />

- Lalu, kita diarahkan ke proses **Storage Configuration ** lebih lanjut.
- Kemudian, kita pilih free space dan tambah GPT partition.

  <img width="399" alt="image" src="https://github.com/user-attachments/assets/db1a2e7b-5ceb-4e6e-a9ab-dd29a3ba7dbf" />

- Lalu, buat partisi untuk sekitar 7GB dengan format ext4 yang dapat digunakan untuk bermacam-macam kebutuhan contohnya installasi aplikasi. Lalu, klik create.

  <img width="400" alt="image" src="https://github.com/user-attachments/assets/79314003-3e31-497f-aeb9-9b68be2336dd" />

- Kemudian, sisa kapasitas kita akan gunakan untuk swap atau virtual memory. lalu pilih create.

  <img width="402" alt="image" src="https://github.com/user-attachments/assets/afb8c199-39e2-483c-a3e8-88a430f4ca81" />

  

  

  
  



