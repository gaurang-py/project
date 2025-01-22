
# [School Management System API](https://schoolmanagmentsystem.onrender.com/api-docs/#/)

## Overview
The **School Management System API** is a comprehensive backend solution designed to facilitate the management of users, schools, classrooms, and students within an educational environment. It provides user authentication, role-based access control, and CRUD operations for essential entities such as users, schools, and classrooms.

---

## Key Features

### 1. User Management
- Create an **initial super admin** with elevated privileges.
- Authenticate users and generate access tokens using **JWT**.
- Manage user roles, including:
  - **Super Admins**: Full system access.
  - **School Admins**: School-specific access.
  - **Regular Users**: Limited access.
- Full CRUD operations for users.

### 2. School Management
- **Super Admin Privileges**:
  - Create, update, and delete schools.
  - Assign school admins to specific schools.
- Ensure that only super admins can perform school-related operations.

### 3. Classroom Management
- **School Admin Privileges**:
  - Create, list, and delete classrooms within their assigned schools.
- Proper error handling for classroom operations.

### 4. Security Measures
- **JWT Tokens**: Secure user authentication and authorization.
- **Bcrypt**: Password hashing for sensitive data.
- **RBAC (Role-Based Access Control)**: Enforce access restrictions.
- API Rate Limiting (Optional for enhanced security).

### 5. Swagger Documentation
- Comprehensive Swagger documentation for all API endpoints.
- Includes details on:
  - Request/response formats.
  - Required parameters.
  - Possible error scenarios.

---

## Technologies Used
- **Node.js**: Server-side scripting.
- **Express.js**: Framework for building RESTful APIs.
- **MongoDB**: Database for storing users, schools, and classroom data.
- **JWT**: Secure authentication tokens.
- **Bcrypt**: Password hashing.
- **Swagger**: API documentation.

---

## Deployment
The School Management System API is deployed on **Render**, providing reliable and scalable hosting. Access the deployed API and documentation [here](https://schoolmanagmentsystem.onrender.com/api-docs/#/).

---

## API Endpoints

### User Management
| Method | Endpoint | Description | Access |
|--------|----------|-------------|--------|
| `POST` | `/api/user/createInitialSuperAdmin` | Create initial super admin user | Public |
| `POST` | `/api/user/loginUser` | Login using registered user credentials | Public |
| `POST` | `/api/user/addingUser` | Add a user with specified access rights | Super Admin |
| `PUT` | `/api/user/updateUserAccessRights` | Update user access rights | Super Admin |
| `PUT` | `/api/user/updateUser` | Update user information | Authenticated |
| `GET` | `/api/user/getAllUsers` | Get all users | Super Admin |
| `DELETE` | `/api/user/deleteUser` | Delete a user | Super Admin |
| `DELETE` | `/api/user/deleteAllUsers` | Delete all users | Super Admin |

### School Management
| Method | Endpoint | Description | Access |
|--------|----------|-------------|--------|
| `POST` | `/api/school/createSchool` | Create a new school | Super Admin |
| `GET` | `/api/school/getAllSchools` | Get all schools | Super Admin |
| `PUT` | `/api/school/updateSchool` | Update school information | Super Admin |
| `DELETE` | `/api/school/deleteAllSchools` | Delete all schools | Super Admin |

### Classroom Management
| Method | Endpoint | Description | Access |
|--------|----------|-------------|--------|
| `POST` | `/api/classroom/createClassroom` | Create a classroom in a school | School Admin |
| `GET` | `/api/classroom/getAllClassrooms` | Get all classrooms for a school | School Admin |
| `DELETE` | `/api/classroom/deleteClassroom` | Delete a classroom by label | School Admin |

---

## Getting Started

### Prerequisites
- **Node.js** (v14 or later)
- **MongoDB** (local or cloud instance)
- **Git**

### Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/gaurang-py/school-management-system.git
   ```
2. Navigate to the project directory:
   ```bash
   cd school-management-system
   ```
3. Install dependencies:
   ```bash
   npm install
   ```

### Configuration

1. Create a `.env` file in the root directory and configure the following:
   ```env
   # Service Configurations
SERVICE_NAME=school_management_api_gaurang-py
USER_PORT=5111
ADMIN_PORT=5222
ENV=development
# ENV=production

# Redis Configurations
REDIS_URI=redis://127.0.0.1:6379
CORTEX_REDIS=redis://127.0.0.1:6379
CORTEX_PREFIX=school_cortex
OYSTER_REDIS=redis://127.0.0.1:6379
OYSTER_PREFIX=school_oyster
CACHE_REDIS=redis://127.0.0.1:6379
CACHE_PREFIX=school_cache

# MongoDB Configuration
MONGO_URI=mongodb://localhost:27017/school_management_api

# Security
LONG_TOKEN_SECRET=Jm9@kxT2Lh!3qNe7zVwR&EoPs4G5uAi^Df
SHORT_TOKEN_SECRET=R8V!qNxT1Zo@Je&2LuEoKmAi9G7W3Pf
NACL_SECRET=W3X@Y9oK2VqNeLmT7J&R^E4AiG8Pf!ZoDf


   ```

### Running the Application

1. Start the server:
   ```bash
   nodemon index.js
   ```
2. Access the API documentation:
   - Visit: [http://localhost:5111/api-docs](http://localhost:5111/api-docs)


---

## Database Schema
A simplified schema for the application:

### User Schema
```json
{
  "name": "String",
  "email": "String (Unique)",
  "password": "String (Hashed)",
  "role": "String (superadmin | admin | user)"
}
```

### School Schema
```json
{
  "name": "String",
  "address": "String",
  "admin": "User Reference"
}
```

### Classroom Schema
```json
{
  "label": "String",
  "capacity": "Number",
  "school": "School Reference"
}
```
