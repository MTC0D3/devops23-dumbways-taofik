# 📘 DevOps Task - Day 6

- Gambarkan sturktur web server menggunakan reverse proxy dan jelaskan cara kerjanya!

- Buatlah Reverse Proxy untuk aplilkasi yang sudah kalian deploy kemarin. (wayshub), untuk domain nya sesuaikan nama masing" ex: alvin.xyz .

## 📃 Gambarkan sturktur web server menggunakan reverse proxy dan jelaskan cara kerjanya!

## ⚔️ Buatlah Reverse Proxy untuk aplilkasi yang sudah kalian deploy kemarin. (wayshub), untuk domain nya sesuaikan nama masing" ex: alvin.xyz .

- Buka direktori windows

```
C:\Windows\System32\drivers\etc
```

<img src="image.png" width="700" height="400" />

- Edit hosts dengan notepad++ sebagai admin

```
192.168.100.200 taofik.xyz
```

<img src="image-1.png" width="700" height="400" />

- Buka terminal akses server dan run wayshub-frontend

```
ssh vm-dumbways
```

<img src="image-2.png" width="700" height="400" />

- Install nginx (jika belum ada)

```
sudo apt install nginx
```

<img src="image-3.png" width="700" height="400" />

- Cek status nginx running atau tidak

```
sudo systemctl status nginx
```

<img src="image-4.png" width="700" height="400" />

- Cek port http (80) apakah sudah dizinkan atau belum

```
sudo ufw status
```

<img src="image-5.png" width="700" height="400" />

- Cek di browser apakah domain sudah bisa digunakan

```
taofik.xyz
```

<img src="image-6.png" width="700" height="400" />

- Buat file untuk konfigurasi di sites-enabled

```
sudo nano /etc/nginx/sites-enabled/taofik.conf
```

```
    server {
        listen 80;
        server_name taofik.xyz;  # Your domain

        location / {
            proxy_pass http://192.168.100.104:3000;  # Forward to WaysHub
            proxy_set_header Host $host;
            proxy_set_header X-Real-IP $remote_addr;
        }
    }
```

<img src="image-7.png" width="700" height="400" />

- Tes konfigurasi nginx dan restart nginx

```
sudo nginx -t
```

```
sudo systemctl restart nginx
```

```
sudo systemctl status nginx
```

<img src="image-8.png" width="700" height="400" />

- Jalankan project wayshub-frontend

```
use nvm 13
```

```
npm start
```

<img src="image-9.png" width="700" height="400" />

- Cek kembali di browser dengan menggunakan domain yang dibuat

```
taofik.xyz
```

<img src="image-10.png" width="700" height="400" />
