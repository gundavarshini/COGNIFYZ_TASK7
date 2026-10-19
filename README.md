
# SecureHub – Database Integration and User Authentication

A full-stack web application developed using Node.js, Express.js, MySQL, HTML, CSS, and JavaScript to implement secure user registration, login, database integration, and session-based authentication.

## Internship Details

| Field              | Details                                      |
| ------------------ | -------------------------------------------- |
| Organization       | Cognifyz Technologies                        |
| Internship Program | Full Stack Development Internship            |
| Internship Status  | Successfully Completed                       |
| Level              | Level 3 – Advanced                           |
| Task Number        | Task 6                                       |
| Task Title         | Database Integration and User Authentication |
| Project Name       | SecureHub – User Authentication System       |


## Project Overview

SecureHub is a web-based authentication system designed to demonstrate secure user account management and database integration.

The application enables users to create accounts, authenticate using their credentials, and access a personalized dashboard. MySQL is used to store user information, while Express.js manages authentication APIs and protected resources.

The project demonstrates essential full-stack development concepts, including REST API development, relational database connectivity, password hashing, session management, input validation, and authorization middleware.

## Objectives

- Integrate a relational database using MySQL.
  
- Implement user registration and login functionality.
  
- Store passwords securely using bcrypt hashing.
  
- Manage authenticated users through server-side sessions.
  
- Protect API endpoints using authorization middleware.
  
- Retrieve and display authenticated user profile information.
  
- Develop a responsive and professional user interface.


## Key Features

- **User Registration:** Create an account using a name, email address, and password.
  
- **User Authentication:** Validate login credentials securely.
  
- **Password Security:** Hash passwords before storing them in the database.
  
- **MySQL Integration:** Store and retrieve user account information.
  
- **Session Management:** Maintain authenticated sessions using server-side session storage.
  
- **Protected API Endpoints:** Restrict private profile access to authenticated users.
  
- **Personalized Dashboard:** Display the logged-in user's name, email, and user ID.
  
- **Logout Functionality:** Destroy the current session when the user signs out.
  
- **Input Validation:** Validate required fields, email format, password length, and password confirmation.
  
- **Responsive Interface:** Provide a clean interface for desktop and mobile screens.
  
- **Health Check API:** Verify application server and database connectivity.

## Technology Stack

| Technology            | Purpose                                             |
| --------------------- | --------------------------------------------------- |
| HTML5                 | Structure of the authentication interface           |
| CSS3                  | Responsive styling and user interface design        |
| JavaScript            | Frontend interactions and API communication         |
| Node.js               | Server-side JavaScript runtime                      |
| Express.js            | Backend framework and REST API routing              |
| MySQL                 | Relational database for user information            |
| MySQL2                | Database connectivity and parameterized SQL queries |
| bcryptjs              | Password hashing and verification                   |
| express-session       | Server-side session management                      |
| express-mysql-session | Persistent session storage in MySQL                 |
| dotenv                | Environment variable configuration                  |
| Nodemon               | Automatic server restart during development         |


## Project Structure


Level3_Task6/
│
├── config/
│   └── db.js
│
├── controllers/
│   └── authController.js
│
├── middleware/
│   └── authMiddleware.js
│
├── models/
│   └── User.js
│
├── public/
│   ├── index.html
│   ├── css/
│   │   └── style.css
│   └── js/
│       └── app.js
│
├── routes/
│   ├── authRoutes.js
│   └── userRoutes.js
│
├── .env
├── .gitignore
├── package.json
├── package-lock.json
└── server.js


## Database Design

**Database Name:** `cognifyz_auth`

The application uses a MySQL table named `users` to manage registered accounts.

## Database Design

| Column       | Data Type      | Description                     |
| ------------ | -------------- | ------------------------------- |
| `id`         | `INT`          | Primary key with auto-increment |
| `full_name`  | `VARCHAR(100)` | Registered user's full name     |
| `email`      | `VARCHAR(150)` | Unique email address            |
| `password`   | `VARCHAR(255)` | Bcrypt-hashed password          |
| `created_at` | `TIMESTAMP`    | Account creation date and time  |

The application also uses a MySQL-managed session table to persist session information.

## API Endpoints

| HTTP Method | Endpoint             | Description                                |
| ----------- | -------------------- | ------------------------------------------ |
| `GET`       | `/api/health`        | Checks server and database connectivity    |
| `POST`      | `/api/auth/register` | Registers a new user                       |
| `POST`      | `/api/auth/login`    | Authenticates user credentials             |
| `POST`      | `/api/auth/logout`   | Destroys the current authenticated session |
| `GET`       | `/api/users/me`      | Retrieves the authenticated user's profile |


### Authentication and Authorization

- Registration validates user input and checks for duplicate email addresses.
  
- Login verifies the submitted password against the stored bcrypt hash.
  
- Successful authentication creates a server-side session.
  
- Protected routes verify the authenticated session before returning private data.
  
- Unauthenticated requests to protected endpoints receive an HTTP `401 Unauthorized` response.

## Installation and Setup

