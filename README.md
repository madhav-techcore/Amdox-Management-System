🚀 Amdox Task Management System

A full-stack task management application built using Java Spring Boot and React that helps teams organize tasks, track progress, and collaborate efficiently.
The system provides secure authentication, role-based access control, Kanban workflow management, and real-time collaboration tools.

📌 Project Overview

The Amdox Task Management System enables teams to manage tasks in a structured workflow. Users can create tasks, assign them to team members, track deadlines, and collaborate through comments.

The application follows a modern full-stack architecture:

Frontend: React for interactive user interface

Backend: Spring Boot REST APIs

Database: MySQL

Security: JWT-based authentication

🏗️ Technology Stack
Backend

Java 17

Spring Boot 3

Spring Security

JWT Authentication

Spring Data JPA (Hibernate)

MySQL Database

Maven

Lombok

Frontend

React 18

React Router v6

Bootstrap 5

Axios

JavaScript ES6

✨ Key Features
🔐 Secure Authentication

User Registration & Login

JWT Token-based Authentication

Password Encryption using BCrypt

👥 Role-Based Access Control
Role	Permissions
ADMIN	Full system access
EDITOR	Create and update own tasks
VIEWER	Read-only access
📋 Task Management

Create, Update, Delete tasks

Task priorities (HIGH, MEDIUM, LOW)

Task status tracking (TODO, IN_PROGRESS, DONE)

Task assignment to users

Due date management

📊 Kanban Workflow

Visual Kanban board

Drag & Drop task updates

Color-coded priorities

Real-time task status updates

🤝 Collaboration

Comment system for tasks

Task assignment

Task history tracking

📈 Analytics

Overdue task detection

Task completion reports

User productivity tracking

🗄️ Database Design
Users Table
CREATE TABLE users (
    id BIGINT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(100),
    email VARCHAR(100) UNIQUE,
    password VARCHAR(255),
    role VARCHAR(20),
    active BOOLEAN
);
Tasks Table
CREATE TABLE tasks (
    id BIGINT PRIMARY KEY AUTO_INCREMENT,
    title VARCHAR(100),
    description TEXT,
    priority VARCHAR(20),
    status VARCHAR(20),
    due_date DATE,
    assigned_to BIGINT,
    created_by BIGINT,
    created_at TIMESTAMP,
    updated_at TIMESTAMP,
    FOREIGN KEY (assigned_to) REFERENCES users(id),
    FOREIGN KEY (created_by) REFERENCES users(id)
);
Comments Table
CREATE TABLE comments (
    id BIGINT PRIMARY KEY AUTO_INCREMENT,
    message TEXT,
    task_id BIGINT,
    user_id BIGINT,
    created_at TIMESTAMP,
    FOREIGN KEY (task_id) REFERENCES tasks(id),
    FOREIGN KEY (user_id) REFERENCES users(id)
);
📁 Project Structure
amdox-task-management
│
├── backend
│   ├── controller
│   ├── service
│   ├── repository
│   ├── model
│   ├── dto
│   ├── security
│   └── TaskManagerApplication.java
│
├── frontend
│   ├── pages
│   ├── components
│   ├── services
│   ├── App.js
│   └── index.js
│
├── database-init.sql
└── README.md
⚙️ Setup Instructions
Prerequisites

Install the following:

Java 17+

Node.js

MySQL

Maven

1️⃣ Database Setup
mysql -u root -p
mysql -u root -p < database-init.sql
2️⃣ Backend Setup
cd task-management-backend
mvn clean install
mvn spring-boot:run

Backend runs on:

http://localhost:8080/api
3️⃣ Frontend Setup
cd task-management-frontend
npm install
npm start

Frontend runs on:

http://localhost:3000
📡 API Overview
Authentication APIs
Register
POST /api/auth/register
Login
POST /api/auth/login
Task APIs
GET    /api/tasks
POST   /api/tasks
PUT    /api/tasks/{id}
DELETE /api/tasks/{id}
GET    /api/tasks/overdue/list
Comment APIs
POST   /api/tasks/{taskId}/comments
GET    /api/tasks/{taskId}/comments
DELETE /api/tasks/{taskId}/comments/{commentId}
🌐 Deployment
Backend Deployment

Build the JAR file:

mvn clean package

Run the application:

java -jar task-management-backend-1.0.0.jar

Supported deployment platforms:

AWS EC2

Railway

Render

Frontend Deployment

Build React project:

npm run build

Deploy to:

Netlify

Vercel

💡 Interview Questions
Explain the Architecture

The project follows a three-tier architecture:

Frontend Layer: React UI

Backend Layer: Spring Boot REST APIs

Data Layer: MySQL database

How JWT Authentication Works

User logs in with credentials

Server generates JWT token

Token is stored on client side

Every request sends token in Authorization header

Backend validates token before processing requests

Key Improvements (Future Scope)

Email notifications

File attachments

Real-time updates using WebSocket

Advanced search and filters

Team workspaces

🧪 Test Accounts

Admin

Email: admin@amdox.com
Password: password123

Editor

Email: john@amdox.com
Password: password123

Viewer

Email: jane@amdox.com
Password: password123
📜 License

This project is created for learning and academic purposes.

👨‍💻 Author

Nyathari Madhav
