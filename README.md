Expense Tracker

Overview

The Expense Tracker application allows users to manage their expenses and view them in a dashboard with visual representations using charts. It includes functionality for user registration, login, and expense management.

Table of Contents

1. [Prerequisites](prerequisites)
2. [Installation](installation)
3. [Configuration](configuration)
4. [Running the Application](running-the-application)
5. [Endpoints](endpoints)
6. [Troubleshooting](troubleshooting)
7. [License](license)

Prerequisites

- Node.js: [Download and install Node.js](https://nodejs.org/)
- MySQL: [Download and install MySQL](https://dev.mysql.com/downloads/mysql/)
- npm: Comes with Node.js installation

Installation

1. Clone the Repository
   git clone
   cd

2. Install Dependencies

   Install the necessary Node.js modules:

   npm install

3. Set Up the Database

   - Ensure MySQL is installed and running.
   - Create a new database for the application or use an existing one.

   CREATE SCHEMA schema_name;

   USE schema_name;

   - -- Create the 'categories' table if it does not already exist
CREATE TABLE IF NOT EXISTS categories (
  id INT AUTO_INCREMENT PRIMARY KEY,
  name VARCHAR(255) UNIQUE NOT NULL
);

-- Create the 'users' table if it does not already exist
CREATE TABLE IF NOT EXISTS users (
  id INT AUTO_INCREMENT PRIMARY KEY, 
  email VARCHAR(255) UNIQUE NOT NULL, 
  username VARCHAR(255) UNIQUE NOT NULL, 
  password VARCHAR(255) NOT NULL,
  createdAt TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Create the 'expenses' table if it does not already exist
CREATE TABLE IF NOT EXISTS expenses (
  id INT AUTO_INCREMENT PRIMARY KEY,
  userId INT,
  categoryId INT,
  amount DECIMAL(10, 2),
  date  DATE,
  createdAt TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  FOREIGN KEY (userId) REFERENCES users(id),
  FOREIGN KEY (categoryId) REFERENCES categories(id)
);


   Database Configuration:

   - Copy the example environment file and update the database credentials:
   - Edit .env file with your database credentials:

     DATABASE_HOST=localhost
     DATABASE_USER=root
     DATABASE_PASSWORD=your_password
     DATABASE=expense_tracker
     SESSION_SECRET=your_session_secret

   - Create the database and tables by running the SQL commands provided.

Configuration

1. Environment Variables

   The application relies on environment variables for configuration. Ensure you have a .env file in the root directory with the following variables:

   DATABASE_HOST=your_database_host
   DATABASE_USER=your_database_user
   DATABASE_PASSWORD=your_database_password
   DATABASE=your_database_name
   SESSION_SECRET=your_session_secret

2. Static Files

Place your static HTML, CSS, and JavaScript files in the public directory. Ensure that home.html, login.html, register.html, and dashboard.html are present.

Running the Application

1. Start the Server

   Run the following command to start the server:
   npm start

   By default, the server will start on [http://localhost:3000](http://localhost:4000).

2. Access the Application

   - Home Page: [http://localhost:3000/](http://localhost:4000/)
   - Login Page: [http://localhost:3000/login](http://localhost:4000/login)
   - Registration Page: [http://localhost:3000/register](http://localhost:4000/register)
   - Dashboard Page: [http://localhost:3000/dashboard](http://localhost:4000/dashboard)

Endpoints

- POST /login: Authenticate a user and start a session.
- POST /register: Register a new user.
- POST /expense: Add a new expense.
- DELETE /expense/:id: Delete an existing expense.
- GET /categories: Fetch all expense categories.
- POST /logout: Log out the current user.


Pitch Deck Link:
https://gamma.app/docs/ExpenseTrackr-Master-Your-Finances-with-Ease-2yqqp3dwzkqpyuy?mode=present#card-u6k1kjkdcmpphhg

Troubleshooting

- 404 Errors: Ensure the path in your HTML links is correct. They should point to the root (e.g., <a href="/">Home</a>).
- Database Connection Issues: Verify your .env file for correct database credentials and ensure MySQL is running.
- Session Issues: Check if cookies are enabled in your browser and ensure the session configuration is correct.

License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