### Prerequisites

Install the following software:

- Node.js
  
- MySQL Server
  
- MySQL Workbench
  
- Visual Studio Code

### Step 1: Clone the Repository


git clone <github.com/gundavarshini>

cd Level3_Task6


### Step 2: Install Dependencies


npm install


### Step 3: Create the MySQL Database

Execute the following SQL commands in MySQL Workbench:


CREATE DATABASE IF NOT EXISTS cognifyz_auth;

USE cognifyz_auth;

CREATE TABLE IF NOT EXISTS users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    full_name VARCHAR(100) NOT NULL,
    email VARCHAR(150) NOT NULL UNIQUE,
    password VARCHAR(255) NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);


The session library creates its required session table automatically.

### Step 4: Configure Environment Variables

Create a `.env` file in the project root:


PORT=5000
DB_HOST=localhost
DB_PORT=3306
DB_USER=root
DB_PASSWORD=your_mysql_password
DB_NAME=cognifyz_auth
SESSION_SECRET=your_long_random_secret
NODE_ENV=development


Replace the database password and session secret with your own values.

**Security:** Never commit the `.env` file or actual credentials to GitHub.

### Step 5: Start the Application

For development:

npm run dev


For normal execution:

npm start


### Step 6: Open the Application

Visit the following URLs in your browser:

- Application: http://localhost:5000
  
- Health Check: http://localhost:5000/api/health

## Application Workflow

1. The user opens the SecureHub authentication page.

2. A new user registers with the required account details.

3. The backend validates the input and hashes the password.

4. User information is stored in the MySQL database.

5. The user signs in with the registered credentials.

6. The backend verifies the password and establishes a session.

7. The authenticated user accesses the personalized dashboard.

8. The user signs out, and the server destroys the session.

## Security Practices

- Passwords are hashed using bcrypt rather than stored in plain text.
  
- Parameterized SQL queries help prevent SQL injection.
  
- Protected API endpoints require an authenticated session.
  
- Session cookies use HttpOnly and SameSite settings.
  
- Environment variables keep database credentials and session secrets outside the source code.
  
- Profile queries return only the information needed by the frontend.
  
- Server-side validation supplements browser-side validation.

For production deployment, HTTPS, CSRF protection, login rate limiting, and production-appropriate session cookie settings should also be configured.

## Testing and Verification

The following test cases can be used to verify the functionality of the SecureHub – User Authentication System.

| Test Case                          | Expected Result                         |
| ---------------------------------- | --------------------------------------- |
| Register with valid details        | Account created successfully            |
| Register with an existing email    | Duplicate account rejected              |
| Register with mismatched passwords | Validation error displayed              |
| Sign in with valid credentials     | User authenticated successfully         |
| Sign in with invalid credentials   | Authentication rejected                 |
| Access profile without login       | HTTP `401 Unauthorized`                 |
| Access profile after login         | Authenticated user information returned |
| Sign out                           | Session destroyed successfully          |
| Check application health           | Server and database status returned     |


## Screenshots

Add screenshots of the actual running application to the `screenshots/` directory to demonstrate the functionality of the SecureHub – User Authentication System.

| Screenshot               | Description                                     |
| ------------------------ | ----------------------------------------------- |
| Authentication Interface | Registration and login page                     |
| User Dashboard           | Authenticated profile dashboard                 |
| Registration Success     | Successful account creation                     |
| MySQL Database           | Registered user record with hashed password     |
| API Testing              | Authentication and protected endpoint responses |

Example Markdown for displaying your dashboard screenshot after adding the image file:

<img width="1460" height="719" alt="image" src="https://github.com/user-attachments/assets/c99fea18-4585-40b2-b664-1d35270eb21e" />

<img width="1469" height="720" alt="image" src="https://github.com/user-attachments/assets/51033b3e-85d2-496f-9c64-bc8dea9b5190" />


<img width="1488" height="725" alt="image" src="https://github.com/user-attachments/assets/0d52d75d-16d3-448f-9a8b-c9d0657d4836" />


<img width="1476" height="678" alt="image" src="https://github.com/user-attachments/assets/e0a54d2d-400f-42cb-b4a6-8be16b13f933" />



## Learning Outcomes

Through this project, I gained practical experience in:

- Integrating MySQL with a Node.js application.
  
- Building RESTful APIs using Express.js.
  
- Implementing user registration and login.
  
- Applying password hashing and verification.
  
- Managing server-side authentication sessions.
  
- Securing private endpoints with authorization middleware.
  
- Organizing a full-stack application using a modular project structure.
  
- Handling backend validation and database errors.

## Conclusion

SecureHub demonstrates the integration of a relational database with a full-stack web application and the implementation of essential user authentication and authorization mechanisms.

The project reinforces practical skills in backend development, SQL database operations, API security, and responsive frontend development.

## Internship Acknowledgment

Developed as part of the **Cognifyz Technologies Full Stack Development Internship – Level 3, Task 6: Database Integration and User Authentication**.

This project demonstrates the practical application of full-stack development concepts and secure data-handling practices.
