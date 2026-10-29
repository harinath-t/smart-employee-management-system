# Smart Employee Management System (SEMS)

A full-stack academic project starter based on the internship report topic. It uses React + Bootstrap, Java Spring Boot REST APIs, and MySQL.

## Features included
- Dashboard counts for employees, attendance records, leave requests, and pending leaves
- Employee create, list, update, delete, search, and status
- Attendance entry and history
- Leave request submission and approve/reject workflow
- Responsive dashboard UI
- REST API validation and duplicate-email handling

## Important scope note
This is a functional starter, not a production-ready HR system. It does **not** yet implement JWT authentication, user accounts, or real role-based authorization. The report topic mentions JWT and separate HR/Manager/Employee roles; add those before claiming them as implemented. The current UI is a demo workspace and should be described honestly in a viva.

## Requirements
- Java 17+
- Maven 3.8+ (or use an IDE with Maven support)
- MySQL 8+
- Node.js 18+

## 1. Database
Start MySQL. Create a database manually if preferred:
```sql
CREATE DATABASE semsdb;
```
The backend can also create the database if the MySQL user has permission because the JDBC URL uses `createDatabaseIfNotExist=true`.

## 2. Start backend
From the `backend` directory, edit `src/main/resources/application.properties` or set environment variables:
- `DB_USER` (default: `root`)
- `DB_PASS` (default: empty)

Then run:
```bash
mvn spring-boot:run
```
Backend: `http://localhost:8080`

## 3. Start frontend
Open another terminal:
```bash
cd frontend
npm install
npm run dev
```
Open the local URL printed by Vite, normally `http://localhost:5173`.

## API endpoints
| Method | Endpoint | Purpose |
|---|---|---|
| GET | `/api/dashboard` | Dashboard totals |
| GET | `/api/employees` | List employees |
| GET | `/api/employees/{id}` | Employee details |
| POST | `/api/employees` | Add employee |
| PUT | `/api/employees/{id}` | Update employee |
| DELETE | `/api/employees/{id}` | Delete employee |
| GET | `/api/attendance` | Attendance history |
| POST | `/api/attendance` | Record attendance |
| DELETE | `/api/attendance/{id}` | Delete attendance record |
| GET | `/api/leaves` | List leave requests |
| POST | `/api/leaves` | Submit leave request |
| PATCH | `/api/leaves/{id}/status?value=Approved` | Approve/reject leave |
| DELETE | `/api/leaves/{id}` | Delete leave request |

## Quick test
1. Start MySQL, backend, and frontend.
2. Open Employees and add an employee with a unique email.
3. Confirm the dashboard employee count changes.
4. Record attendance for the employee.
5. Submit a leave request and test Approve/Reject.

## Suggested future improvements
- Spring Security + JWT login
- Role-based authorization for Admin, Manager, and Employee
- Employee-linked attendance and leave records using JPA relationships
- Pagination, CSV/PDF reports, audit log, and automated tests
- Deploy frontend and backend with production environment variables
