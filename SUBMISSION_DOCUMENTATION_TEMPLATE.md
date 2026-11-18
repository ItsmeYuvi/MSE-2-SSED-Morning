# MSE-2 Software Engineering & DevOps Practical Examination Documentation
**Document Name:** `ROLL_NUMBER_STUDENT_NAME.pdf`

---

## 1. Student Information

- **Full Name:** [Your Full Name, e.g., Yuvraj Singh]
- **University Roll Number:** [Your University Roll Number]
- **Section:** [Your Section, e.g., AIML-B]
- **Branch:** [Your Branch, e.g., Artificial Intelligence & Machine Learning]
- **GitHub Username:** ItsmeYuvi

---

## 2. GitHub Submission Details

- **GitHub Repository URL (Personal Fork):** https://github.com/ItsmeYuvi/MSE-2-SSED-Morning
- **GitHub Branch Used for Implementation:** `main`
- **Upstream Starter Repository:** https://github.com/atindeRR/MSE-2-SSED-Morning

---

## 3. Docker Hub Details

- **Docker Hub Username:** [Your Docker Hub Username, e.g., ItsmeYuvi]
- **Frontend Docker Image URL:** https://hub.docker.com/r/ItsmeYuvi/taskflow-frontend (or `ItsmeYuvi/frontend`)
- **Backend Docker Image URL:** https://hub.docker.com/r/ItsmeYuvi/taskflow-backend (or `ItsmeYuvi/backend`)

---

## 4. Container Architecture & Implementation Summary

- **Frontend (`frontend/Dockerfile`):** Multi-stage Docker build utilizing `node:20-alpine` for building React/Vite assets and `nginx:1.27-alpine` for production serving on port 80 (mapped to 8080). Configured reverse proxy for `/api/` and `/health` to `http://backend:3000`.
- **Backend (`backend/Dockerfile`):** Production Node.js 20 container running as non-root user (`USER 1000`) with optimized `npm ci --omit=dev` layer caching, listening on port 3000.
- **Database (`postgres:16-alpine`):** PostgreSQL database with named volume persistence (`postgres_data`) and automatic initialization (`init.sql`).
- **Cache (`redis:7-alpine`):** In-memory cache for API task endpoints with health-checked readiness.
- **Docker Compose:** Complete orchestration defined in `docker-compose.yml` (build-enabled) and `docker-compose.deploy.yml` (pure image pull).

---

## 5. CI/CD Execution Evidence & Screenshots

*(Paste the actual screenshots captured from your GitHub Actions workflow runs and local/cloud deployment here)*

### 5.1 GitHub Actions Workflow Overview
*(Screenshot of the completed GitHub Actions workflow run in your GitHub repository)*
- **Workflow Run URL:** [Insert GitHub Actions Run URL]

### 5.2 Docker Hub Authentication & Buildx Setup
*(Screenshot showing successful Docker Hub authentication step in GitHub Actions)*

### 5.3 Backend Docker Image Build and Publishing
*(Screenshot showing the backend Docker build and push step completing successfully)*

### 5.4 Frontend Docker Image Build and Publishing
*(Screenshot showing the frontend Docker build and push step completing successfully)*

### 5.5 Docker Compose Image Pull
*(Screenshot showing `docker compose -f docker-compose.deploy.yml pull` in the Actions runner)*

### 5.6 Application Deployment
*(Screenshot showing `docker compose -f docker-compose.deploy.yml up -d` starting all 4 services)*

### 5.7 Backend Health Check Verification
*(Screenshot showing `curl http://localhost:3000/health` returning `{"status":"ok","postgres":"ok","redis":"ok"}`)*

### 5.8 Frontend Accessibility Verification
*(Screenshot showing `curl http://localhost:8080/` and browser access to `http://localhost:8080`)*

### 5.9 Automated API Test Suite Execution
*(Screenshot showing all 12 Jest test cases passing against the deployed stack)*

### 5.10 Final Successful CI/CD Pipeline Status
*(Screenshot showing green checkmark / 100% successful completion of all CD workflow stages)*

---

## 6. Declaration

"I hereby declare that the submitted Docker implementation is my own work. I have successfully executed and verified the required CI/CD pipeline stages, published the Docker images to my Docker Hub account, and tested the application deployment."

---
**Date:** [Insert Date]  
**Signature / Student Name:** [Insert Student Name]
