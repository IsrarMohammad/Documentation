Meeting Notes Page Documentation
===============================

Usage
-----

The Meeting Notes feature allows users to create, view, edit, and delete meeting notes associated with a room. Notes are stored locally in the browser for quick access and editing. The interface consists of a notes list and an "add/edit note" form.

**Key Features:**

- View a list of all meeting notes.
- Add new notes with date, time, purpose, and summary.
- Edit existing notes by clicking on them.
- Delete notes with a single click.
- User-friendly interface with clear navigation and feedback.

**Example Usage:**

1. Open the Meeting Notes page to see a list of existing notes and placeholders for new ones.
2. Click "Add" or a placeholder to create a new note.
3. Fill in the date, time, purpose, and summary, then click "Save".
4. To edit an existing note, click its entry in the list.
5. To delete a note, click the 🗑️ button next to it.

Maintenance
-----------

The Meeting Notes feature is composed of three main parts:

1. **HTML Structure**
    - A page for listing notes with an "Add" button.
    - A form page for adding or editing notes.
    - Navigation buttons for returning to the notes list.

2. **CSS Styling**
    - Consistent, modern look with clear form fields and interactive buttons.
    - Responsive design for various screen sizes.
    - Visual feedback for buttons and note boxes.

3. **JavaScript Logic**
    - Handles displaying, adding, editing, and deleting notes.
    - Uses `localStorage` to persist notes in the browser.
    - Provides user feedback via alerts and form validation.

**How it works:**

- On the notes list page, notes are loaded from `localStorage` and displayed as clickable boxes.
- If fewer than three notes exist, placeholder boxes prompt the user to add more.
- Clicking "Add" or a placeholder navigates to the add/edit form.
- The form supports both creating and editing notes, depending on the URL parameters.
- On form submission, notes are saved to `localStorage` and the user is redirected to the notes list.
- The delete button removes a note from `localStorage` and refreshes the list.

Comments
--------

Implementation Comments
~~~~~~~~~~~~~~~~~~~~~~~

**HTML**

.. code-block:: html

    <!-- Notes List Page -->
    <div class="notescontainer">
      <h2 id="heading">Meeting notes</h2>
      <div id="noteslist"></div>
      <button class="addbtn" onclick="window.location.href='addnote.html'">Add</button>
    </div>

    <!-- Add/Edit Note Form Page -->
    <form id="notesform">
      <h2>Input meeting notes</h2>
      <label>Date</label>
      <input type="date" id="date" required />
      <label>Time</label>
      <input type="time" id="time" required />
      <label>Purpose</label>
      <input type="text" id="purpose" required />
      <label>Summary</label>
      <textarea id="summary" required></textarea>
      <button type="submit" class="savebtn">Save</button>
    </form>

- The notes list and form are separated into different pages for clarity.
- Navigation buttons allow users to move between the form and the list.

**CSS**

.. code-block:: css

    .notescontainer {
      margin-top: 100px;
      padding: 30px;
      background-color: #cceeff;
      border-radius: 20px;
      box-shadow: 0px 4px 8px rgba(0, 0, 0, 0.1);
      width: 80%;
      max-width: 400px;
      text-align: center;
    }
    .note-box {
      background-color: #fff;
      margin: 10px 0;
      padding: 15px;
      border-radius: 10px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      box-shadow: 1px 1px 5px rgba(0,0,0,0.1);
      cursor: pointer;
      transition: transform 0.2s;
    }
    .note-box:hover {
      transform: scale(1.02);
    }
    .addbtn, .savebtn {
      background-color: #b2f0f0;
      border: none;
      padding: 10px 20px;
      margin-top: 20px;
      border-radius: 15px;
      font-weight: bold;
      cursor: pointer;
      box-shadow: 2px 2px 5px #aaa;
    }
    form {
      display: flex;
      flex-direction: column;
      margin-top: 80px;
      width: 80%;
      max-width: 400px;
    }
    form label {
      margin-top: 15px;
      font-weight: 500;
    }
    form input,
    form textarea {
      margin-top: 5px;
      padding: 10px;
      border: 1px solid #ccc;
      border-radius: 10px;
      font-size: 14px;
    }
    form textarea {
      resize: vertical;
      min-height: 80px;
    }

