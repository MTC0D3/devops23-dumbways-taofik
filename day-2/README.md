# 📘 DevOps Task - Day 2

## Diagram Jaringan

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
