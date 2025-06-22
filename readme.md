
## 🐳 Docker & Docker Compose Installation on Linux (Ubuntu 24.04)

Follow these steps to install **Docker** and **Docker Compose** on your Ubuntu 24.04 server (or Droplet):

### ✅ Step 1: Update the system

```bash
sudo apt update && sudo apt upgrade -y
```

---

### ✅ Step 2: Install required dependencies

```bash
sudo apt install ca-certificates curl gnupg lsb-release -y
```

---

### ✅ Step 3: Add Docker’s official GPG key

```bash
sudo mkdir -p /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | \
  sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
```

---

### ✅ Step 4: Set up the Docker repository

```bash
echo \
  "deb [arch=$(dpkg --print-architecture) \
  signed-by=/etc/apt/keyrings/docker.gpg] \
  https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

---

### ✅ Step 5: Install Docker Engine

```bash
sudo apt update
sudo apt install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin -y
```

---

### ✅ Step 6: Enable and start Docker

```bash
sudo systemctl enable docker
sudo systemctl start docker
```

---

### ✅ Step 7: Verify installation

```bash
docker --version
docker compose version
```

> ✅ You should see versions like:
>
> * `Docker version 24.0.0+`
> * `Docker Compose version v2.x.x`

---

### 🔐 (Optional) Add your user to the docker group

This allows you to run Docker without `sudo`.

```bash
sudo usermod -aG docker $USER
newgrp docker
```

---
🐳 3. Run Docker Compose

Make sure you have a docker-compose.yml file in your project root.

Start your services:
```bash
docker compose up -d
```
Check logs:


```bash
docker compose logs -f
```

Stop all containers:

```bash
docker compose down
```


✅ Common Commands
Action	Command
Start services	docker compose up -d
Stop services	docker compose down
View logs	docker compose logs -f
Restart services	docker compose restart
Rebuild containers	docker compose up --build
