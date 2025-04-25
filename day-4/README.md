# 📘 DevOps Task - Day 4

- Penjelasan tentang git
- Buat sebuah repository bernama "dumbways-batch-23" yang berisi 3 file
- Manage repository tugas kalian (devops23-dumbways-<nama>) menggunakan terminal!

## Pengertian Git

- Git adalah satu version control system yag memiliki fitur unggulan distributed version control yang artinya penyimpanan git tidak hanya berada dalam satu tempat saja melainkan semua orang yang terlibat dalam pengkodean proyek akan menyimpan database git, sehingga akan memudahkan dalam mengelola proyek baik online atau offline.

<img src="image.png" width="700" height="400" />

### Perintah Dasar Git

| Perintah                | Fungsi                                                         |
| :---------------------- | :------------------------------------------------------------- |
| `git init`              | Membuat repositori baru                                        |
| `git clone <url>`       | Mengunduh repositori dari remote                               |
| `git status`            | Melihat status file yang diubah atau belum di-commit           |
| `git add <file>`        | Menambahkan file ke staging area                               |
| `git commit -m "pesan"` | Menyimpan perubahan ke repositori lokal                        |
| `git log`               | Melihat riwayat commit                                         |
| `git restore <file>`    | Mengembalikan file ke versi terakhir dari commit terakhir      |
| `git restore --staged`  | Menghapus file dari staging area, tapi tidak mengubah isi file |

### Bekerja dengan Remote

| Perintah                      | Fungsi                                            |
| :---------------------------- | :------------------------------------------------ |
| `git remote add origin <url>` | Menghubungkan repo lokal ke remote                |
| `git push origin <branch>`    | Mengirim perubahan ke remote                      |
| `git pull origin <branch>`    | Mengambil dan menggabungkan perubahan dari remote |
| `git fetch`                   | Mengambil semua update dari remote tanpa merge    |
| `git remote -v`               | Melihat daftar remote repositori                  |

### Branching dan Merging

| Perintah                 | Fungsi                                        |
| :----------------------- | :-------------------------------------------- |
| `git branch`             | Melihat daftar branch                         |
| `git branch <nama>`      | Membuat branch baru                           |
| `git checkout <branch>`  | Pindah ke branch tertentu                     |
| `git checkout -b <nama>` | Membuat dan langsung berpindah ke branch baru |
| `git merge <branch>`     | Menggabungkan branch ke branch aktif          |
| `git rebase <branch>`    | Menyusun ulang riwayat commit                 |
