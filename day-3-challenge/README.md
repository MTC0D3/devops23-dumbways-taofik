# 📘 DevOps Challenge - Day 3

- Bisa ssh kedalam server dengan contoh command : `ssh vm-dumbways`
- Rubah port SSH menjadi 6969
- SSH hanya bisa diakses 1 device (jika login dari device lain akan bentrok)

## 📃 Membuat alias 'vm-dumbways' untuk Login SSH

- Membuat file config di direktori 'C:\Users\nama_user\.ssh'

<img src="image.png" width="700" height="400" />

- Buka file config dengan notepad dan menambahkan script berikut kemudian simpan:

```
Host vm-dumbways
    HostName 192.168.100.104
    User taofiks
    Port 22
    IdentityFile ~/.ssh/taofiks_key
```

<img src="image-1.png" width="700" height="400" />

- Buka terminal lalu login SSH dengan command berikut:

```
ssh vm-dumbways
```

<img src="image-2.png" width="700" height="400" />

## 📝 Mengubah Konfigurasi Port SSH ke 6969

- Buka konfigurasi SSH pada Ubuntu Server dengan text editor nano

```
sudo nano /etc/ssh/sshd_config
```

<img src="image-3.png" width="700" height="400" />

- Ubah konfigurasi port yang sebelumnya default 22 menjadi 6969. Setelah selesai lalu simpan file konfigurasi tersebut.

<img src="image-4.png" width="700" height="400" />

<img src="image-5.png" width="700" height="400" />

- Restart service SSH

```
sudo systemctl restart ssh
```

<img src="image-6.png" width="700" height="400" />

- Logout dari SSH dengan mengeksekusi command exit, lalu masuk kembali

<img src="image-7.png" width="700" height="400" />

- Diketahui koneksi pada port 22 ditolak, untuk mengatasinya maka diperlukan modifikasi pada file 'C:\Users\nama_user\.ssh\config' dengan mengubah konfigurasi port dari 22 ke 6969

<img src="image-8.png" width="700" height="400" />

<img src="image-9.png" width="700" height="400" />

- Simpan file config dan coba login ulang pada SSH Server

<img src="image-10.png" width="700" height="400" />

## ⚔️ Pembatasan Akses Server melalui SSH Hanya 1 Device

- Buka konfigurasi SSH pada Ubuntu Server dengan text editor nano

```
sudo nano /etc/ssh/sshd_config
```

- Ubah konfigurasi MaxSessions dan MaxStartups. Setelah selesai lalu simpan file konfigurasi tersebut.

**Catatan :**

MaxSessions 1 = Maksimal 1 sesi SSH per koneksi.

MaxStartups 1:1:1 = Cuma 1 koneksi SSH diizinkan pada saat bersamaan (dengan delay 0%).

<img src="image-11.png" width="700" height="400" />

- Restart service SSH

```
sudo systemctl restart ssh
```

<img src="image-12.png" width="700" height="400" />

- Uji coba dengan device lain, maka akan terjadi Connection refused

<img src="image-14.png" width="700" height="400" />

<img src="image-15.jpg" width="700" height="400" />
