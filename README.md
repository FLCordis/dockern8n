# 🚀 Docker Environment: N8N + Postgres + Redis + Waha + Ngrok

This repository provides a complete **Docker-based environment** to run [N8N](https://n8n.io/) with **Postgres**, **Redis**, **Waha (WhatsApp Gateway)**, and **Ngrok** for secure public exposure.

## 📂 Project structure

```
.
├── docker-compose.yml # Docker services definition
├── .env # Environment variables (⚠️ do not commit to public repos!)
├── ngrok.yml # Ngrok tunnel configuration
└── README.md # This guide
```


## 🔧 Included services

- **Postgres** → Database for N8N  
- **Redis** → Cache / messaging  
- **Waha** → WhatsApp gateway  
- **N8N** → Workflow automation tool  
- **Ngrok** → Secure tunnel to expose N8N publicly  

## ▶️ How to use

1. **Set up your `.env`** (example):
   ```env
   NGROK_TOKEN=YOUR_TOKEN_HERE
   ```
2. **Configure ngrok.yml (only if you change the N8N location/container)**:
```yaml
tunnels:
  n8n:
    proto: http
    addr: n8n:5678
```

3. **Start the containers:**
```bash
docker compose up -d
```

4. **Stop containers:**
```bash
docker compose down
```

5. **Check logs (ngrok URL):**
```bash
docker compose logs -f
```

### 🌍 Access Points

N8N → http://localhost:5678 or verifying the Ngrok container logs/dashboard on https://dashboard.ngrok.com/endpoints
Waha → http://localhost:3000
Postgres → Port 5432
Redis → Port 6379
Ngrok → Displays public URL in logs

### 📌 Restart from scratch
```
docker compose down -v
docker compose up -d --build
```
