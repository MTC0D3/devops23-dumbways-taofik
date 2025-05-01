# 📘 DevOps Challenge - Day 4

- Repository dumbways-batch-23 dibuat private

- Demokan penggunaan Pull Request

## 📃 Membuat Repositori dumbways-batch-23 Menjadi Private

- Membuka repositori dumbways-batch-23
- Pilih Settings
- Muncul halaman Settings untuk repositori tersebut, scroll sampai menemukan tampilan sebagai berikut, lalu pilih Change visibility
- Change to private

<img src="images/image.png" width="700" height="400" />

- Klik I want to make this repository private

<img src="images/image-1.png" width="700" height="400" />

- Klik I have read and understand these effects

<img src="images/image-2.png" width="700" height="400" />

- Klik Make this repository private

<img src="images/image-3.png" width="700" height="400" />

- Masukkan password akun Github untuk konfirmasi

<img src="images/image-4.png" width="700" height="400" />

- Setelah berhasil maka repositori dumbways-batch-23 sudah menjadi Private

<img src="images/image-5.png" width="700" height="400" />

## 📝 Demonstrasi Git Pull Request

- Clone repositori dumbways-batch-23 ke direktori lokal

```
git clone git@github.com:MTC0D3/dumbways-batch-23.git backend-1
```

<img src="images/image-6.png" width="700" height="400" />

- Masuk ke direktori backende-1 dan buat branch baru

```
cd backend-1
```

```
git checkout -b hero
```

```
git status
```

<img src="images/image-7.png" width="700" height="400" />

- Buat perubahan pada salah satu file yang tersedia, misal file1

```
ls
```

```
cat file1
```

```
nano file1
```

```
cat file1
```

```
git status
```

<img src="images/image-8.png" width="700" height="400" />

- file1 telah mengalami perubahan (modified), melakukan staging file1, commit, dan push kembali ke repositori dengan branch 'hero'

```
git add .
```

```
git commit -m "Buat hero section"
```

```
git push origin hero
```

<img src="images/image-9.png" width="700" height="400" />

- Buka repositori dumbways-batch-23 dan akan muncul tombol 'Compare & pull request'. Saat ini seolah pemilik repositori akan meninjau pull request sehingga tombol tersebut perlu diklik

<img src="images/image-10.png" width="700" height="400" />

- Open pull request dengan mengisi title dan description klik 'Create pull request'

<img src="images/image-11.png" width="700" height="400" />

- Jika pemilik repositori ingin melihat perubahan pada file yang diajukan, dapat melihat pada tab 'Files changed'

<img src="images/image-12.png" width="700" height="400" />

- Setelah Open Pull request, pemilik repositori dapat langsung melakukan merge jika tidak ada konflik dengan base branch dengan klik 'Merge pull request'.

<img src="images/image-13.png" width="700" height="400" />

- Mengisi informasi untuk melakukan Merge lalu Confirm merge

<img src="images/image-14.png" width="700" height="400" />

- Pull request yang telah dikonfirmasi untuk Merge akan memiliki tampilan sebagai berikut

<img src="images/image-15.png" width="700" height="400" />

- jika pull request sudah dilakukan merge dengan base branch, maka dari backend-1 dapat membersihkan branch hero (Opsional)

```
git checkout master
```

```
git pull origin master
```

```
git branch -d hero
```

<img src="images/image-16.png" width="700" height="400" />

Dari pemilik repositori:

```
git push origin --delete hero
```

<img src="images/image-18.png" width="700" height="400" />

Sebelum branch hero dihapus:

<img src="images/image-17.png" width="700" height="400" />

Setelah branch hero dihapus:

<img src="images/image-19.png" width="700" height="400" />
