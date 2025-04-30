Registration Page Documentation
==============================

Usage
-----

The Registration Page allows new users (students) to create an account by providing a username, email, and password. The form includes validation for all fields and provides immediate feedback for invalid entries. Upon successful registration, users are redirected to the login page.

**Key Features:**

- User registration with username, email, and password.
- Real-time form validation and error messages.
- Responsive and accessible design.
- Link to login page for existing users.

**Example Usage:**

1. Open the registration page in your browser.
2. Fill in the username, email, password, and confirm password fields.
3. Click "Register" to submit the form.
4. If registration is successful, you will be redirected to the login page.
5. If you already have an account, click "Log in" to navigate to the login page.

Maintenance
-----------

The registration page is composed of three main components:

1. **HTML Structure**
    - Provides the form layout, input fields, error messages, and navigation links.
2. **CSS Styling**
    - Ensures a visually appealing, responsive, and user-friendly interface.
3. **JavaScript Logic**
    - Handles real-time validation, error display, form submission, and communication with the backend API.

**How it works:**

- As users fill out the form, JavaScript validates each input (username length, email format, password strength, password match).
- Error messages are displayed in real-time below each field if validation fails.
- The "Register" button is disabled until all inputs are valid.
- On submission, a POST request is sent to `/api/register` with the form data in JSON format.
- If registration is successful (HTTP 201), the user is redirected to the login page.
- If registration fails, an error message is shown.
- All interactions are handled asynchronously for a smooth user experience.

Comments
--------

Implementation Comments
~~~~~~~~~~~~~~~~~~~~~~~

**HTML**

.. code-block:: html

   <form id="registerForm" action="/SETAP-coursework/frontend/landingpage/index.html" class="card">
       <h2>Register</h2>
       <p>Please fill in this form to create an account.</p>
       <input type="text" placeholder="enter your student username" name="student-username" id="student-username" required>
       <span id="usernameError" class="error"></span>
       <input type="email" placeholder="enter your student email" name="student-email" id="student-email" required>
       <span id="emailError" class="error"></span>
       <input type="password" placeholder="enter password" name="password" id="password" required>
       <span id="passwordError" class="error"></span>
       <input type="password" placeholder="confirm password" name="confirm-password" id="confirm-password" required>
       <span id="confirmPasswordError" class="error"></span>
       <button type="submit" class="register-button">Register</button>
       <div class="container signin">
           <p>Already have an account? <a class="register-link" href="/SETAP-coursework/frontend/loginpage/login.html">Log in</a></p>
       </div>
   </form>

- Each field is paired with a span for real-time error feedback.
- The "Log in" link provides navigation for existing users.

**CSS**

.. code-block:: css

   .card {
       background: white;
       border-radius: 10px;
       box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
       padding: 2rem;
   }
   .error {
       color: red;
       font-size: 12px;
       display: block;
       margin-top: -10px;
       margin-bottom: 10px;
   }

- The CSS centers the registration form, styles the card, and highlights errors.
- Responsive design is achieved with flexible widths and margins.

**JavaScript**

.. code-block:: javascript

   // Real-time validation for all fields
   function checkInputs() {
       let isValid = true;
       // Username validation
       // Email validation
       // Password validation
       // Password match validation
       // Enable/disable register button
   }
   // Form submission with fetch API
   document.getElementById("registerForm").addEventListener('submit', async (event) => {
       event.preventDefault();
       // Send POST request to backend
       // Handle response and errors
   });

- Validates inputs as the user types.
- Disables the register button if any field is invalid.
- Handles form submission and redirects on success.

Interface Comments
~~~~~~~~~~~~~~~~~~

**API Endpoint**

- **POST** `/api/register`
    - **Request Body:**  
      ``{ "username": string, "email": string, "password": string, "password2": string }``
    - **Response:**  
      ``{ "message": string }`` and HTTP status code

**Form Fields**

- `student-username`: Student's username (minimum 3 characters).
- `student-email`: Student's email (must be valid format).
- `password`: Password (minimum 8 characters, must include a letter and a number).
- `confirm-password`: Must match the password.

**Navigation**

- On successful registration: Redirects to `/loginpage/login.html`
- On "Log in" link click: Redirects to `/SETAP-coursework/frontend/loginpage/login.html`

----

.. note::
   Update the validation logic or API endpoint as needed if the backend requirements change.

Index
-----

* :ref:`genindex`
* :ref:`modindex`
* :ref:`search`

