# 🐳 DevOps Assignment: Nginx Reverse Proxy + Docker Compose

This project demonstrates a simple microservices setup using Docker Compose, Nginx as a reverse proxy, and two backend services (Go and Python Flask).

---

## 🚀 Setup Instructions

1. **Clone the repository**
   ```bash
   git clone https://github.com/IamGaurav-jav/DevOpsTask.git
   cd Assignment
   ```

2. **Build and start all services**
   ```bash
   docker-compose up --build
   ```

3. **Access the services via Nginx reverse proxy**
   - Service 1 (Go): [http://localhost:8080/service1/ping](http://localhost:8080/service1/ping), [http://localhost:8080/service1/hello](http://localhost:8080/service1/hello)
   - Service 2 (Flask): [http://localhost:8080/service2/ping](http://localhost:8080/service2/ping), [http://localhost:8080/service2/hello](http://localhost:8080/service2/hello)

---

## 🌐 How Routing Works

- **Nginx** listens on port `8080` and acts as a reverse proxy.
- Requests to `/service1/*` are routed to the Go backend (`service_1`).
- Requests to `/service2/*` are routed to the Python Flask backend (`service_2`).
- All services are accessible via a single port (`8080`).

**Nginx config snippet:**
```nginx
location /service1/ {
    proxy_pass http://service1:8001/;
    # ...headers...
}
location /service2/ {
    proxy_pass http://service2:8002/;
    # ...headers...
}
```

---

## 📝 Bonus Features

- **Health checks:** Both services expose `/ping` endpoints for health checking.
- **Logging:** Nginx logs all incoming requests with timestamp, path, and client info.
- **Modular Docker setup:** Each service and Nginx run in their own containers using bridge networking.

---

## 📂 Project Structure

```
.
├── docker-compose.yml
├── nginx/
│   ├── nginx.conf
│   └── Dockerfile
├── service_1/
│   ├── main.go
│   └── Dockerfile
├── service_2/
│   ├── app.py
│   └── Dockerfile
└── README.md
```

---

## 🧪 Testing

After running `docker-compose up --build`, visit:

- [http://localhost:8080/service1/ping](http://localhost:8080/service1/ping)
- [http://localhost:8080/service1/hello](http://localhost:8080/service1/hello)
- [http://localhost:8080/service2/ping](http://localhost:8080/service2/ping)
- [http://localhost:8080/service2/hello](http://localhost:8080/service2/hello)

You should see JSON responses from each service.

---

## 📜 License

MIT
