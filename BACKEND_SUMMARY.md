# Gram Swasthya Connect – Backend API Summary

## Overview
This is a NestJS backend for Gram Swasthya Connect, a rural telemedicine platform. It uses MongoDB Atlas for data storage, supports modular API design, and is ready for frontend consumption.

---

## Tech Stack
- **Framework:** NestJS (TypeScript)
- **Database:** MongoDB Atlas (Mongoose ODM)
- **API Docs:** Swagger (OpenAPI) at `/api/docs`
- **File Uploads:** Multer middleware
- **Validation:** class-validator, class-transformer

---

## Authentication & Roles
- (Pluggable) Firebase Auth planned for identity verification
- Roles: ASHA, Doctor, Admin, Patient (role-based access, to be implemented)

---

## Core API Modules & Endpoints

### Auth
- `POST /auth/login` — Verify Firebase idToken and return user info
- `POST /auth/refresh` — Refresh access token
- `GET /auth/me` — Get current authenticated user

### Users
- `GET /users` — List all users (admin only)
- `GET /users/:id` — Get user by ID
- `POST /users` — Create new user
- `PUT /users/:id` — Update user
- `DELETE /users/:id` — Delete user

### Consultations
- `GET /consultations` — List consultations (filtered by role)
- `GET /consultations/:id` — Get consultation details
- `POST /consultations` — Create new consultation
- `PUT /consultations/:id` — Update consultation
- `DELETE /consultations/:id` — Cancel consultation

### Chat
- `WS /chat` — WebSocket gateway for real-time messaging (to be implemented)
- `POST /chat/send` — Send message via REST fallback
- `GET /chat/history/:roomId` — Get chat history for a room

### Reports
- `POST /reports/upload` — Upload medical report (image/PDF)
- `GET /reports/:id` — View report
- `DELETE /reports/:id` — Delete report

### Availability
- `POST /availability` — Doctor sets available slots
- `GET /availability/:doctorId` — View doctor’s slots
- `POST /availability/book` — ASHA books a slot

### Notifications
- `POST /notifications/sms` — Send SMS via Twilio (to be implemented)
- `POST /notifications/email` — Send email alert (to be implemented)

### Audit
- `GET /audit` — View system logs (admin only)
- `POST /audit` — Log custom event

### Utility
- `GET /api/docs` — Swagger UI for API documentation
- `GET /health` — Health check endpoint

---

## Data Models (MongoDB Collections)
- **reports** — Stores uploaded medical report metadata (filename, mimetype, size, url)
- (Other collections will be created as you define schemas for users, consultations, etc.)

---

## Usage Notes
- All endpoints are documented and testable via Swagger at `/api/docs`.
- File upload endpoints expect `multipart/form-data`.
- DTOs and validation are in place for clean API contracts.
- Environment variables for MongoDB are stored in `.env` (`MONGODB_URI`, `MONGODB_DBNAME`).

---

## Next Steps for Frontend
- Use the Swagger docs to generate API clients or test endpoints.
- Implement authentication and role-based access as needed.
- Expand schemas and endpoints as your frontend requirements grow.

---

For any further backend expansion (new modules, endpoints, or integrations), update this summary and the Swagger docs accordingly.
