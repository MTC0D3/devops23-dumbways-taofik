# 📘 DevOps Task - Day 4

- Penjelasan tentang git
- Buat sebuah repository bernama "dumbways-batch-23" yang berisi 3 file
- Manage repository tugas kalian (devops23-dumbways-<nama>) menggunakan terminal!

## 📃 Pengertian Git

- Git adalah satu version control system yag memiliki fitur unggulan distributed version control yang artinya penyimpanan git tidak hanya berada dalam satu tempat saja melainkan semua orang yang terlibat dalam pengkodean proyek akan menyimpan database git, sehingga akan memudahkan dalam mengelola proyek baik online atau offline.

<img src="images/image.png" width="700" height="400" />

### Perintah Dasar

| Perintah                | Fungsi                                                          |
| :---------------------- | :-------------------------------------------------------------- |
| `git init`              | Membuat repositori baru                                         |
| `git clone <url>`       | Mengunduh repositori dari repositori server                     |
| `git status`            | Melihat status file yang diubah atau belum di-commit            |
| `git add <file>`        | Menambahkan file ke staging index                               |
| `git commit -m "pesan"` | Menyimpan perubahan ke repositori lokal                         |
| `git log`               | Melihat riwayat commit                                          |
| `git restore <file>`    | Mengembalikan file ke versi terakhir dari commit terakhir       |
| `git restore --staged`  | Menghapus file dari staging index, tapi tidak mengubah isi file |

---

### Remote

| Perintah                      | Fungsi                                            |
| :---------------------------- | :------------------------------------------------ |
| `git remote add origin <url>` | Menghubungkan repo lokal ke remote                |
| `git push origin <branch>`    | Mengirim perubahan ke remote                      |
| `git pull origin <branch>`    | Mengambil dan menggabungkan perubahan dari remote |
| `git fetch`                   | Mengambil semua update dari remote tanpa merge    |
| `git remote -v`               | Melihat daftar remote repositori                  |

---

### Branching & Merging

| Perintah                 | Fungsi                                        |
| :----------------------- | :-------------------------------------------- |
| `git branch`             | Melihat daftar branch                         |
| `git branch <nama>`      | Membuat branch baru                           |
| `git checkout <branch>`  | Pindah ke branch tertentu                     |
| `git checkout -b <nama>` | Membuat dan langsung berpindah ke branch baru |
| `git merge <branch>`     | Menggabungkan branch ke branch aktif          |
| `git rebase <branch>`    | Menyusun ulang riwayat commit                 |

## 📝 Membuat Repositori Github dan push ke Repositori

### 1. Konfigurasi username dan email untuk akun Github

- Gunakan perintah berikut untuk melakukan konfigurasi

```
git config --global user.name <username>
git config --global user.email "<email>"
git config --list
```

<img src="images/image-1.png" width="700" height="400" />

### 2. Cek apakah Public Key dan Private Key sudah ada

- Lakukan pengecekan apakah public key dan private key sudah ada dengan perintah berikut

```
cd .ssh
ls
```

<img src="images/image-2.png" width="700" height="400" />

### 3. Buat pasangan Public Key dan Private Key (Jika belum ada)

- Buatlah pasangan public key dan private key jika belum ada dengan perintah berikut

```
ssh-keygen
```

### 4. Salin Public key

- Tampilkan isi file id_rsa.pub dan salin dengan perintah berikut

```
cat id_rsa.pub
```

<img src="images/image-3.png" width="700" height="400" />

### 5. Konfigurasi di github

- Masuk ke menu settings pilih tab SSH and GPG keys

<img src="images/image-4.png" width="700" height="400" />

- Pilih new SSH kemudian masukan title dan masukan public key di form key kemudian klik add SSH key

<img src="images/image-5.png" width="700" height="400" />

- Github akan mengonfirmasi dengan meminta password login akun Github, mengisi password dan tekan Confirm

- Maka SSH Key berhasil ditambahkan ke akun Github

- Uji koneksi dari terminal SSH ke server Github dengan perintah berikut

```
ssh git@github.com -T
```

Jika muncul pesan seperti berikut maka koneksi berhasil

<img src="images/image-6.png" width="700" height="400" />

### 6. Buat direktori dan beberapa file (Opsional)

- Buatlah sebuah direktori dan beberapa file dengan perintah berikut

