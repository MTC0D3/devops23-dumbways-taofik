# 📘 DevOps Task - Day 4

- Penjelasan tentang git
- Buat sebuah repository bernama "dumbways-batch-23" yang berisi 3 file
- Manage repository tugas kalian (devops23-dumbways-<nama>) menggunakan terminal!

## 📃 Pengertian Git

- Git adalah satu version control system yag memiliki fitur unggulan distributed version control yang artinya penyimpanan git tidak hanya berada dalam satu tempat saja melainkan semua orang yang terlibat dalam pengkodean proyek akan menyimpan database git, sehingga akan memudahkan dalam mengelola proyek baik online atau offline.

<img src="image.png" width="700" height="400" />

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

<img src="image-1.png" width="700" height="400" />

### 2. Cek apakah Public Key dan Private Key sudah ada

- Lakukan pengecekan apakah public key dan private key sudah ada dengan perintah berikut

```
cd .ssh
ls
```

<img src="image-2.png" width="700" height="400" />

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

<img src="image-3.png" width="700" height="400" />

### 5. Konfigurasi di github

- Masuk ke menu settings pilih tab SSH and GPG keys

<img src="image-4.png" width="700" height="400" />

- Pilih new SSH kemudian masukan title dan masukan public key di form key kemudian klik add SSH key

<img src="image-5.png" width="700" height="400" />

- Github akan mengonfirmasi dengan meminta password login akun Github, mengisi password dan tekan Confirm

- Maka SSH Key berhasil ditambahkan ke akun Github

- Uji koneksi dari terminal SSH ke server Github dengan perintah berikut

```
ssh git@github.com -T
```

Jika muncul pesan seperti berikut maka koneksi berhasil

<img src="image-6.png" width="700" height="400" />
