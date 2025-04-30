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

Comments
--------

Implementation Comments
~~~~~~~~~~~~~~~~~~~~~~~

**HTML**

.. code-block:: html

   <!-- Create Room Form -->
   <form id="create-room-form">
       <label for="roomname">Enter room name:</label>
       <input type="text" id="roomname" placeholder="Room Name">
       <small id="roomNameError" class="error"></small>
       <button class="btn" id="createRoomBtn" disabled>Create</button>
       <p class="info">Already have a room?
           <a href="/SETAP-coursework/frontend/rooms/joinroom.html">
               <span class="link" id="joinlink">Join room</span>
           </a>
       </p>
   </form>

   <!-- Join Room Form -->
   <label for="roomcode">Enter room code:</label>
   <input type="text" id="roomcode" placeholder="Room Code">
   <button class="btn" id="joinRoomBtn">
       <a href="/SETAP-coursework/frontend/rooms/enterRooms/enterRooms.html">Join</a>
   </button>
   <p class="info">No room code?
       <a href="/SETAP-coursework/frontend/rooms/createroom.html">
           <span class="link" id="createlink">Create room</span>
       </a>
   </p>

- Each form provides clear labeling and error feedback.
- Navigation links allow users to switch between creating and joining rooms.

**CSS**

.. code-block:: css

   .btn {
       display: block;
       width: 100px;
       padding: 10px;
       margin: 10px auto;
       border: none;
       border-radius: 10px;
       background: #6EDFEA;
       font-size: 16px;
       font-weight: bold;
       cursor: pointer;
       transition: 0.3s;
   }
   .btn:hover {
       background: #57C7D4;
   }
   .error {
       color: red;
       font-size: 12px;
       display: block;
       margin-top: -5px;
       margin-bottom: 10px;
   }

- The CSS provides a clean, modern look and ensures usability on all devices.
- Error messages are styled for visibility and clarity.

**JavaScript**

.. code-block:: javascript

   document.addEventListener("DOMContentLoaded", function () {
     const createRoomForm = document.getElementById("create-room-form");
     const createRoomBtn = document.getElementById("createRoomBtn");
     const roomNameInput = document.getElementById("roomname");

     if (createRoomForm && createRoomBtn && roomNameInput) {
       const roomNameError = document.getElementById("roomNameError");

       function validateRoomName() {
         const room = roomNameInput.value.trim();
         if (room.length > 0 && room.length < 3) {
           roomNameError.textContent = "Room name must be at least 3 characters.";
           createRoomBtn.disabled = true;
         } else {
           roomNameError.textContent = "";
           createRoomBtn.disabled = room.length === 0 || room.length < 3;
         }
       }

       roomNameInput.addEventListener("input", validateRoomName);

       createRoomForm.addEventListener('submit', async function (event) {
         event.preventDefault();
         const roomName = roomNameInput.value.trim();
         if (roomName.length < 3) return;

         try {
           const response = await fetch("http://localhost:3000/api/rooms", {
             method: "POST",
             headers: { "Content-Type" : "application/json" },
             body: JSON.stringify({ roomName })
           });
           const result = await response.json();
           if (response.status == 201) {
             alert(result.message);
             window.location.href = `/dashboard.html?roomId=${result.room.room_id}`;
           } else {
             roomNameError.textContent = result.message;
           }
         } catch (error) {
           roomNameError.textContent = "Error: " + error.message;
         }
       });

       validateRoomName();
     }
   });

- Validates room name input in real time.
- Handles form submission, sends data to the backend, and processes the response.
- Displays error messages and redirects on success.

Interface Comments
~~~~~~~~~~~~~~~~~~

**API Endpoint (Create Room)**

- **POST** `/api/rooms`
    - **Request Body:** ``{ "roomName": string }``
    - **Response:** ``{ "message": string, "room": { "room_id": string } }`` and HTTP status code

**Form Fields**

- `roomname`: Name for the new room (minimum 3 characters).
- `roomcode`: Code to join an existing room.

**Navigation**

- On successful room creation: Redirects to `/dashboard.html?roomId=<room_id>`
- "Join room" and "Create room" links allow users to switch between pages.

----

.. note::
   If the backend API or room joining logic changes, update the JavaScript accordingly.

Index
-----

* :ref:`genindex`
* :ref:`modindex`
* :ref:`search`
