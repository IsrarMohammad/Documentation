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
