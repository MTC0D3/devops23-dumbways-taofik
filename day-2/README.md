# 📘 DevOps Task - Day 2
## 🔍 Apa itu DevOps ?
DevOps adalah penghubung antara tim development dan operations agar mempercepat proses development hingga rilis ke publik.

Salah satu istilah dalam DevOps adalah continuous, yang berarti segala sesatu yang berkelanjutan. biasanya ada istilah CI/CD yaitu :

- **Continuous integration (CI)** merupakan praktik pada proses pengembangan aplikasi di mana Developer dengan rutin dan teratur memasukkan (commit) atau menggabungkan (merge) setiap perubahan kode (code changes) mereka ke sebuah repositori terpusat (central repository) dan/atau ke mainline trunk (seperti branch master/main), setelah itu proses build dan unit test secara otomatis pun dijalankan.

- **Continuous delivery (CD)** adalah praktik pada proses pengembangan aplikasi di mana perubahan kode (code changes) secara otomatiss dipersiapkan sebelum nantinya dikirim ke lingkungan production.

- **Continuous Deployment (CD)** pada hakikatnya adalah proses yang “serupa tapi tak sama”. Perbedaannya, continuous delivery memiliki proses persetujuan manual (manual approval) sebelum aplikasi di-deploy ke production, sementara continuous deployment tidak memiliki hal tersebut.

## 🖥️ Virtual Machine Setup 
- Pertama kita perlu memiliki dan menjalankan VirtualBox
  
  <img width="954" alt="image" src="https://github.com/user-attachments/assets/4aa8d262-f93b-42de-8842-24a9feab24a4" />

- Kemudian, klik New untuk membuat Virtual Machine baru
- Lalu, beri nama untuk virtual machine dan pilih Os Image yang ingin di install pada VM di sini kita gunakan Ubuntu Server. Janggan lupa centang pada pilihan Skip Unattended Installation agar tidak dibuatkan host otomatis.
  
  <img width="567" alt="image" src="https://github.com/user-attachments/assets/0b1d5a18-6627-4d90-a833-f17d5e1bf1b2" />

- Klik pada hardware lalu konfigurasi untuk memory dan core processor. saya atur memory di 2GB dan processor di 2 core.

  <img width="567" alt="image" src="https://github.com/user-attachments/assets/7e573e17-ff8b-4f0c-9b09-01bcda544d80" />
