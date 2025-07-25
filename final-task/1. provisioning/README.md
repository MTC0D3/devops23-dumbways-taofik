---
# Provisioning
---

## TASK

**Before you start the task, please read this:**
- Please screenshot the command step-by-step
- Describe the process in your final task repository

**Requirements**
- Local machine w/ Ansible & Terraform
- Biznet GIO NEO Lite Servers
  - Appserver - 2 CPU, 2GB RAM
  - Gateway - 1 CPU, 1GB RAM
-  Others Servers if required

**Instructions**
- Attach SSH keys & IP configuration to all VMs
- Server Configuration using Ansible

---

## Attach SSH keys & IP configuration to all VMs

1. Buat public dan private key di local computer (saya pakai wsl)

```
ssh-keygen -t rsa -b 4096
```

![alt text](image.png)

2. Tekan enter saja semua sampai public dan private key terbuat

3. Cek public dan private key di direktori `.ssh`, jika benar maka akan ada `id_rsa` dan `id_rsa.pub`

```
cd .ssh

ls
```

![alt text](image-1.png)


4. Lalu copy isi dari public key yaitu dari file `id_rsa.pub`

```
cat id_rsa.pub
```

5. Lalu buka biznet gio cloud dan akses dashboard nya

![alt text](image-2.png)

6. Klik tab `SSH key`

![alt text](image-3.png)

7. Lalu klik `Add SSH Key`

8. Beri nama ssh key dan masukan public key yang dibuat tadi

![alt text](image-4.png)

9. Lalu klik `Add`

10. Pilih tab `NEO Lite`

11. Masuk ke salah satu server scroll ke bawah cari SSH Access lalu ganti dengan key yang dibuat tadi, klik update key

![alt text](image-5.png)

12. Lakukan hal yang sama ke semua server

---

## Server Configuration using Ansible

1. Install ansible di local computer (saya gunakan wsl)

```
sudo apt update
sudo apt install software-properties-common
sudo add-apt-repository --yes --update ppa:ansible/ansible
sudo apt install ansible
```

![alt text](image-6.png)

2. Validasi installasi dengan perintah berikut

```
ansible --version
```

![alt text](image-7.png)

3. Dan untuk scriptnya bisa dilihat [DISINI](https://github.com/MTC0D3/devops23-dumbways-taofik/tree/main/final-task/ansible)

4. Selanjutnya, untuk menjalankan scriptnya bisa satu persatu seperti ini

```
ansible-playbook 1_install_docker.yaml;
ansible-playbook 2_create_user.yaml;
ansible-playbook 3_setup_ufw_port.yaml;
ansible-playbook 4_install_monitoring.yaml;
ansible-playbook 5_reverse_proxy.yaml;
ansible-playbook 6_clone_repository.yaml;
ansible-playbook 7_install_jenkins.yaml;
```