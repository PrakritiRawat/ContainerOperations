
# ⚓ Microservices Architecture with Docker Swarm

---

## 📌 Introduction
This guide explains how to deploy a **microservices architecture** using **Docker Swarm**:  
- ✅ An **API Gateway** (Flask app)
- ✅ A **Backend Service** (Flask app)

You'll learn to **build**, **deploy**, **scale**, and **update** services in a production-like environment.

---

## 🚀 Step 1: Install Docker & Initialize Docker Swarm

### 1.1 Install Docker
Make sure Docker is installed and running.

Check installation:

```bash
docker --version
```

If Docker is not installed, [download it here](https://www.docker.com/products/docker-desktop).

✅ Ensure **Docker Desktop** is running in the background!

---

### 1.2 Initialize Docker Swarm
Start Docker Swarm mode:

```bash
docker swarm init
```
✅ Your machine becomes the **Swarm Manager**.

---

## 📁 Project Structure

```
microservices-docker-swarm/
│── backend-service/
│    ├── backend.py
│    ├── Dockerfile
│
│── api-gateway/
│    ├── api_gateway.py
│    ├── Dockerfile
│
│── docker-compose.yml
│── README.md
```

---

## 🛠 Step 2: Create the Microservices Code

### 🔹 Backend Service (backend-service/backend.py)

```python
from flask import Flask

app = Flask(__name__)

@app.route('/')
def hello():
    return "Hello from Backend Service!"

if __name__ == "__main__":
    app.run(host='0.0.0.0', port=5000)
```

**Dockerfile (backend-service/Dockerfile):**

```dockerfile
FROM python:3.9-slim
WORKDIR /app
COPY backend.py /app
RUN pip install flask
CMD ["python", "backend.py"]
```

---

### 🔹 API Gateway (api-gateway/api_gateway.py)

```python
from flask import Flask
import requests

app = Flask(__name__)

@app.route('/')
def hello():
    backend_response = requests.get('http://backend-service:5000')
    return f"API Gateway ➔ {backend_response.text}"

if __name__ == "__main__":
    app.run(host='0.0.0.0', port=8080)
```

**Dockerfile (api-gateway/Dockerfile):**

```dockerfile
FROM python:3.9-slim
WORKDIR /app
COPY api_gateway.py /app
RUN pip install flask requests
CMD ["python", "api_gateway.py"]
```

---

## 📦 Step 3: Build Docker Images

```bash
docker build -t backend-service ./backend-service
docker build -t api-gateway ./api-gateway
docker images
```
✅ Now you have two images: `backend-service` and `api-gateway`.

---

## 📜 Step 4: Create Docker Compose File for Swarm

`docker-compose.yml`:

```yaml
version: '3.7'

services:
  backend-service:
    image: backend-service
    deploy:
      replicas: 2
      restart_policy:
        condition: on-failure
    networks:
      - app-network
    ports:
      - "5000:5000"

  api-gateway:
    image: api-gateway
    deploy:
      replicas: 2
      restart_policy:
        condition: on-failure
    networks:
      - app-network
    ports:
      - "8080:8080"
    depends_on:
      - backend-service

networks:
  app-network:
    driver: overlay
```

✅ Important: Docker Swarm **requires `image:` field** instead of `build:` inside `docker-compose.yml`.

---

## 🚀 Step 5: Deploy the Microservices to Docker Swarm

```bash
docker stack deploy -c docker-compose.yml my_microservices
```

✅ The stack will be created with two services running!

---

## 📊 Step 6: Verify the Deployment

Check running services:

```bash
docker stack services my_microservices
```

Check running containers:

```bash
docker ps
```

✅ Your services and tasks will be visible.

---

## 🌐 Step 7: Access the Microservices

Open your browser:

```url
http://localhost:8080
```

✅ You should see:

```
API Gateway ➔ Hello from Backend Service!
```

---

## 🔄 Step 8: Scaling the Services

To scale the backend service to 5 replicas:

```bash
docker service scale my_microservices_backend-service=5
```

✅ Verify again:

```bash
docker stack services my_microservices
```

✅ You’ll see 5 replicas running!

---

## 🛠 Step 9: Updating the Services

After making code changes, rebuild the image:

```bash
docker build -t backend-service ./backend-service
```

Update the running service with the new image:

```bash
docker service update --image backend-service:latest my_microservices_backend-service
```

✅ This will **hot update** the service without downtime!

---

## 🛑 Step 10: Remove the Stack and Exit Swarm

Remove the running stack:

```bash
docker stack rm my_microservices
```

Leave the swarm:

```bash
docker swarm leave --force
```

✅ Your machine exits Swarm Mode safely.

---

# 🎯 Conclusion

✅ You've successfully:
- Built microservices with Docker
- Deployed them with Docker Swarm
- Scaled and updated services dynamically

---

# 🚀 Happy Dockerizing and Scaling Microservices! 🐳✨

---


---
