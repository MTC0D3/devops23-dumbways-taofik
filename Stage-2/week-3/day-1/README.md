# 📘 DevOps Task - Day 1

Membuat konfigurasi ansible untuk :
    - Install docker
    - membuat user baru (nama user mentor) dengan home
    - Menjalankan aplikasi wayshub (frontend+backend+db dengan compose docker)

## Install Ansible

1. Untuk Ubuntu, cara installnya cukup dengan menjalankan command berikut

```
sudo apt update
sudo apt install software-properties-common
sudo add-apt-repository --yes --update ppa:ansible/ansible
sudo apt install ansible
```

2. Cek installasi sudah sukses atau belum

```
ansible --version
```

## Konfigurasi Ansible 

1. Buat direktori ansible

```
mkdir ansible
```

2. buat group variabel

```
mkdir group_vars

cd group_vars

nano all
```

masukan script berikut

```
# Inventory
username: "taofiks"

# Create New user
newuser: "ads"
home_dir: "/home/{{ newuser }}"
public_key: "/home/ubuntu/.ssh/authorized_keys" # location of your pub_key in your local machine
enc_pass: "$6$zPj2MDxDKoYtjKa2$HOEIwJNblz8uoAy.8VouCtUEV5DKTiZNp90JiDyOqiy1rHZxs5k8NXFDuCi94qrJ5DIswUO6mguFNOg4J7PAU." # 1

# Monitoring
job_name: "dw-devops-23"
scrape_interval: "5s"
targets:
  - "103.175.221.143:9100"
  - "103.127.136.1:9100"
grafana_dir: "{{ home_dir }}/grafana"
prometheus_config: "{{ grafana_dir }}/prometheus.yml"
grafana_datasources: "{{ grafana_dir }}/provisioning/datasources"
grafana_data: "{{ grafana_dir }}/data"

# Reverse Proxy
nginx_dir: "{{ home_dir }}/nginx"
cloudflare_api: "419c5a759060eac71d19cbf9a231ec94267ca"
cloudflare_email: "taofik.code@gmail.com"
domain: "taofik.studentdumbways.my.id"
subdomains:
  - name: "exporter."
    backend: "103.175.221.143:9100"
  - name: "monitoring."
    backend: "103.175.221.143:3000"
  - name: "prom."
    backend: "103.175.221.143:9090"
```

3. buat file inventory

```
nano inventory
```

masukan script berikut

```
appserver ansible_host=103.175.221.143 ansible_user="{{ newuser }}" ansible_ssh_port="{{SSHport}}"
gateway ansible_host=103.127.136.1 ansible_user="{{ newuser }}" ansible_ssh_port="{{ SSHport }}"
```

4. buat file ansible.cfg

```
nano ansible.cfg
```

masukan script berikut

```
[defaults]
host_key_checking = False
inventory = ./inventory
private_key_file = ./gateway.pem

[privilege_escalation]
become=True
become_method=sudo
#become_user=root
become_ask_pass=False
```

## 📃 Install docker

1. buat file docker_installer.sh

```
nano docker_insatller.sh
```

masukan script berikut

```
#!/bin/bash

# Cek Update
echo -e "\n\n~~~Step 1: Cek Update!~~~\n\n"
sudo apt-get update

# Upgrade
echo -e "\n\n~~~Step 2: Melakukan Upgrade!~~~\n\n"
sudo apt-get upgrade -y

# Selesai Update & Upgrade
echo -e "\n\n~~~Selesai Update & Upgrade!~~~\n\n"

# Add Docker's official GPG key:
echo -e "\n\n~~~Step 3: Menambahkan GPG key!~~~\n\n"
sudo apt-get install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

echo -e "\n\n~~~Selesai menambahkan GPG key!~~~\n\n"

# Add the repository to Apt sources:

echo -e "\n\n~~~Step 4: Menambahkan Docker ke repository APT!~~~\n"

echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

sleep 1
echo -n "Done!!"

echo -e "\n\n~~~Selesai menambahkan Docker ke repository APT!~~~\n\n"

echo -e "\n\n~~~Step 5: Cek Update!~~~\n\n"
sudo apt-get update

echo -e "\n\n~~~Step 6: Install Docker!~~~\n\n"
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin -y

# Add current user to docker group
echo -e "\n\n~~~Adding current user to Docker Group!~~~\n\n"
sudo usermod -aG docker $USER
sleep 1
echo -n "Done!!"

# Cek versi Docker
echo -e "\n\n~~~Cek versi Docker!~~~\n\n"
docker -v

echo -e "\n\n~~Selesai!~~~\n\n"
```

2. buat file docker.yaml 

```
nano docker.yaml
```

masukan script berikut