```
mkdir day-4
cd day-4
echo "Hai Taofik" > file1
"Semangat yaa" > file2
echo "Bisa koo" > file3
ls
```

<img src="images/image-7.png" width="700" height="400" />

### 7. Buat repositori lokal baru dengan nama "dumbways-batch-23"

- Gunakan perintah berikut untuk membuat repositori lokal

```
git init dumbways-batch-23
```

<img src="images/image-8.png" width="700" height="400" />

### 8. Pindahkan file1, file2, dan file3 ke direktori "dumbways-batch-23"

- Gunakan perintah berikut untuk memindahkan file

```
mv file1 dumbways-batch-23
mv file2 dumbways-batch-23
mv file3 dumbways-batch-23
```

<img src="images/image-9.png" width="700" height="400" />

### 9. Membuat .gitignore untuk menyimpan file atau direktori yang akan diabaikan git

- Buat file .gitignore dengan perintah berikut

```
nano .gitignore
```

<img src="images/image-11.png" width="700" height="400" />

<img src="images/image-10.png" width="700" height="400" />

### 10. Menambahkan perubahan repositori ke staging index

- Gunakan perintah berikut untuk menambahkan perubahan repo kita ke staging index

```
git add .
git status
```

<img src="images/image-12.png" width="700" height="400" />

### 11. Melakukan commit dan memberikan pesan "First commit"

- Gunakan perintah berikut untuk menyimpan projek ke repo lokal dan menambahkan pesan

```
git commit -m "First commit"
```

<img src="images/image-13.png" width="700" height="400" />

### 12. Restore repositori

- Jika ingin mengembalikan atau merubah isi file sebelum di commit sesuai dengan sebelumnya gunakan git restore

```
git restore file1
```

<img src="images/image-14.png" width="700" height="400" />

### 13. Buat repositori baru di Github

- Buat repositori dengan nama yang sama seperti di repo lokal yaitu "dumbways-batch-23"

<img src="images/image-15.png" width="700" height="400" />

### 14. Menghubungkan repo Github dengan repo lokal

- Remote sesuai link dan pastikan memilih SSH di atas sebab perubahan akan dikirim ke repositori Github menggunakan command SSH

```
git remote add origin git@github.com:MTC0D3/dumbways-batch-23.git
```

<img src="images/image-16.png" width="700" height="400" />

<img src="images/image-17.png" width="700" height="400" />

- Jika ingin mengganti branch yang tersedia, dapat menggunakan command berikut:

```
git branch -M <branch>
```

<img src="images/image-18.png" width="700" height="400" />

### 15. Mengirim perubahan ke repositori Github

- Gunakan perintah berikut untuk mengirim perubahan

```
git push -u origin master
```

<img src="images/image-19.png" width="700" height="400" />

### 16. Maka sudah terjadi perubahan di repositori Github "dumbways-batch-23"

<img src="images/image-20.png" width="700" height="400" />

## ⚔️ Manage repository menggunakan terminal

### The Three States

- Git memiliki tiga state terhadap file kita: modified, staged dan committed
- Modified artinya kita mengubah (menambah, mengedit, menghapus) file, namun belum disimpan secara permanen ke repository
- Staged artinya kita menandai modifikasi yang kita lakukan terhadap file akan disimpan secara permanen ke repository
- Committed artinya data sudah aman disimpan di repository

### 1. Memeriksa status dari repositori lokal

- Gunakan perintah berikut untuk melihat statusnya

```
git status
```

<img src="images/image-21.png" width="700" height="400" />

### 2. Menambahkan perubahan repositori ke staging index

- Gunakan perintah berikut untuk menambahkan ke staging index

```
git add .
```

<img src="images/image-22.png" width="700" height="400" />

### 3. Melakukan commit dan memberikan pesan

- Gunakan perintah berikut untuk melakukan commit

```
git commit -m "Update Readme.md task day-4"
```

<img src="images/image-23.png" width="700" height="400" />

### 4. Mengirim perubahan ke repositori Github

- Gunakan perintah berikut untuk mengirim perubahan

```
git push
```

**Catatan :**

- Saya telah menggunakan -u singkatan dari --set-upstream sebelumnya, artinya:
- Sudah di atur supaya next time kamu tinggal ketik git push atau git pull tanpa harus sebut nama branch lagi, karena Git udah tahu branch lokal ini terhubung ke branch master di remote origin.

<img src="images/image-24.png" width="700" height="400" />
