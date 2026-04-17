#  HNG Stage 1 – Simple API Deployment

##  Overview

This project is a minimal REST API built as part of the HNG Internship Stage 1 task.

The goal is not just to build an API, but to demonstrate an understanding of how backend services are deployed in a production-like environment using a reverse proxy and process management.

---

##  Tech Stack

* **Node.js** – runtime environment
* **Express.js** – backend framework
* **Nginx** – reverse proxy
* **PM2** – process manager (keeps app alive)
* **Ubuntu VPS** – hosting environment

---

##  Architecture

Client Request → Nginx (Port 80) → Node App (Port 3000)

* The Node.js app runs on a **private port (3000)**
* Nginx handles **public traffic (port 80)**
* PM2 ensures the service **stays alive after crashes or reboot**

---

##  How to Run Locally

```bash
git clone https://github.com/ahlbertng/my-api.git
cd my-api
npm install
node index.js
```

App runs on:

```
http://localhost:3000
```

---

##  API Endpoints

### GET /

```json
{
  "message": "API is running"
}
```

---

### GET /health

```json
{
  "message": "healthy"
}
```

---

### GET /me

```json
{
  "name": "Ahlbert [Your Full Name]",
  "email": "your-email@example.com",
  "github": "https://github.com/ahlbertng"
}
```

---

##  Live Deployment

Base URL:

```
http://your-server-ip
```

Endpoints:

* `/`
* `/health`
* `/me`

---

##  Deployment Process (What I Actually Did)

1. Built API locally using Express
2. Tested endpoints with curl
3. Pushed code to GitHub
4. Cloned repo on VPS
5. Installed dependencies
6. Ran app on port 3000
7. Configured Nginx reverse proxy
8. Used PM2 to keep service running

---

##  Key Takeaways

* Understanding how services run on ports
* Importance of reverse proxy in production
* Managing long-running processes with PM2
* Separating application logic from infrastructure

---

##  Notes

* All endpoints return **JSON**
* HTTP status code is **200**
* Response time is under **500ms**
* App is not exposed directly — secured via Nginx
