🚀 Amdox Task Management System

A full-stack task management application built using Java Spring Boot, React, and MySQL to help teams organize work, track progress, and collaborate efficiently.

The system provides secure authentication, role-based access control, Kanban workflow management, and real-time task collaboration.

📌 Overview

The Amdox Task Management System allows users to create, assign, and monitor tasks through a simple and interactive interface.

Users can:

Create and manage tasks

Assign tasks to team members

Track deadlines and priorities

Collaborate using task comments

Visualize workflow using a Kanban board

🛠 Tech Stack
Backend

Java 17

Spring Boot

Spring Security

JWT Authentication

Spring Data JPA (Hibernate)

MySQL

Maven

Frontend

React 18

React Router

Bootstrap 5

Axios

JavaScript (ES6)

✨ Key Features
🔐 Secure Authentication

User registration and login

JWT token-based authentication

Password encryption using BCrypt

👥 Role-Based Access Control
Role	Access
ADMIN	Full access to system
EDITOR	Create and edit tasks
VIEWER	Read-only access
📋 Task Management

Create, update, and delete tasks

Assign tasks to users

Track deadlines

Manage task priorities and status

Task Priorities

🔴 HIGH

🟡 MEDIUM

🟢 LOW

Task Status

TODO

IN_PROGRESS

DONE

📊 Kanban Workflow

The application includes a Kanban board for visual task management.

Columns include:

📌 TODO

⚙️ IN PROGRESS

✅ DONE

Users can drag and drop tasks between columns to update their progress.

🤝 Collaboration

Add comments to tasks

Assign tasks to team members

Track task activity and updates

🗄 Database Design
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
├── task-management-backend
│   ├── controller
│   ├── service
│   ├── repository
│   ├── model
│   ├── dto
│   ├── security
│   └── TaskManagerApplication.java
│
├── task-management-frontend
│   ├── components
│   ├── pages
│   ├── services
│   ├── App.js
│   └── index.js
│
├── database-init.sql
└── README.md
⚙️ Setup Guide
Requirements

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

Backend runs at:

http://localhost:8080/api
3️⃣ Frontend Setup
cd task-management-frontend
npm install
npm start

Frontend runs at:

http://localhost:3000
📡 API Endpoints
Authentication
POST /api/auth/register
POST /api/auth/login
Tasks
GET    /api/tasks
POST   /api/tasks
PUT    /api/tasks/{id}
DELETE /api/tasks/{id}
GET    /api/tasks/overdue/list
Comments
POST   /api/tasks/{taskId}/comments
GET    /api/tasks/{taskId}/comments
DELETE /api/tasks/{taskId}/comments/{commentId}
🔮 Future Improvements

Email notifications for task updates

File attachments for tasks

Real-time updates using WebSockets

Advanced search and filtering

Analytics dashboard

👨‍💻 Author

Nyathari Madhav
