# Task Management Application

A full-stack task management system built with the MERN stack (MongoDB, Express, React, Node.js) using TypeScript.

**Frontend**: https://kazam-fe-cyan.vercel.app/



## Features

- **User Authentication**
  - JWT-based authentication
  - Password hashing with bcrypt
  - Protected routes for secure access

- **Task Management**
  - Create, Read, Update, Delete tasks
  - Mark tasks as completed/pending
  - Filter and search tasks by status

- **Additional Features**
  - User registration and login
  - User dashboard with task management
  - Real-time updates on task status
  - Input validation with Joi for secure and accurate data entry

- **Technical Features**
  - RESTful API backend
  - Context API for state management in the frontend
  - Responsive UI with Tailwind CSS
  - Type-safe codebase with TypeScript

## Tech Stack

### **Frontend:**
- React + TypeScript
- React Context API for state management
- React Router
- Axios for API calls
- Tailwind CSS for responsive UI

### **Backend:**
- Node.js + Express + TypeScript
- MongoDB + Mongoose
- JWT Authentication for user security
- Bcrypt for password hashing
- Joi for input validation
# Task Management API Documentation

## Base URL
```
https://kazam-backend-8uil.onrender.com
```

## Authentication
Most endpoints require JWT authentication. Include the token in the Authorization header:
```
Authorization: Bearer <JWT_Token_Here>
```

## Endpoints

### Authentication

#### Register User
Create a new user account.

- **URL:** `/api/auth/register`
- **Method:** `POST`
- **Content-Type:** `application/json`

**Request Body:**
```json
{
    "email": "testmail@gmail.com",
    "password": "1234",
    "username": "testuser"
}
```

**Success Response:**
- **Code:** 200
- **Content:**
```json
{
    "message": "User registered successfully"
}
```

#### Login User
Authenticate user and receive JWT token.

- **URL:** `/api/auth/login`
- **Method:** `POST`
- **Content-Type:** `application/json`

**Request Body:**
```json
{
    "email": "testmail@gmail.com",
    "password": "1234"
}
```

**Success Response:**
- **Code:** 200
- **Content:**
```json
{
    "token": "JWT_Token_Here"
}
```

### Tasks

#### Create Task
Create a new task for the authenticated user.

- **URL:** `/api/tasks`
- **Method:** `POST`
- **Authentication:** Required
- **Content-Type:** `application/json`

**Request Body:**
```json
{
    "title": "New Task",
    "description": "Task description",
    "status": "pending",
    "dueDate": "2024-12-31T23:59:59.000Z"
}
```

**Success Response:**
- **Code:** 201
- **Content:**
```json
{
    "id": "task_id",
    "message": "Task created successfully"
}
```

#### Get Tasks
Retrieve all tasks for the authenticated user.

- **URL:** `/api/tasks`
- **Method:** `GET`
- **Authentication:** Required

**Success Response:**
- **Code:** 200
- **Content:**
```json
[
    {
        "id": "task_id",
        "title": "New Task",
        "description": "Task description",
        "status": "pending",
        "dueDate": "2024-12-31T23:59:59.000Z"
    }
]
```

#### Update Task
Update an existing task.

- **URL:** `/api/tasks/:id`
- **Method:** `PATCH`
- **Authentication:** Required
- **Content-Type:** `application/json`

**URL Parameters:**
- `id`: Task ID

**Request Body:**
```json
{
   
    "status": "completed",
 
}
```

**Success Response:**
- **Code:** 200
- **Content:**
```json
{
    "message": "Task updated successfully"
}
```

#### Delete Task
Delete a specific task.

- **URL:** `/api/tasks/:id`
- **Method:** `DELETE`
- **Authentication:** Required

**URL Parameters:**
- `id`: Task ID

**Success Response:**
- **Code:** 200
- **Content:**
```json
{
    "message": "Task deleted successfully"
}
```



## Error Responses
The API uses conventional HTTP response codes to indicate the success or failure of requests:
- `200`: Success
- `201`: Created
- `400`: Bad Request
- `401`: Unauthorized
- `403`: Forbidden
- `404`: Not Found
- `500`: Internal Server Error

Error responses will include a message describing the error:
```json
{
    "error": "Error message description"
}
```

## Testing Tools
You can test the API using:
- [Postman](https://www.postman.com/)



## Notes
- All timestamps are in ISO 8601 format
- Task status can be either "pending" or "completed"
- The JWT token expires after 24 hour

