# REST API – Todo Application

A backend REST API for a Todo application, built with Node.js, Express, and MySQL.
The API allows users to register, authenticate, and manage their own todos and categories with full CRUD functionality.

This project was originally developed as part of a course assessment.

## Project Overview
The application provides a secure REST API for managing todo items. Each user can create, update, and soft-delete their own todos, organize them into categories, and track progress through predefined statuses.

All protected routes require authentication using JWT, and all responses follow a consistent JSON structure. Only the backend is implemented; no frontend is included.


## Key Features
- User registration and login
- JWT-based authentication
- Todo management (create, read, update, soft delete)
- Category management per user
- Predefined todo statuses:
  - Not Started
  - Started
  - Completed
  - Deleted
- Soft deletion using status flags
- Validation and error handling on all endpoints
- Swagger API documentation
- Automated API testing


## Tech Stack
- Node.js
- Express
- MySQL
- Sequelize ORM
- JWT Authentication
- dotenv
- Swagger
- Jest
- Supertest


## Database Design
The application uses a relational MySQL database named `myTodo`.

Main entities include:
- users
- todos
- categories
- statuses

Status records are automatically inserted on first application startup and are
protected against duplication.

Each user has their own categories and todos. A category cannot be deleted if it
is assigned to an existing todo.


## Authentication & Security
- Passwords are hashed before being stored in the database
- JWT tokens are generated on login
- User identity is derived exclusively from the JWT token
- All routes require authentication except:
  - Sign up
  - Login

No user-identifiable information is passed directly in request bodies for
protected routes.


## API Response Format
All endpoints return JSON responses using a consistent structure.

Success response:
{
  "status": "success",
  "data": {
    "statusCode": 200,
    "result": "..."
  }
}

Failure response:
{
  "status": "fail",
  "data": {
    "statusCode": 400,
    "result": "..."
  }
}

Error response:
{
  "status": "error",
  "result": "..."
}

## Testing
Automated tests are implemented using Jest and Supertest, covering scenarios such
as:
- Successful login
- Accessing protected routes with a valid JWT
- Creating and deleting todo items
- Rejecting requests without a token
- Rejecting requests with an invalid token

## API Documentation
Swagger documentation is available when the server is running.

Access it at:
http://localhost:3000/doc


## Running the Project Locally

1. Copy `.env.example` to `.env` and edit the database credentials
2. Install dependencies:
   npm install
3. Start MySQL and create the database `myTodo`
   (or allow Sequelize to create it, depending on privileges)
4. Start the server:
   npm run dev
5. On first run, the server will sync models and seed todo statuses automatically

The API runs on:
http://localhost:3000


## What This Project Demonstrates
- RESTful API design
- Secure authentication with JWT
- Relational database modeling
- Sequelize ORM usage
- Middleware-based authorization
- Error handling and validation
- Automated backend testing
- API documentation with Swagger

## Possible Improvements
- Add refresh tokens for improved session handling
- Implement pagination for large todo lists
- Add role-based permissions
- Expand automated test coverage