- The CSS provides a visually appealing, accessible, and responsive design.
- Buttons and note boxes are styled for easy interaction.

**JavaScript**

.. code-block:: javascript

    document.addEventListener("DOMContentLoaded", () => {
      const notesList = document.getElementById("noteslist");
      const form = document.getElementById("notesform");

      if (notesList) {
        const storedNotes = JSON.parse(localStorage.getItem("meetingNotes")) || [];
        const MAX_DUMMIES = 3;
        const dummiesToShow = Math.max(0, MAX_DUMMIES - storedNotes.length);

        // Show dummy placeholders
        for (let i = 0; i < dummiesToShow; i++) {
          const box = document.createElement("div");
          box.className = "note-box";
          box.innerHTML = `
            <div onclick="window.location.href='addnote.html'" style="text-align: left;">
              <strong>Meeting Note ${i + 1}</strong><br/>
              <small>Click to add details</small>
            </div>
            <button disabled>🗑️</button>
          `;
          notesList.appendChild(box);
        }

        // Show real notes
        storedNotes.forEach((note, index) => {
          const box = document.createElement("div");
          box.className = "note-box";
          box.innerHTML = `
            <div onclick="window.location.href='addnote.html?index=${index}'" style="text-align: left;">
              <strong>${note.purpose}</strong><br/>
              <small>${note.date} at ${note.time}</small>
            </div>
            <button onclick="deleteNote(${index})">🗑️</button>
          `;
          notesList.appendChild(box);
        });
      }

      // Handle add/edit form
      if (form) {
        const params = new URLSearchParams(window.location.search);
        const index = params.get("index");
        const existing = JSON.parse(localStorage.getItem("meetingNotes")) || [];

        if (index !== null && existing[index]) {
          const note = existing[index];
          document.getElementById("date").value = note.date;
          document.getElementById("time").value = note.time;
          document.getElementById("purpose").value = note.purpose;
          document.getElementById("summary").value = note.summary;
        }

        form.addEventListener("submit", (e) => {
          e.preventDefault();

          const date = document.getElementById("date").value;
          const time = document.getElementById("time").value;
          const purpose = document.getElementById("purpose").value;
          const summary = document.getElementById("summary").value;

          const newNote = { date, time, purpose, summary };

          if (index !== null && existing[index]) {
            existing[index] = newNote;
          } else {
            existing.push(newNote);
          }

          localStorage.setItem("meetingNotes", JSON.stringify(existing));
          alert("Notes saved successfully");
          window.location.href = "meetingnotes.html";
        });
      }
    });

    // Delete function
    function deleteNote(index) {
      const storedNotes = JSON.parse(localStorage.getItem("meetingNotes")) || [];
      storedNotes.splice(index, 1);
      localStorage.setItem("meetingNotes", JSON.stringify(storedNotes));
      location.reload();
    }

- Notes are stored and retrieved from `localStorage`.
- The form supports both adding and editing notes.
- The delete button removes a note and refreshes the list.

Interface Comments
~~~~~~~~~~~~~~~~~~

**Form Fields**

- `date`: Date of the meeting.
- `time`: Time of the meeting.
- `purpose`: Short description of the meeting's purpose.
- `summary`: Detailed notes or summary.

**Navigation**

- Back button: Returns to the notes list.
- Add/Edit: Navigates to the add/edit form.
- Delete: Removes a note from the list.

**Data Storage**

- Notes are stored in the browser's `localStorage` under the key `"meetingNotes"`.

----

.. note::
   For multi-user or server-based storage, adapt the JavaScript to use API calls instead of `localStorage`.

Index
-----

* :ref:`genindex`
* :ref:`modindex`
* :ref:`search`

