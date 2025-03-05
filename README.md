# User Authentication System

A secure user authentication system built with Node.js, Express, and MongoDB.

## Features

- User registration and login
- JWT-based authentication
- Password reset functionality
- Input validation
- Error handling
- Secure password hashing

## Prerequisites

- Node.js
- MongoDB
- SMTP server credentials (for password reset functionality)

## Setup

1. Install dependencies:
   ```bash
   npm install
   ```

2. Configure environment variables:
   - Copy `.env.example` to `.env`
   - Update the values in `.env` with your configuration

3. Start MongoDB server

4. Run the application:
   ```bash
   npm run dev
   ```

## API Endpoints

- POST `/register` - Register a new user
- POST `/login` - Login user
- POST `/forgot-password` - Request password reset
- POST `/reset-password/:token` - Reset password
- GET `/me` - Get current user (protected route)

## Security Features

- Password hashing using bcrypt
- JWT for authentication
- Input validation using express-validator
- Secure password reset flow
- Protection against common vulnerabilities
