
# FastAPI Signup and Login System

This repository contains a FastAPI-based user authentication system, including signup, email verification, login, forgot password, and delete user functionalities. The system uses SQLite as the database and bcrypt for password hashing.

## Features

- User Signup with email verification
- User Login with security features like account lockout after multiple failed attempts
- Forgot Password functionality with OTP-based password reset
- Delete user account

## Installation

### Prerequisites

- Python 3.11
- SQLite
- Email id and email id app password details for sending emails

### Steps

1. **Clone the repository:**


2. **Create a virtual environment:**

```bash
python -m venv venv
source venv/bin/activate  # On Windows use `venv\Scripts\activate`
```

3. **Install the required packages:**

```bash
pip install -r requirements.txt
```

4. **Set up the environment variables:**

Create a `.env` file in the project root directory and add your SMTP email credentials:

```plaintext
EMAIL_USER=your_email@example.com
EMAIL_PASSWORD=your_email_password
```



5. **Run the FastAPI application:**

```bash
python3 main.py
```

Your FastAPI application will be available at `http://0.0.0.0:8000`.

## API Endpoints

### Signup

**Endpoint:** `POST /signup/`

**Request Body:**

```json
{
  "username": "newuser",
  "email": "newuser@example.com",
  "password": "SecurePass123!"
}
```

**Response:**

```json
{
  "message": "Signup successful. Please verify your email to complete registration."
}
```

### Verify Email

**Endpoint:** `POST /verify-email/`

**Request Body:**

```json
{
  "email": "newuser@example.com",
  "otp": 123456
}
```

**Response:**

```json
{
  "message": "Email verified successfully. Your account is now active."
}
```

### Login

**Endpoint:** `POST /login/`

**Request Body:**

```json
{
  "username": "newuser",
  "password": "SecurePass123!"
}
```

**Response:**

```json
{
  "message": "Login successful!"
}
```

### Forgot Password

**Endpoint:** `POST /forgot-password/`

**Request Body:**

```json
{
  "username": "newuser",
  "email": "newuser@example.com"
}
```

**Response:**

```json
{
  "message": "OTP sent to your email. Please check your email to reset your password."
}
```

### Reset Password

**Endpoint:** `POST /reset-password/`

**Request Body:**

```json
{
  "username": "newuser",
  "otp": 123456,
  "new_password": "NewSecurePass123!"
}
```

**Response:**

```json
{
  "message": "Your password has been reset successfully. You can now log in with your new password."
}
```

### Delete User

**Endpoint:** `DELETE /delete/`

**Request Body:**

```json
{
  "username": "newuser",
  "password": "SecurePass123!"
}
```

**Response:**

```json
{
  "message": "User deleted successfully."
}
```

## Project Structure

```plaintext
.
├── .env
├── app.py
├── requirements.txt
└── user_data.db
```

- `.env`: Contains environment variables for SMTP email credentials.
- `app.py`: Main FastAPI application file.
- `requirements.txt`: Python dependencies.
- `user_data.db`: SQLite database file.

## Security Considerations

- Passwords are hashed using bcrypt before being stored in the database.
- OTPs are generated and sent via email for account verification and password reset.
- Account lockout mechanism is implemented to prevent brute-force attacks.

## Contribution

Feel free to open issues or submit pull requests for any improvements or bug fixes.

## Support

For support, email uniyarakapil@gmail.com


---

