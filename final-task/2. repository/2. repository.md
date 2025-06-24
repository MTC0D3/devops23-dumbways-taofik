---
# REPOSITORY
---

## TASK

**Before you start the task, please read this:**
- Please screenshot the command step-by-step
- Describe the process in your final task repository

**Requirements**
- Personal Github/GitLab accounts (must be private)
- Frontend : [fe-dumbmerch](https://github.com/demo-dumbways/fe-dumbmerch)
  - NodeJS v16.x or above
  - Create .env file for FE+BE Integration (REACT_APP_BASEURL) https://api.ade.studentdumbways.my.id/api/v1


- Backend : [be-dumbmerch](https://github.com/demo-dumbways/be-dumbmerch)
  - Golang v1.16.x or above
  - Modify .env file for DB Integration

**Instructions**
- Create a repository on Github or Gitlab
- **Private** repository access
- Set up 2 branches
   - Staging
   - Production
- Each Branch have their own CI/CD

---

## Create Private Github Repository

1. Silahkan buat repository baru di github [DISINI](https://github.com/new)

2. Selanjutnya ganti dari public ke private, lalu buat repository-nya

![alt text](image.png)

### fe-dumbmerch

![alt text](image-1.png)

### be-dumbmerch

![alt text](image-2.png)

3. Untuk clone repository menggunakan ansible, untuk scriptnya bisa dilihat [DISINI](../ansible/6_clone_repository.yaml)

4. Cek apakah branch baru sudah terbuat

```
git branch -a
```

5. Selanjutnya, koneksikan ke github. Buka pengaturan akun github dengan mengklik Settings. Lalu pilih SSH and GPG Keys -> New SSH Key

6. Masukkan Public key yang digunakan pada server

7. Selanjutnya jalankan command berikut

```
git config --global user.email "email@contoh.com" && git config --global user.name "githubuser"
```

8. Jika sudah, coba cek koneksi ke github. Jika sukses akan muncul seperti ini

```
ssh -T git@github.com
```

9. Buat file .env untuk frontend

```
echo "REACT_APP_BASEURL=https://api.taofik.studentdumbways.my.id/api/v1" > .env
```

10. Edit file .env untuk backend, sesuaikan dengan database yang digunakan

11. Selanjutnya, Pastikan branch sudah sesuai, lalu push ke repository yang barusan dibuat

```
git switch staging
git add .
git commit -m 'updating .env'
git push origin staging
```

12. Ganti ke branch production

```
git switch production
```

13. Lakukan merge dan push

```
git merge staging
git push origin production
```

14. Lakukan push juga pada fe-dumbmerch dan pastikan untuk push ke semua branch