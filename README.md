# Flask User Authentication System
This Flask application is a basic user authentication system that demonstrates how to manage user login, logout, and access control for a protected dashboard.
Overview:
---

# Flask User Authentication System

This is a simple Flask application that demonstrates a basic user authentication system. The app allows users to log in, access a protected dashboard, and log out. It uses **Flask-Login** for managing user sessions and **Flask-SQLAlchemy** for database interactions.

## Features

- **User Authentication:**
  - Users can log in with their credentials.
  - The application checks credentials against stored values in an SQLite database.
  - Only authenticated users can access the dashboard.

- **Session Management:**
  - User sessions are managed securely with `Flask-Login`.
  - Users can log out, ending their session.

- **Protected Routes:**
  - The dashboard is a protected route, accessible only to logged-in users.
  - The app uses the `login_required` decorator to restrict access.

## Components

### Database Setup

- **SQLite** is used as the database.
- The `User` model represents the users of the application and contains the following fields:
  - `id`: Unique identifier for each user.
  - `username`: The user's login name.
  - `password`: The user's password (currently stored in plaintext, which should be hashed in production).
  - `role`: User role, which can be used to implement role-based access control.

### User Authentication Flow

1. **Login:**
   - Users can log in via the `/login` route.
   - The app checks the database for a user with the provided username and password.
   - If the credentials are correct, the user is logged in and redirected to the dashboard.

2. **Dashboard:**
   - The `/dashboard` route is protected and accessible only to authenticated users.
   - The logged-in user's information is displayed on the dashboard.

3. **Logout:**
   - Users can log out via the `/logout` route, which ends their session and redirects them to the login page.

### Routes

- **`/login`**: Handles user login. It displays a form for the user to enter their credentials.
- **`/dashboard`**: Protected route that displays the dashboard page for authenticated users.
- **`/logout`**: Logs out the user and ends their session.

### Security Considerations

- **Password Handling**: 
  - Currently, passwords are stored and compared in plaintext. This is not secure for production. Implement password hashing (e.g., using bcrypt) before deploying to a live environment.

- **Session Security**:
  - The `SECRET_KEY` is used to sign session cookies, which helps prevent tampering.

## Installation

1. **Clone the repository**:
   ```bash
   git clone https://github.com/yourusername/your-repo-name.git
   cd your-repo-name
   ```

2. **Create and activate a virtual environment**:
   ```bash
   python3 -m venv venv
   source venv/bin/activate  # On Windows use `venv\Scripts\activate`
   ```

3. **Install the dependencies**:
   ```bash
   pip install -r requirements.txt
   ```

4. **Run the application**:
   ```bash
   python app.py
   ```

5. **Access the application**:
   - Open your browser and go to `http://127.0.0.1:5000/login`.

## Templates

- **`login.html`**: 
  - A form-based template where users input their credentials.
  
- **`dashboard.html`**: 
  - Displays user-specific information after login.

## Contributing

Feel free to submit pull requests or open issues to improve the application or fix bugs.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

---

Replace placeholders like `yourusername` and `your-repo-name` with your actual GitHub username and repository name.
