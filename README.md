# Real-Time Chat Application
A scalable, production-ready real-time chat application built with the MERN stack, featuring Docker containerization and Kubernetes orchestration.

## Features

- **Real-time Messaging** with Socket.io
- **JWT Authentication** for secure access
- **Profile Management** with image uploads
- **Online/Offline Status** tracking
- **Modern UI** with React & TailwindCSS
- **Kubernetes Deployment** with custom manifests

## Tech Stack

**Backend:** Node.js, Express, MongoDB, Socket.io  
**Frontend:** React, TailwindCSS, DaisyUI, Zustand  
**DevOps:** Docker, Kubernetes, Nginx  
**Auth:** JWT

## Quick Start

### Prerequisites
- Node.js (v14+)
- Docker & Docker Compose
- Kubernetes cluster

### Environment Setup

Create `backend/.env`:
```env
MONGODB_URI=mongodb://mongo:27017/chatapp
JWT_SECRET=your_jwt_secret_key
PORT=5001
```

### Using Docker Compose (Recommended)

```bash
# Clone repository
git clone https://github.com/iemafzalhassan/full-stack_chatApp.git
cd full-stack_chatApp

# Build and run
docker-compose up -d --build
```

Access the app at `http://localhost`

### Manual Docker Setup

```bash
# Create network
docker network create full-stack

# Run MongoDB
docker run -d -p 27017:27017 --name mongo --network=full-stack mongo:latest

# Build & run backend
cd backend
docker build -t chat-backend .
docker run -d --network=full-stack -p 5001:5001 --env-file .env chat-backend

# Build & run frontend
cd ../frontend
docker build -t chat-frontend .
docker run -d --network=full-stack -p 5173:5173 chat-frontend
```

## ☸️ Kubernetes Deployment

This project includes Kubernetes manifests for production deployment.

```bash
# Apply all manifests
kubectl apply -f k8s/

# Check deployment status
kubectl get pods
kubectl get services

# Access the application
kubectl port-forward service/frontend-service 8080:80
```

### K8s Resources Included
- Deployment manifests for frontend, backend, and MongoDB
- Service configurations
- ConfigMaps and Secrets
- Persistent Volume Claims for MongoDB
- Ingress configuration (optional)

## Contributing

Contributions welcome! Please:
1. Fork the repository
2. Create a feature branch
3. Submit a pull request

## Screenshots

![Chat Interface](frontend/public/chat.png)
![Settings](frontend/public/settings.png)

---

**Original Project:** [iemafzalhassan](https://github.com/iemafzalhassan/full-stack_chatApp)