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
