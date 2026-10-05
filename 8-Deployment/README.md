# 8. Deployment, Infrastructure & Environment Setup

[![Software Engineering](https://img.shields.io/badge/Course-Software%20Engineering%20(UE24CS351AA2)-0052CC.svg)](https://pes.edu)
[![Student SRN](https://img.shields.io/badge/SRN-PES1UG24CS453-orange.svg)](https://github.com/siasimran-magic)
[![Docker](https://img.shields.io/badge/Container-Docker%20%26%20Compose-2496ED.svg)](https://docker.com)
[![CI/CD](https://img.shields.io/badge/Pipeline-GitHub%20Actions-2088FF.svg)](https://github.com/features/actions)

**Project**: Online Internship & Placement Preparation Portal (IPP)  
**Institution**: PES University | Department of Computer Science & Engineering  
**Student SRN**: PES1UG24CS453  

---

## 🏗️ 1. Deployment Topology & Infrastructure Architecture

```mermaid
graph TD
    User["🌐 Internet / Student Users"] -->|HTTPS (Port 443)| Cloudflare["Cloudflare DNS & SSL"]
    Cloudflare --> LB["Nginx Reverse Proxy / Load Balancer"]
    
    subgraph Docker_Compose_Network["Docker Container Network (ipp-network)"]
        LB -->|/api/*| Backend["Node.js / FastAPI Backend (Port 5000)"]
        LB -->|/*| Frontend["React SPA Web Client (Port 3000)"]
        
        Backend --> DB[(PostgreSQL 15 Database - Port 5432)]
        Backend --> Cache[(Redis 7 Cache & Session Store - Port 6379)]
    end

    Backend -->|Store Resumes| CloudS3["AWS S3 / Cloudinary Bucket"]
```

---

## ⚙️ 2. Environment Configuration Matrix

Create a `.env` file in the project root based on the following template:

| Environment Variable | Description | Default / Example Value | Secret / Required |
|:---|:---|:---|:---:|
| `NODE_ENV` | Runtime environment mode | `development` or `production` | Required |
| `PORT` | Backend service listen port | `5000` | Optional |
| `DATABASE_URL` | PostgreSQL connection string | `postgresql://ipp_user:ipp_pass@db:5432/ipp_db` | **Secret / Required** |
| `REDIS_URL` | Redis in-memory cache URI | `redis://cache:6379` | **Secret / Required** |
| `JWT_SECRET` | Secret key for signing auth tokens | `secure_ipp_jwt_token_pes1ug24cs453` | **Secret / Required** |
| `JWT_EXPIRES_IN` | Token validity duration | `24h` | Required |
| `CLIENT_URL` | Allowed CORS frontend origin | `http://localhost:3000` | Required |
| `S3_BUCKET_NAME` | Cloud storage bucket for resumes | `ipp-student-resumes` | Optional in Local Dev |

---

## 🐳 3. Containerization (Docker & Docker Compose)

### Multi-Container Setup (`docker-compose.yml`)
```yaml
version: '3.8'

services:
  web:
    build:
      context: ./frontend
      dockerfile: Dockerfile
    ports:
      - "3000:3000"
    environment:
      - VITE_API_URL=http://localhost:5000/api
    depends_on:
      - api
    networks:
      - ipp-network

  api:
    build:
      context: ./backend
      dockerfile: Dockerfile
    ports:
      - "5000:5000"
    env_file:
      - .env
    depends_on:
      - db
      - cache
    networks:
      - ipp-network

  db:
    image: postgres:15-alpine
    restart: always
    environment:
      POSTGRES_USER: ipp_user
      POSTGRES_PASSWORD: ipp_password
      POSTGRES_DB: ipp_db
    ports:
      - "5432:5432"
    volumes:
      - pgdata:/var/lib/postgresql/data
    networks:
      - ipp-network

  cache:
    image: redis:7-alpine
    restart: always
    ports:
      - "6379:6379"
    networks:
      - ipp-network

volumes:
  pgdata:

networks:
  ipp-network:
    driver: bridge
```

---

## 🚀 4. Step-by-Step Local Deployment Guide

### Option A: Using Docker (Recommended)
1. Ensure Docker Desktop is running.
2. Clone repository and start all services:
   ```bash
   git clone https://github.com/siasimran-magic/InternshipPlacementPortal_IPP.git
   cd InternshipPlacementPortal_IPP
   docker-compose up --build
   ```
3. Open `http://localhost:3000` in your web browser.

### Option B: Bare-Metal Setup
1. **Database & Cache**:
   ```bash
   # Start local PostgreSQL and Redis servers
   sudo service postgresql start
   redis-server
   ```
2. **Backend**:
   ```bash
   cd backend
   npm install
   npm run db:migrate
   npm run dev
   ```
3. **Frontend**:
   ```bash
   cd frontend
   npm install
   npm run dev
   ```

---

## 🔄 5. CI/CD GitHub Actions Pipeline Configuration

The `.github/workflows/ci-cd.yml` automates testing and deployment on every push to `main`:

```yaml
name: CI/CD Pipeline

on:
  push:
    branches: [ main, develop ]
  pull_request:
    branches: [ main ]

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Setup Node.js
        uses: actions/setup-node@v3
        with:
          node-version: 18
      - name: Install Dependencies
        run: npm ci
      - name: Run Lint and Unit Tests
        run: npm test
      - name: Run Coverage Report
        run: npm run test:coverage

  deploy:
    needs: test
    if: github.ref == 'refs/heads/main'
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Build Docker Container
        run: docker build -t ipp-portal:latest .
      - name: Deploy to Cloud (Render / Vercel)
        run: echo "Deploying artifact to staging/production server..."
```
