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

- Node.js (v14 or higher)
- MongoDB Atlas account
- Gmail account (for password reset functionality)

## Installation & Setup

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd user-authentication-system
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Environment Variables**
   Create a `.env` file in the root directory and add the following:
   ```plaintext
   PORT=3000
   MONGODB_URI=your_mongodb_atlas_connection_string
   JWT_SECRET=your_jwt_secret_key
   SMTP_USER=your_gmail@gmail.com
   SMTP_PASS=your_gmail_app_password
   ```
   Replace the placeholders with your actual values:
   - `MONGODB_URI`: Your MongoDB Atlas connection string
   - `JWT_SECRET`: Any secure random string
   - `SMTP_USER`: Your Gmail address
   - `SMTP_PASS`: Your Gmail App Password (not your regular password)

4. **Gmail Setup for Password Reset**
   - Go to your Google Account settings
   - Enable 2-Step Verification
   - Generate an App Password:
     - Go to Security → App passwords
     - Select "Mail" and your device
     - Use the generated password in your `.env` file

## Running the Application

1. **Start the server**
   ```bash
   npm start
   ```
   or for development with auto-reload:
   ```bash
   npm run dev
   ```

2. **The server will start on `http://localhost:3000`**

## API Endpoints

- `POST /register` - Register a new user
  ```json
  {
    "email": "user@example.com",
    "password": "yourpassword"
  }
  ```

- `POST /login` - Login user
  ```json
  {
    "email": "user@example.com",
    "password": "yourpassword"
  }
  ```

- `POST /forgot-password` - Request password reset
  ```json
  {
    "email": "user@example.com"
  }
  ```

- `POST /reset-password/:token` - Reset password
  ```json
  {
    "password": "newpassword"
  }
  ```

- `GET /me` - Get current user (Protected route)
  - Requires Authorization header: `Bearer <your-jwt-token>`

## Testing the API

You can test the API using tools like Postman or curl:

1. **Register a new user**
   ```bash
   curl -X POST http://localhost:3000/register \
   -H "Content-Type: application/json" \
   -d '{"email":"user@example.com","password":"yourpassword"}'
   ```

2. **Login**
   ```bash
   curl -X POST http://localhost:3000/login \
   -H "Content-Type: application/json" \
   -d '{"email":"user@example.com","password":"yourpassword"}'
   ```

3. **Access protected route**
   ```bash
   curl -X GET http://localhost:3000/me \
   -H "Authorization: Bearer your-jwt-token"
   ```

## Security Features

- Password hashing using bcrypt
- JWT for authentication
- Input validation using express-validator
- Secure password reset flow
- Protection against common vulnerabilities

## Deployment

This application can be deployed on various platforms:

**Vercel**
   - Install Vercel CLI: `npm i -g vercel`
   - Run: `vercel`


## Troubleshooting

1. **MongoDB Connection Issues**
   - Ensure your IP is whitelisted in MongoDB Atlas
   - Check if the connection string is correct
   - Verify network connectivity

2. **Email Not Sending**
   - Verify Gmail app password is correct
   - Check if 2-Step Verification is enabled
   - Ensure SMTP settings are correct

3. **JWT Issues**
   - Verify JWT_SECRET is set in .env
   - Check token expiration
   - Ensure token is properly formatted in requests

## Contributing

Feel free to submit issues and enhancement requests.

## License

This project is licensed under the MIT License.
