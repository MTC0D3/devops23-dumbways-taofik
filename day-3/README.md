# 📘 DevOps Task - Day 3

- Akses server menggunakan terminal (Windows Terminal/PuTTY/etc.)
- Konfigurasi ssh kalian agar bisa di akses _hanya menggunakan publickey_ (password dimatikan)
- Buat step by step penggunaan text manipulation! (grep, sed, cat, echo)
- Nyalakan ufw dengan memberikan akses untuk port 22, 80, 443, 3000, 5000 dan 6969!

## 💻 Akses server menggunakan terminal

### 1. Melihat Ip Adrress Server

- Gunakan perintah berikut untuk melihat ip address server

```
ip a
```

<img src="image.png" width="700" height="400" />

### 2. Akses lewat Terminal device pribadi

- Disini saya menggunakan bash atau terminal bawaan git kemudian jalankan perintah berikut

```
ssh username@ip_address
```

- Jika terjadi Connection refused install terlebih dahulu openshh di server nya dengan perintah berikut

```
sudo apt install openssh-server
```

<img src="image-2.png" width="700" height="400" />

### 3. Cek apakah SSH sudah berjalan

- Gunakan perintah berikut untuk melihat status SSH

```
sudo systemctl status ssh
```

<img src="image-3.png" width="700" height="400" />

### 4. Akses kembali server

- Jika sudah melakukan installasi dan pengecekan status silahkan akses kembali server dengan perintah berikut

```
ssh username@ip_address
```

<img src="image-1.png" width="700" height="400" />

**Catatan** : username dan password yang digunakan harus sama dengan yang ada di server

## 🔐 Konfigurasi Akses SSH Menggunakan Public Key

### 1. Generate Public Key dan Private Key

- Untuk membuat Public Key dan Private Key gunakan perintah berikut

```
ssh-keygen
```

<img src="image-6.png" width="700" height="400" />

### 2. Buka Folder "C:\Users<nama_user>.ssh"

- Terdapat 2 key yaitu Public key (ekstensi .pub) dan Private Key. Private Key harus disimpan baik-baik dan harus dirahasiakan.

<img src="image-7.png" width="700" height="400" />

### 3. Buka file Public Key dan salin isinya

- Saya menggunakan notepad untuk melihat dan menyalin isi file nya

<img src="image-4.png" width="700" height="400" />

### 4. Akses kembali ke server dengan Terminal

- Kemudian, buka file "authorized_keys" di direktori ~/.ssh lalu gunakan perintah berikut

```
cd .ssh/
ls
sudo nano authorized_keys
```

<img src="image-5.png" width="700" height="400" />

### 5. Paste Public Key pada file "authorized_keys"

- Silahkan paste Public Key pada file "authorized_keys" di server Ubuntu dan simpan

<img src="image-8.png" width="700" height="400" />

### 6. Uji coba koneksi ke Server

- Lakukan pengujian koneksi ke server dengan SSH menggunakan Public Key Terminal dengan perintah berikut

```
ssh -i ~/.ssh/taofiks_key taofiks@192.168.100.104
```

<img src="image-9.png" width="700" height="400" />

### 7. konfigurasi login hanya dengan Public Key

- Lakukan konfigurasi pada file konfigurasi SSH

```
sudo nano /etc/ssh/sshd_config
```

<img src="image-10.png" width="700" height="400" />

- Atur parameter sebagai berikut. Setelah selesai simpan file tersebut.

```
PubkeyAuthentication yes
PasswordAuthentication no
```

<img src="image-12.png" width="700" height="400" />

**Catatan :**
PubkeyAuthentication = mengizinkan autentikasi via SSH key.
PasswordAuthentication = menonaktifkan login via password.

- Restart SSH service pada terminal

```
sudo systemctl restart sshd
```

- Disconnect SSH dengan mengetikkan "exit" atau ctrl + d di terminal dan coba login ke Server dengan password

- Server menolak login menggunakan password dan login hanya bisa menggunakan Public Key

<img src="image-13.png" width="700" height="400" />

```
ssh -i ~/.ssh/taofiks_key taofiks@192.168.100.104
```

<img src="image-14.png" width="700" height="400" />

## 💻 Text Manipulation

### grep

| Perintah             | Fungsi                                                                                        |
| -------------------- | --------------------------------------------------------------------------------------------- |
| `grep hello file`    | Mencari baris yang mengandung kata "hello" di dalam file                                      |
| `grep -c hello file` | Menghitung jumlah baris yang mengandung kata "hello" di dalam file                            |
| `grep hello *`       | Mencari semua baris yang mengandung kata "hello" di semua file yang ada di direktori saat ini |
| `grep -c hello *`    | Menghitung jumlah baris yang mengandung kata "hello" di setiap file di direktori saat ini.    |

<img src="image-15.png" width="700" height="400" />

<img src="image-16.png" width="700" height="400" />

<img src="image-17.png" width="700" height="400" />

<img src="image-18.png" width="700" height="400" />

---

### sed

| Perintah                       | Fungsi                                                                                                  |
| ------------------------------ | ------------------------------------------------------------------------------------------------------- |
| `sed -i 's/hello/asek/g' file` | Mencari semua teks "hello" dalam file dan menggantinya dengan "asek" tanpa memilik output ke file lain" |

<img src="image-19.png" width="700" height="400" />

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

![alt text](images/image-1.png)

- Menginstal versi terbaru dari paket yang sudah terpasang.

![alt text](images/image-2.png)

- Membuat direktori baru

![alt text](images/image-3.png)

- Membuat file kosong

![alt text](images/image-4.png)

- Menampilkan daftar file dan direktori dalam direktori saat ini.

![alt text](images/image-5.png)

- Menampilkan daftar file dan direktori dengan detail tambahan (permissions, owner, dll) serta hidden file dan direktori.

![alt text](images/image-6.png)

- Pindah ke direktori latihan

![alt text](images/image-7.png)

- Pindah ke direktori induk (parent directory).

![alt text](images/image-8.png)

- Menyalin file

![alt text](images/image-9.png)

- Memindahkan file ke direktori latihan

![alt text](images/image-10.png)

- Mengganti nama file

![alt text](images/image-11.png)

- Menampilkan string atau teks ke output

![alt text](images/image-12.png)

- Menampilkan string atau teks ke output file

![alt text](images/image-13.png)

- Melihat isi file

![alt text](images/image-14.png)

- Mencari file dan direktori

![alt text](images/image-15.png)

- Mencari file dengan spesifik

![alt text](images/image-16.png)

- Mencari teks dalam file

![alt text](images/image-17.png)

- Membuka teks editor bawaan linux

![alt text](images/image-18.png)

- Menacri teks di semua file

![alt text](images/image-19.png)

- Merubah file permission

![alt text](images/image-20.png)

- Mengubah pemilik dan grup dari suatu file.

![alt text](images/image-21.png)

- Melihat command yang sudah digunakan

![alt text](images/image-22.png)

- Berpindah ke root user

![alt text](images/image-23.png)
