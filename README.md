# MAD1-Week-9-Flask-Application-with-Security
This Flask application is a basic user authentication system that demonstrates how to manage user login, logout, and access control for a protected dashboard.
Overview:
The app uses Flask along with Flask-Login for managing user sessions and Flask-SQLAlchemy for database interactions. It also includes simple routes to handle user login, logout, and access to a protected dashboard.

Components:
Database Setup:

SQLite is used as the database, configured with the URI 'sqlite:///login_db.sqlite3'.
The User model represents the users of the application. It contains fields for id, username, password, and role.
The database is managed using Flask-SQLAlchemy.
User Authentication:

The Flask-Login extension manages user sessions. It provides functions like login_user, logout_user, and login_required to control access to certain routes.
The load_user function retrieves a user from the database by their id, which is stored in the session.
Routes:

/login Route:

Handles both GET and POST requests.
On a GET request, it renders the login.html template, allowing the user to enter their credentials.
On a POST request, it retrieves the username and password from the form, checks the database for a matching user, and if the credentials are correct, logs the user in and redirects them to the /dashboard route. If the credentials are incorrect, it returns an appropriate error message.
/dashboard Route:

This is a protected route, accessible only to authenticated users.
The route renders the dashboard.html template, passing the current_user (the user who is logged in) to the template for display.
/logout Route:

Logs out the current user and redirects them to the /login page.
Templates:
login.html:
A form-based template where users input their credentials.
dashboard.html:
Displays user-specific information and can be customized to show different content based on the user's role or other attributes.
Security:
Password Handling:
The app currently compares plaintext passwords directly, which is not secure for a production environment. In a real-world application, passwords should be hashed before storing them in the database, and comparisons should be made between the hashed versions.
Session Management:
The SECRET_KEY is used to sign session cookies, ensuring that they cannot be tampered with by clients.
Usage:
Users can log in via the /login route, and upon successful authentication, they are redirected to the /dashboard page.
The /dashboard page is protected, meaning only logged-in users can access it.
Users can log out via the /logout route, which ends their session and redirects them to the login page.
This app is a simple starting point for building more complex Flask applications with user authentication and role-based access control. It can be extended with additional features like user registration, password hashing, role management, and more secure practices.
