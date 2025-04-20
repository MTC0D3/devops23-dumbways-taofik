# 📘 DevOps Task - Day 2

## Diagram Jaringan

![alt text](image.png)

- **Perhitungan Jumlah Subnet**

  Untuk menghitung jumlah subnet, kita bisa menggunakan rumus 2^x (di mana x adalah
  banyaknya angka 1 dalam oktet terakhir di subnet mask).

  192.168.11.0/30
  Subnet mask = 11111111.11111111.11111111.11111100
  Maka 2^6 = 64 Subnet

- **Jumlah host per Subnet**

  Jumlah host per subnet bisa kita ketahui melalui rumus (2^y)-2 (di mana y adalah banyaknya
  angka 0 dalam oktet terakhir di subnet mask).

  Dari subnet mask 11111111.11111111.11111111.11111100, oktet terakhirnya adalah 00. Itu artinya, (2^2)-2 = 4-2 = 2 host per subnet.

  Kenapa harus dikurangi 2?

  Karena ada 2 IP address yang tidak bisa dipakai oleh host, yakni network
  address dan broadcast address.

  Dalam kasus 192.168.11.0/30, network address-nya adalah 192.168.11.0 dan broadcast
  address-nya adalah 192.168.11.3.

  Jadi, rentang IP address yang valid untuk host adalah 192.168.11.1–192.168.11.2.

## Perbedaan SH (Shell) dan BASH (Bourne-Again Shell)

| Aspek            | SH (Shell)                                                                                                   | BASH (Bourne-Again Shell)                                                                                     |
| ---------------- | ------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------- |
| **Definisi**     | SH adalah antarmuka baris perintah dasar yang digunakan untuk menjalankan perintah dan skrip di sistem Unix. | BASH merupakan pengembangan dari Bourne Shell yang menghadirkan fitur tambahan untuk interaksi dan scripting. |
| **Fungsi Utama** | Shell dasar untuk menjalankan perintah dan skrip sederhana.                                                  | Shell modern dengan fitur lengkap untuk scripting dan interaksi.                                              |

## Dokumentasi Dasar Command Linux

### Manajemen Paket

| Perintah           | Fungsi                                                    |
| ------------------ | --------------------------------------------------------- |
| `sudo apt update`  | Memperbarui daftar paket dari repositori.                 |
| `sudo apt upgrade` | Menginstal versi terbaru dari paket yang sudah terpasang. |
| `sudo apt install` | Menginstall paket                                         |
| `sudo apt remove`  | Menghapus paket                                           |

---

### Navigasi Direktori

| Perintah          | Fungsi                                                   |
| ----------------- | -------------------------------------------------------- |
| `pwd`             | Menampilkan path direktori kerja saat ini.               |
| `cd ..`           | Pindah ke direktori induk (parent directory).            |
| `cd /path/to/dir` | Pindah ke direktori yang ditentukan dengan path lengkap. |

---

### Melihat isi direktori

| Perintah | Fungsi                                                                                  |
| -------- | --------------------------------------------------------------------------------------- |
| `ls`     | Menampilkan daftar file dan direktori dalam direktori saat ini.                         |
| `ls -l`  | Menampilkan daftar file dan direktori dengan detail tambahan (permissions, owner, dll). |
| `ls -a`  | Menampilkan semua file, termasuk file tersembunyi (yang dimulai dengan titik).          |
| `ls -h`  | Menampilkan ukuran file dalam format yang lebih mudah dibaca (misal: KB, MB).           |

---

### Manajemen File & Folder

| Perintah              | Fungsi                               |
| --------------------- | ------------------------------------ |
| `touch file.txt`      | Membuat file kosong                  |
| `mkdir folder`        | Membuat folder baru                  |
| `cp file.txt folder/` | Menyalin file ke folder              |
| `mv file.txt folder/` | Memindahkan atau mengganti nama file |
| `rm file.txt`         | Menghapus file                       |
| `rm -r folder/`       | Menghapus folder dan isinya          |

---

### Pengguna & Hak Akses

| Perintah                 | Fungsi                                                                                     |
| ------------------------ | ------------------------------------------------------------------------------------------ |
| `whoami`                 | Menampilkan nama user yang sedang aktif.                                                   |
| `chmod ugoa+rwx file.sh` | Memberikan hak baca, tulis, dan eksekusi kepada semua pengguna (user, group, others, all). |
| `chmod 755 file.sh`      | Mengatur permission file secara numerik.                                                   |
| `ls -l`                  | Menampilkan file + permission                                                              |
| `chown user:group file`  | Mengubah pemilik dan grup dari suatu file.                                                 |

---

- Memperbarui daftar paket dari repositori.

![alt text](image-1.png)

- Menginstal versi terbaru dari paket yang sudah terpasang.

![alt text](image-2.png)

- Membuat direktori baru

![alt text](image-3.png)

- Membuat file kosong

![alt text](image-4.png)

- Menampilkan daftar file dan direktori dalam direktori saat ini.

![alt text](image-5.png)

- Menampilkan daftar file dan direktori dengan detail tambahan (permissions, owner, dll) serta hidden file dan direktori.

![alt text](image-6.png)

- Pindah ke direktori latihan

![alt text](image-7.png)

- Pindah ke direktori induk (parent directory).

![alt text](image-8.png)

- Menyalin file

![alt text](image-9.png)

- Memindahkan file ke direktori latihan

![alt text](image-10.png)

- Mengganti nama file

![alt text](image-11.png)

- Menampilkan string atau teks ke output

![alt text](image-12.png)

- Menampilkan string atau teks ke output file

![alt text](image-13.png)

- Melihat isi file

![alt text](image-14.png)

- Mencari file dan direktori

![alt text](image-15.png)

- Mencari file dengan spesifik

![alt text](image-16.png)

- Mencari teks dalam file

![alt text](image-17.png)

- Membuka teks editor bawaan linux

![alt text](image-18.png)

- Menacri teks di semua file

![alt text](image-19.png)

- Merubah file permission

![alt text](image-20.png)

- Mengubah pemilik dan grup dari suatu file.

![alt text](image-21.png)

- Melihat command yang sudah digunakan

![alt text](image-22.png)

- Berpindah ke root user

![alt text](image-23.png)
