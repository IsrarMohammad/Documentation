Room Management Pages Documentation
==================================

Usage
-----

The Room Management section allows users to create a new room, join an existing room, or navigate between these options. These pages enable collaboration and group activities within the application.

**Create Room Page:**

- Users can create a new room by entering a room name.
- The "Create" button is enabled only when the room name is at least 3 characters long.
- Users can navigate to the "Join Room" page if they already have a room code.

**Join Room Page:**

- Users can join an existing room by entering a valid room code.
- Users can navigate to the "Create Room" page if they do not have a room code.

**Room Selection Page:**

- If the user is not in a room, they are prompted to either create a new room or join an existing one.

**Typical Workflow:**

1. If not in a room, the user is presented with options to create or join a room.
2. To create a room, the user enters a room name and submits the form.
3. To join a room, the user enters a room code and submits the form.
4. Navigation links are provided to switch between creating and joining a room.

Maintenance
-----------

The Room Management feature is composed of three main parts:

1. **HTML Structure**
    - Provides forms and navigation for creating and joining rooms.
    - Displays error messages and feedback to the user.

2. **CSS Styling**
    - Ensures a clean, modern, and responsive user interface.
    - Styles forms, buttons, error messages, and layout.

3. **JavaScript Logic**
    - Validates input fields in real time.
    - Handles form submission and communicates with the backend API.
    - Displays error messages and redirects users as appropriate.

**How it works:**

- **Create Room:**
    - The user enters a room name. JavaScript validates that the name is at least 3 characters.
    - On submission, a POST request is sent to `/api/rooms` with the room name.
    - If successful, the user is redirected to the dashboard with the new room ID.
    - If unsuccessful, an error message is shown.

- **Join Room:**
    - The user enters a room code and clicks "Join".
    - (Implementation note: The provided code currently navigates to a static page; backend integration may be required.)

- **Room Selection:**
    - Provides clear navigation to create or join a room.

