Input Availability Page Documentation
====================================

Usage
-----

The Input Availability page enables users to specify their available days and times. This feature is designed to help coordinate schedules within the application, such as for meetings or collaborative sessions.

**Key Features:**

- Users select a day (Monday–Friday) and a time slot (09:00–18:00).
- Immediate feedback is provided if either field is left empty.
- A "Save" button allows users to submit their availability.
- A back button allows users to return to the previous page.

**Example Usage:**

1. Open the Input Availability page.
2. Select a day from the dropdown menu.
3. Select a time from the dropdown menu.
4. Click "Save" to submit your availability.
5. Use the back arrow to return to the previous page if needed.

Maintenance
-----------

The Input Availability page consists of three main components:

1. **HTML Structure**
    - Provides a form with dropdowns for day and time selection.
    - Includes a back button and a save button.

2. **CSS Styling**
    - Ensures a clean, centered, and visually appealing interface.
    - Styles the form, buttons, and layout for usability.

3. **JavaScript Logic**
    - Handles navigation (back button).
    - Validates that both day and time are selected before saving.
    - Provides user feedback via alerts.

**How it works:**

- The user selects a day and a time from their respective dropdowns.
- When "Save" is clicked, JavaScript checks that both fields are filled.
    - If both are filled, an alert confirms the saved availability.
    - If either is empty, an alert prompts the user to complete both fields.
- The back button uses browser history to return to the previous page.

Comments
--------

Implementation Comments
~~~~~~~~~~~~~~~~~~~~~~~

**HTML**

.. code-block:: html

   <div class="container">
       <div class="back-button">
           <img src="/SETAP-coursework/frontend/icons/left-arrow.png" alt="back">   
       </div>
       <h2>Input availability</h2>
       <div class="availability-form">
           <label for="day">When</label>
           <div class="select-group">
               <select id="day">
                   <option value="">Day</option>
                   <option value="Monday">Monday</option>
                   ...
               </select>
               <select id="time">
                   <option value="">Time</option>
                   <option value="09:00 AM">09:00 AM</option>
                   ...
               </select>
           </div>
       </div>
       <button class="save-button">Save</button>
   </div>

- The form is simple and user-friendly, with clear labeling and dropdowns for input.
- The back button is visually distinct and accessible.

**CSS**

.. code-block:: css

   .container {
       position: relative;
       width: 300px;
       text-align: center;
   }
   .back-button {
       position: absolute;
       top: 10px;
       right: 10px;
       cursor: pointer;
   }
   .availability-form {
       background-color: white;
       padding: 15px;
       border-radius: 10px;
       width: 90%;
       margin: 20px auto;
       box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.1);
   }
   .save-button {
       background-color: #C4EBF5;
       border: none;
       padding: 10px 20px;
       border-radius: 15px;
       font-size: 14px;
       cursor: pointer;
   }

- The CSS ensures the form is centered, visually appealing, and easy to use.
- Buttons and dropdowns are styled for clarity and accessibility.

**JavaScript**

.. code-block:: javascript

   document.querySelector(".back-button").addEventListener("click", function () {
       window.history.back()
   })

   document.querySelector(".save-button").addEventListener("click", function () {
       let day = document.getElementById("day").value
       let time = document.getElementById("time").value

       if (day && time) {
           alert(`Availability saved: ${day}, ${time}`)
       }
       else
       {
           alert("Please select both day and time")
       }
   })

- The back button allows for easy navigation.
- The save button validates input and provides immediate feedback.
- Alerts are used for simplicity; integration with a backend or state management can be added as needed.

Interface Comments
~~~~~~~~~~~~~~~~~~

**Form Fields**

- `day`: Dropdown menu for selecting the day (Monday–Friday).
- `time`: Dropdown menu for selecting the time (09:00–18:00, hourly).

**Navigation**

- Back button: Returns the user to the previous page.
- Save button: Validates and saves the selected availability.

**User Feedback**

- Alerts are used for both successful saves and validation errors.

----

.. note::
   If backend integration is required, update the JavaScript to send the selected availability to your API.

Index
-----

* :ref:`genindex`
* :ref:`modindex`
* :ref:`search`

