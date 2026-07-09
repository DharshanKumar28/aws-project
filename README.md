
# Faculty Portal & Attendance Management System

A full-stack, cloud-optimized web application designed to streamline attendance tracking and automate student communications for university faculty. 

## 📖 Project Overview

Managing student attendance manually is time-consuming and prone to communication delays. This project provides a centralized, secure portal for faculty to record daily student attendance, monitor academic standing, and instantly issue disciplinary or low-attendance warnings directly to students. 

Built as a comprehensive monorepo, this application leverages a modern React frontend and a robust Python REST API, with architectural considerations for scalable deployment on AWS.

## ✨ Key Features

* **Real-Time Attendance Tracking:** Intuitive dashboard for faculty to mark and review student attendance records.
* **Automated Warning System:** Integrated communication module allowing faculty to trigger direct warnings to students falling below attendance thresholds.
* **Role-Based Access Control:** Secure authentication ensuring only authorized faculty and administrative staff can modify academic records.
* **Cloud-Ready Architecture:** Structured for seamless deployment across AWS services (e.g., S3/CloudFront for the frontend, EC2 or API Gateway/Lambda for the backend).

## 🛠️ Technology Stack

**Frontend (Client-Side)**
* **Core:** React 18
* **Build Engine:** Vite (with SWC for high-performance compilation)
* **Package Manager:** pnpm

**Backend (Server-Side API)**
* **Framework:** Python (FastAPI/REST API architecture)
* **Data Validation:** Pydantic (`schemas.py`)
* **Database ORM:** SQLAlchemy (managed via `models.py` and `crud.py`)

## 📂 Repository Architecture

This project is maintained as a monorepo, separating client and server logic while keeping version control centralized:

```text
aws-project/
├── backend/                # Python API service
│   ├── app/                
│   │   ├── crud.py         # Database query operations
│   │   ├── main.py         # ASGI application entry point
│   │   ├── models.py       # Relational database models
│   │   ├── schemas.py      # Request/Response data serialization
│   │   └── util.py         # Shared helper functions
│   └── .env                # Environment configuration
└── frontend/               # React SPA
    ├── src/                # UI components and state management
    ├── package.json        
    ├── pnpm-lock.yaml      
    └── vite.config.js      # Build configuration

```

## 🚀 Local Development Setup

To run this application locally, you will need to initialize both the backend server and the frontend development environment.

### 1. Initializing the Backend

Ensure you have Python 3.8+ installed.

```bash
cd backend
python -m venv venv

# Activate virtual environment
# Windows: venv\Scripts\activate
# Unix/macOS: source venv/bin/activate

pip install -r requirements.txt
python app/main.py 

```

*Note: Ensure your database URI and local environment variables are properly configured in `backend/.env` prior to launch.*

### 2. Initializing the Frontend

Ensure you have Node.js and `pnpm` installed. Open a new terminal session:

```bash
cd frontend
pnpm install
pnpm run dev

```

The frontend application will be served at `http://localhost:5173`.

## ☁️ AWS Deployment Roadmap

This application is designed with cloud-native principles in mind:

1. **Frontend Hosting:** The Vite build output (`dist/`) can be statically hosted on **Amazon S3** and distributed globally via **Amazon CloudFront** for low-latency access.
2. **Backend Hosting:** The Python API can be containerized and deployed to **Amazon ECS**, or run on a traditional **Amazon EC2** instance with an Nginx reverse proxy.
3. **Database:** Relational data management via **Amazon RDS** (PostgreSQL/MySQL) for high availability and automated backups.

---

*Developed as part of a collaborative academic course project.*

