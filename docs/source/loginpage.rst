Login Page Documentation
========================

Usage
-----

The Login Page provides a secure interface for users to authenticate themselves using their username or email and password. Upon successful login, users are redirected to their dashboard. New users can navigate to the registration page.

**Key Features:**

- User authentication with username or email and password.
- User frindly  design.
- Link to registration page for new users.
- Error handling for failed login attempts.

**Example Usage:**

   1. Open the login page in your browser.
   2. Enter your username or email and password.
   3. Click "Continue" to log in.
   4. If you are a new user, click "Register" to create an account.

Maintenance
-----------

The login page consists of three main components:

1. **HTML Structure**  
   - Provides the layout for the login form, including input fields and navigation links.
2. **CSS Styling**  
   - Ensures the page is visually appealing and responsive across devices.
3. **JavaScript Logic**  
   - Handles form submission, communicates with the backend API, and manages user feedback and navigation.

**How it works:**

- When the user submits the login form, JavaScript intercepts the submission and sends a POST request to the backend API (`/api/login`).
- The API expects a JSON payload containing either an email or username and a password.
- If authentication is successful (HTTP 200), the user is redirected to the dashboard.
- If authentication fails, an error message is displayed.
- All interactions are handled asynchronously to ensure a smooth user experience.

