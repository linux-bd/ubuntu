## 🐳 Docker Installation Steps on Ubuntu

### **1️⃣ Update your system**

```bash
sudo apt update && sudo apt upgrade -y
```

### **2️⃣ Install Docker**

```bash
sudo apt install docker.io -y
```

> ✅ এটি `docker.io` প্যাকেজ ইন্সটল করবে, যা Ubuntu রিপোজিটরিতে থাকা অফিসিয়াল Docker Engine।

---

### **3️⃣ Enable & Start Docker Service**

```bash
sudo systemctl enable docker
sudo systemctl start docker
```

---

### **4️⃣ Check Docker Status**

```bash
sudo systemctl status docker
```

> ✅ এখানে যদি “active (running)” দেখা যায়, তাহলে Docker চলছে।

---

### **5️⃣ Verify Docker Installation**

```bash
docker --version
docker ps
```

> `docker ps` এখনো permission error দিতে পারে, কারণ docker group permissions এখনো দেওয়া হয়নি।

---

### **6️⃣ Add current user to Docker group**

```bash
sudo usermod -aG docker ${USER}
```

> ⚠️ এরপর **logout করে আবার login** করতে হবে (বা `newgrp docker` চালাও) যাতে permission কাজ করে।

---

### **7️⃣ Verify docker command without sudo**

```bash
docker ps
docker images
```

---

### **8️⃣ Check disk usage**

```bash
df -H
```

> এটি ডিস্ক স্পেস দেখাবে — Docker images গুলো কত জায়গা নিচ্ছে বুঝতে কাজে লাগে।

---

### **9️⃣ Optional: Test Docker with Hello World**

```bash
docker run hello-world
```

> যদি “Hello from Docker!” দেখা যায় — তাহলে Docker সম্পূর্ণভাবে install ও configure হয়ে গেছে 🎉
