# Task Manager Backend

A RESTful API backend for the Task Manager application built with Node.js, Express, and MongoDB.

## Features

- User authentication with JWT
- CRUD operations for tasks
- Task priority and status management
- MongoDB database integration
- Input validation
- Error handling

## Tech Stack

- Node.js
- Express.js
- MongoDB with Mongoose
- JSON Web Tokens (JWT)
- bcryptjs for password hashing
- express-validator for input validation
- cors for cross-origin resource sharing
- dotenv for environment variables

## Prerequisites

- Node.js (v14+ recommended)
- MongoDB installed locally or MongoDB Atlas account
- npm or yarn package manager

## Installation

1. Clone the repository:
```bash
git clone https://github.com/FortuneUmubyeyi/TaskManager-BackEnd.git
cd TaskManager-BackEnd
```

2. Install dependencies:
```bash
npm install
```

3. Create a `.env` file in the root directory:
```env
PORT=5000
MONGODB_URI=mongodb://localhost:27017/task-manager
JWT_SECRET=your_jwt_secret_key
```

Note: Replace `your_jwt_secret_key` with a secure secret key and update the MongoDB URI if using Atlas.

## Running the Application

### Development Mode
```bash
npm run dev
```

### Production Mode
```bash
npm start
```

## API Endpoints

### Authentication
- POST `/api/auth/register` - Register a new user
  - Required fields: username, email, password
- POST `/api/auth/login` - Login user
  - Required fields: email, password
- GET `/api/auth/user` - Get authenticated user info
  - Requires: Authentication token

### Tasks
- GET `/api/tasks` - Get all tasks for authenticated user
  - Requires: Authentication token
- POST `/api/tasks` - Create a new task
  - Requires: Authentication token
  - Required fields: title
  - Optional fields: description, priority, status
- PUT `/api/tasks/:id` - Update a task
  - Requires: Authentication token
  - Updateable fields: title, description, priority, status
- DELETE `/api/tasks/:id` - Delete a task
  - Requires: Authentication token

## Response Format

### Success Response
```json
{
  "data": {
    // Response data
  }
}
```

### Error Response
```json
{
  "message": "Error message"
}
```

## Authentication

The API uses JWT tokens for authentication. Include the token in the request header:
```
x-auth-token: <your-jwt-token>
```

## Error Handling

The API implements proper error handling for:
- Validation errors
- Authentication errors
- Database errors
- Not found errors
- Server errors

## Development

### Directory Structure
```
├── config/
├── middleware/
│   └── auth.js
├── models/
│   ├── User.js
│   └── Task.js
├── routes/
│   ├── auth.js
│   └── tasks.js
├── .env
├── .gitignore
├── package.json
└── server.js
```
