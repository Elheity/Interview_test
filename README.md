
# Flask E-commerce API

This project is a simple e-commerce API built using Flask, SQLite, SQLAlchemy, and JWT authentication. It includes endpoints for user registration, login, role-based access control (for admin), and interactions with products, orders, and order items.

## Features

- User registration (admin and normal users).
- JWT-based user authentication.
- Admin-only endpoint to ensure restricted access.
- Product, order, and order item management via models.
- Visitor access without authentication.

## Technologies Used

- **Flask**: Micro web framework for building the API.
- **SQLAlchemy**: Object-Relational Mapping (ORM) for database interactions.
- **Flask-Bcrypt**: Password hashing for security.
- **JWT (JSON Web Token)**: Used for user authentication.
- **SQLite**: Lightweight database for development.
- **Flask-Migrate**: Database migration tool to handle schema changes.

## Setup and Installation

1. Clone the repository:

   ```bash
   git clone https://github.com/Elheity/Interview_test.git
   cd Interview_test
   ```

2. Install the required Python packages:

   ```bash
   pip install -r requirements.txt
   ```

3. Initialize the database:

   ```bash
   flask db init
   flask db migrate -m "Initial migration"
   flask db upgrade
   ```

4. Run the Flask development server:

   ```bash
   flask run
   ```

5. The API will be available at `http://127.0.0.1:5000/`.

## API Endpoints

### 1. Register a User

- **URL**: `/register`
- **Method**: `POST`
- **Request Body (JSON)**:
    - Normal User:
      ```json
      {
        "first_name": "user",
        "last_name": "normal",
        "email": "user@gmail.com",
        "phone": "123456789",
        "password": "12345678"
      }
      ```
    - Admin User:
      ```json
      {
        "first_name": "Admin",
        "last_name": "User",
        "email": "admin_user@gmail.com",
        "phone": "123456789",
        "password": "12345678",
        "is_admin": true
      }
      ```

### 2. Login

- **URL**: `/login`
- **Method**: `POST`
- **Request Body (JSON)**:
    ```json
    {
      "email": "user@gmail.com",
      "password": "12345678"
    }
    ```

### 3. Admin-Only Page

- **URL**: `/admin_only_page`
- **Method**: `GET`
- **Authorization**: Requires a valid JWT token from an admin user.

### 4. All Users

- **URL**: `/all_users`
- **Method**: `GET`
- **Authorization**: Requires a valid JWT token from any logged-in user.

### 5. Visitor Page

- **URL**: `/visitor`
- **Method**: `GET`
- **Authorization**: No authorization required.