```
- name: "Install Docker Engine using Ansible"
  hosts: all
  become: true
  vars:
    ansible_user: "{{ username }}"
    ansible_ssh_port: "22"

  tasks:
    - name: "Copy docker_installer.sh to remote host"
      copy:
        src: docker_installer.sh
        dest: /tmp/docker_installer.sh
        mode: '0755'

    - name: "Run Docker installer script"
      shell: "bash /tmp/docker_installer.sh"

    - name: "Ensure Docker service is started and enabled"
      systemd:
        name: docker
        state: started
        enabled: yes
```

3. Jalankan playbook dengan perintah berikut

```
ansible-playbook docker.yaml
```

## 📃 Membuat user baru (nama user mentor) dengan home

1. Buat file user.yaml

```
nano user.yaml
```

masukan script beriut

```
- name: "Create user using Ansible"
  hosts: all
  become: true
  vars:
    ansible_user: "{{ username }}"
    ansible_ssh_port: "22"
  tasks:

    - name: "Create new user with sudo and docker access"
      user:
        name: "{{ newuser }}"
        password: "{{ enc_pass }}"
        shell: /bin/bash
        createhome: yes
        groups: sudo,docker
        append: yes

    - name: "Add sudoers entry to disable password prompt"
      become: yes
      lineinfile:
        path: /etc/sudoers.d/nopassword
        line: '{{ newuser }} ALL=(ALL) NOPASSWD:ALL'
        create: yes
        validate: 'visudo -cf %s'

    - name: "Create .ssh folder"
      file:
        path: "{{ home_dir }}/.ssh"
        state: directory
        owner: "{{ newuser }}"
        group: "{{ newuser }}"
        mode: 0700

    - name: "Create authorized_keys"
      copy:
        src: "{{ public_key }}"
        dest: "{{ home_dir }}/.ssh/authorized_keys"
        owner: "{{ newuser }}"
        group: "{{ newuser }}"
        mode: 0600

    - name: "Allow login using pubkey"
      lineinfile:
        path: "/etc/ssh/sshd_config"
        regexp: 'PubkeyAuthentication no'
        line: 'PubkeyAuthentication yes'

    - name: "Disable password authentication for root"
      lineinfile:
        path: /etc/ssh/sshd_config
        state: present
        regexp: '^#?PermitRootLogin'
        line: 'PermitRootLogin prohibit-password'

    - name: "Reload ssh"
      ansible.builtin.systemd_service:
        name: ssh
        state: restarted
```

3. Jalankan playbook dengan perintah berikut

```
ansible-playbook user.yaml
```

## Menjalankan aplikasi wayshub (frontend+backend+db dengan compose docker)

1. Buat file docker-compose.yaml

```
nano docker-compose.yaml
```

Masukan script berikut

```
version: '3.8'

services:
  database:
    image: mtc0d3/wayshub-db
    container_name: wayshub-db
    restart: always
    networks:
      - herta
    environment:
      MYSQL_ROOT_PASSWORD: rootpassword
      MYSQL_USER: user
      MYSQL_PASSWORD: password
      MYSQL_DATABASE: wayshub
    ports:
      - "3306:3306"
    volumes:
      - mysql-data:/var/lib/mysql
    healthcheck:
      test: ["CMD", "mysqladmin", "ping", "-h", "localhost"]
      timeout: 5s
      retries: 10

  backend:
    image: mtc0d3/wayshub-be
    container_name: wayshub-be
    restart: always
    depends_on:
      database:
        condition: service_healthy
    networks:
      - herta
    environment:
      DB_HOST: database
      DB_USER: user
      DB_PASSWORD: password
      DB_NAME: wayshub
    ports:
      - "5000:5000"
    command: >
      sh -c "
      npx sequelize db:create &&
      npx sequelize db:migrate &&
      pm2-runtime ecosystem.config.js
      "

  frontend:
    image: mtc0d3/wayshub-fe
    container_name: wayshub-fe
    restart: always
    depends_on:
      - backend
    networks:
      - herta
    stdin_open: true
    ports:
      - "3000:3000"
    command: >
      sh -c "
      pm2-runtime ecosystem.config.js
      "

volumes:
  mysql-data:

networks:
  herta:
```

2. Buat file deploy.yaml

```
nano deploy.yaml
```

Masukan script berikut

```
- name: Jalankan Docker Compose
  hosts: appserver
  become: true

  vars:
    compose_project_dir: "/home/{{newuser}}/project"

  tasks:
    - name: Pastikan direktori project ada
      file:
        path: "{{ compose_project_dir }}"
        state: directory
        owner: "{{newuser}}"
        group: "{{newuser}}"
        mode: '0755'

    - name: Salin file docker-compose.yaml
      copy:
        src: ./docker-compose.yaml
        dest: "{{ compose_project_dir }}/docker-compose.yaml"
        owner: "{{newuser}}"
        group: "{{newuser}}"
        mode: '0664'

    - name: Jalankan Docker Compose
      shell: docker compose up -d
      args:
        chdir: "{{ compose_project_dir }}"
```

3. Jalankan playbook dengan perintah berikut

```
ansible-playbook deploy.yaml
```