Enter Room Menu Page Documentation
==================================

Usage
-----

The Enter Room Menu page serves as the central navigation hub for room-related features within the application. After entering a room, users are presented with a visually organized menu of actions they can perform, such as managing room settings, scheduling meetings, viewing notes, updating availability, and adding participants.

**Key Features:**

- Centralized access to all room-related tools and settings.
- Intuitive button-based navigation with icons and descriptive labels.
- Prominent "Exit" button to leave the room interface.

**Example Usage:**

1. Enter a room to access the menu.
2. Click on any of the available buttons (Room Settings, Meeting Scheduler, Meeting Notes, Availability, Add Participants) to navigate to that feature.
3. Click "Exit" to leave the room and return to the previous page or dashboard.

Maintenance
-----------

The Enter Room Menu page consists of three main components:

1. **HTML Structure**
    - A container holding an exit button and a grid of navigation buttons.
    - Each button is labeled and paired with a relevant icon for clarity.

2. **CSS Styling**
    - Uses grid layouts for responsive, organized button placement.
    - Consistent color palette and rounded buttons for a modern, user-friendly appearance.
    - Ensures accessibility and visual feedback on interaction.

3. **JavaScript Logic**
    - Handles button click events to redirect users to the appropriate room feature pages.
    - Each button is mapped to a specific feature route.
    - The exit button can be extended to handle more complex exit logic if needed.

**How it works:**

- The menu loads with all navigation buttons enabled.
- When a button is clicked, JavaScript redirects the user to the corresponding feature page.
- The exit button allows the user to leave the room interface.

Comments
--------

Implementation Comments
~~~~~~~~~~~~~~~~~~~~~~~

**HTML**

.. code-block:: html

    <div class="container">
        <div class="exit">
            <img src="/SETAP-coursework/frontend/icons/room-door.png" alt="exit icon">
            <span>Exit</span>
        </div>
        <div class="buttons">
            <button id="roomsetting"><img src="/SETAP-coursework/frontend/icons/setting.png" alt="">Room Settings</button>
            <button id="meetingscheduler"><img src="/SETAP-coursework/frontend/icons/scheduler.png" alt="">Meeting Scheduler</button>
            <button id="meetingnotes"><img src="/SETAP-coursework/frontend/icons/notes.png" alt="">Meeting Notes</button>
            <button id="availability"><img src="/SETAP-coursework/frontend/icons/clock.png" alt="">Availability</button>
            <button id="addparticipants"><img src="/SETAP-coursework/frontend/icons/add.png" alt="">Add Participants</button>
        </div>
    </div>

- Each button is uniquely identified for event handling.
- The exit button is visually separated and accessible.

**CSS**

.. code-block:: css

    .container {
        position: relative;
        width: 300px;
        text-align: center;
    }
    .buttons {
        display: grid;
        grid-template-columns: 1fr 1fr;
        gap: 10px;
        margin-top: 50px;
    }
    button {
        background-color: #C4EBF5;
        border: none;
        padding: 15px;
        border-radius: 10px;
        font-size: 14px;
        display: flex;
        flex-direction: column;
        align-items: center;
        cursor: pointer;
    }
    button img {
        width: 24px;
        height: 24px;
        margin-bottom: 5px;
    }
    .exit {
        position: absolute;
        top: 10px;
        right: 10px;
        display: flex;
        align-items: center;
        gap: 5px;
        cursor: pointer;
    }
    .exit img {
        width: 25px;
        height: 25px;
    }

- The grid layout ensures buttons are organized and accessible.
- Icons help users quickly identify each feature.

**JavaScript**

.. code-block:: javascript

    document.getElementById("roomsetting").addEventListener("click", function () {
         window.location.href = "/SETAP-coursework/frontend/rooms/availability/meeting scheduler.html"
    })

    document.getElementById("meetingscheduler").addEventListener("click", function () {
         window.location.href = "/SETAP-coursework/frontend/rooms/availability/meetingscheduler.html"
    })

    document.getElementById("meetingnotes").addEventListener("click", function () {
        window.location.href = "/SETAP-coursework/frontend/rooms/availability/meetingnotes.html"
    })

    document.getElementById("availability").addEventListener("click", function () {
        window.location.href = "/SETAP-coursework/frontend/rooms/availability/availability.html"
    })

    document.getElementById("addparticipants").addEventListener("click", function () {
         window.location.href = "/SETAP-coursework/frontend/rooms/availability/addparticipants.html"
    })

- Each button is wired to redirect to a specific feature page.
- The exit button can be enhanced to handle room exit logic or confirmation dialogs.

Interface Comments
~~~~~~~~~~~~~~~~~~

**Navigation Buttons**

- `#roomsetting`: Navigates to the Room Settings page.
- `#meetingscheduler`: Navigates to the Meeting Scheduler page.
- `#meetingnotes`: Navigates to the Meeting Notes page.
- `#availability`: Navigates to the Availability page.
- `#addparticipants`: Navigates to the Add Participants page.
- `.exit`: Exits the current room interface.

**Routing**

- All navigation is handled client-side via JavaScript, changing the `window.location.href` to the appropriate page.

----

.. note::
   If new features are added or routes change, update the button event handlers and hrefs accordingly.

Index
-----

* :ref:`genindex`
* :ref:`modindex`
* :ref:`search`

