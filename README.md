# 🚀 Ansible Docker Setup (Praktikan 1)

## 📌 Deskripsi
Project ini berisi konfigurasi Ansible untuk:
- Install Docker Engine
- Setup firewall (UFW) hanya membuka port 22 (SSH)

Menggunakan 2 node:
- Backend
- Frontend

---

## 🖥️ Requirement

- 2 Virtual Machine Ubuntu
- Ansible (WSL / Linux)
- SSH access ke VM

---

## 📁 Struktur Project
.
├── inventory.yml
├── playbook.yml
└── roles/
└── docker/
└── tasks/
└── main.yml

---

## ⚙️ Setup Step-by-Step

### 1. Clone Repository

```
git clone https://github.com/USERNAME/REPO-NAME.git
cd REPO-NAME
```

### 2. Setup 2 VM Ubuntu
Buat 2 VM:
- node-backend
- node-frontend
Cek IP masing-masing VM:
```
ip a
```
contoh:
```
Backend  : 192.168.7.30
Frontend : 192.168.7.31
```

### 3. Edit inventory.yml
```
backend:
  hosts:
    node_backend:
      ansible_host: 192.168.7.30 #Ganti IP nya sesuai dengan IP masing masing
      ansible_user: ubuntu

frontend:
  hosts:
    node_frontend:
      ansible_host: 192.168.7.31 #Ganti IP nya sesuai dengan IP masing masing
      ansible_user: ubuntu
```

### 4. Test Koneksi Ansible
```
ansible all -m ping -i inventory.yml
```
Jika berhasil:
```
SUCCESS => pong
```

### 5. Jalankan Playbook
```
ansible-playbook -i inventory.yml playbook.yml
```

## 🧪 Testing Docker
Masuk ke node:
```
ssh ubuntu@IP_NODE 
```
Jalankan:
```
docker run hello-world
```
Jika berhasil:
```
Hello from Docker!
```

## 🔐 Firewall
Cek status firewall:
```
sudo ufw status
```

## ⚠️ Catatan
- IP harus disesuaikan
- SSH harus aktif
- VM harus menyala saat digunakan

## 👥 Untuk Praktikan 2 & 3
1. Clone repo
2. Setup VM sendiri
3. Ubah IP di inventory.yml
4. Jalankan playbook

## ✅ Status
- ✔️ Docker installed
- ✔️ Firewall configured
- ✔️ Multi-node ready
