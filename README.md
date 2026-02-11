# Multi-Tenant Project Management API

A production-ready, multi-tenant backend built with Django REST Framework.
This API supports organizations, role-based access control, and isolated project/task management per organization.

**Tech Stack:** Django, DRF, PostgreSQL, JWT, Docker, Gunicorn

---

## 🚀 Features

### 🔐 Authentication

* Custom User model (email-based login)
* JWT authentication (access + refresh tokens)
* Protected endpoints

### 🏢 Multi-Tenancy

* Users can belong to multiple organizations
* Complete data isolation per organization
* Cross-organization access is prevented at the API level

### 👥 Role-Based Access Control

Each organization supports three roles:

| Role   | Permissions                                   |
| ------ | --------------------------------------------- |
| Admin  | Full access (manage members, delete projects) |
| Member | Create/update projects and tasks              |
| Viewer | Read-only access                              |

Custom DRF permission classes enforce these rules.

### 📂 Project Management

* Create and manage projects per organization
* Only organization members can access projects

### ✅ Task Management

* Assign tasks to members
* Status tracking (Todo / In Progress / Done)
* Due dates
* Filtering by status, assignee
* Pagination enabled

### 📊 Advanced Backend Features

* Organization-level data isolation
* Custom permission classes
* Filtering & search (django-filter)
* API pagination
* Audit logging for key actions
* Production-ready settings configuration

---

## 🧠 Architecture Overview

The system is designed around organization-based isolation:

User
→ Membership
→ Organization
→ Project
→ Task

Key design decisions:

* Multi-tenant logic handled at queryset level
* Role-based permissions implemented via custom DRF permission classes
* Custom user model for flexibility and future scalability
* PostgreSQL used for production realism

---

## 🗂 Project Structure

```
apps/
  users/
  organizations/
  projects/
  tasks/

config/
  settings/
    base.py
    dev.py
    prod.py
```

---

## 🐳 Running Locally (Docker)

### 1. Clone repository

```
git clone <your-repo-url>
cd project
```

### 2. Create environment file

```
cp .env.example .env
```

### 3. Run containers

```
docker-compose up --build
```

### 4. Apply migrations

```
docker-compose exec web python manage.py migrate
```

API will be available at:

```
http://localhost:8000/api/
```

---

## 🔑 Authentication Flow

1. Register user
2. Obtain JWT token
3. Include token in Authorization header:

```
Authorization: Bearer <access_token>
```

---

## 📘 API Documentation

Interactive Swagger documentation available at:

```
/api/docs/
```

---

## 🧪 Testing

Run tests:

```
docker-compose exec web pytest
```

Test coverage includes:

* Authentication
* Organization membership
* Role-based restrictions
* Task filtering
* Cross-organization isolation

---

## 🌍 Deployment

Deployed using:

* Gunicorn
* PostgreSQL
* Environment-based settings
* DEBUG disabled in production

Live API: <deployment-link>

---

## 🛡 Security Considerations

* JWT-based authentication
* Organization-level access enforcement
* Role-based permission validation
* Environment variables for sensitive data
* DEBUG disabled in production

---

## 📌 Why This Project?

This project demonstrates:

* Backend architecture design
* Multi-tenant data modeling
* Permission system implementation
* API security best practices
* Production deployment workflow
* Containerized development environment

It is structured to reflect real-world SaaS backend development practices.

---

## 👨‍💻 Author

Ugochukwu Chukwuemeka
Backend Developer – Django / DRF
GitHub: <your-link>
LinkedIn: <your-link>
