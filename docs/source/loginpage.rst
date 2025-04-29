Login Page Documentation
========================

Usage
-----

The Login Page provides a secure interface for users (students) to authenticate themselves using their username or email and password. Upon successful login, users are redirected to their dashboard. New users can navigate to the registration page.

**Key Features:**

- User authentication with username or email and password.
- Responsive and visually appealing design.
- Link to registration page for new users.
- Error handling for failed login attempts.

**Example Usage:**

.. code-block:: none

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

Comments
--------

Implementation Comments
~~~~~~~~~~~~~~~~~~~~~~~

**HTML**

.. code-block:: html

   <form id="login-form">
       <input type="text" id="student-username-email" name="student-username-email" placeholder="username or email-address" required>
       <input type="password" id="password" name="password" placeholder="password" required>
       <button type="submit">Continue</button>
   </form>

- The form uses semantic input types for accessibility and validation.
- The "Register" link provides easy navigation for new users.

**CSS**

.. code-block:: css

   .login-card {
       background: white;
       border-radius: 10px;
       box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
       padding: 2rem;
   }

- The CSS ensures the login card is centered, visually distinct, and user-friendly.
- Responsive design is achieved using flexbox and relative units.

**JavaScript**

.. code-block:: javascript

   document.getElementById('login-form').addEventListener('submit', async (event) => {
       event.preventDefault();
       // Fetch form data
       // Send POST request to API
       // Handle response and errors
   });

- The JavaScript attaches an event listener to the form to handle submission.
- The user input is validated and sent to the backend.
- On success, the user is redirected; on failure, an error message is shown.

Interface Comments
~~~~~~~~~~~~~~~~~~

**API Endpoint**

- **POST** `/api/login`
    - **Request Body:** `{ "email": string|null, "username": string, "password": string }`
    - **Response:** `{ "message": string }` and HTTP status code

**Form Fields**

- `student-username-email`: Accepts either a username or an email address.
- `password`: Accepts the user's password.

**Navigation**

- On successful login: Redirects to `Dashboard/dashboard.html`
- On registration link click: Redirects to `/SETAP-coursework/frontend/registerpage/register.html`

----

.. note::
   For any changes to the backend API or authentication flow, update the JavaScript logic accordingly.

Index
-----

* :ref:`genindex`
* :ref:`modindex`
* :ref:`search`

