Slot-ify Landing Page Documentation
===================================

Usage
-----

The Slot-ify Landing Page serves as the welcoming entry point for users of the scheduling application. It displays the application branding, a relevant illustration, animated loading dots, and a dynamic typing effect for the tagline. After a brief introduction, users are automatically redirected to the login page.

**Key Features:**

- Prominent branding and app name.
- Illustration to visually introduce the scheduling concept.
- Animated loading dots to indicate activity.
- Typing effect for the tagline to engage users.
- Automatic redirection to the login page after a short delay.

**Example Usage:**

1. Users visit the main application URL.
2. The landing page displays branding, illustration, animated dots, and a typing tagline.
3. After 10 seconds, users are redirected to the login page to begin authentication.

Maintenance
-----------

The landing page consists of three main components:

1. **HTML Structure**
    - Contains branding, illustration, loading dots, and a footer text area for the typing effect.
    - Minimal navigation; the page is designed for a brief display before redirecting.

2. **CSS Styling**
    - Responsive and visually appealing layout with a modern color scheme.
    - Animations for the illustration (hover effect), loading dots (bounce), and page fade-in.
    - Typing effect styling with a blinking cursor.

3. **JavaScript Logic**
    - Implements the typing effect for the tagline.
    - Loops the typing effect with a pause and clear cycle.
    - Automatically redirects users to the login page after 10 seconds.

**How it works:**

- On load, the page animates the tagline text character-by-character.
- Loading dots bounce in sequence to indicate the app is preparing.
- After the animation loop, the page redirects to the login page using `window.location.href`.

Comments
--------

Implementation Comments
~~~~~~~~~~~~~~~~~~~~~~~

**HTML**

.. code-block:: html

    <div class="container">
        <div class="branding">
            <h1>Slot-ify</h1>
        </div>
        <div class="illustration">
            <img src="/SETAP-coursework/images/Managers-team-Graphics-17978760-1.jpg" alt="Illustration of scheduling app">
        </div>
        <div class="loading-dots">
            <span class="dot"></span>
            <span class="dot"></span>
            <span class="dot"></span>
        </div>
        <div class="footer-text">
            <p id="typing-text"></p>
        </div>
    </div>

- The container centers all content and manages layout.
- The illustration and loading dots provide visual engagement.
- The footer text area displays the animated tagline.

**CSS**

.. code-block:: css

    body {
        font-family: 'Outfit', sans-serif;
        background: linear-gradient(135deg, #e0f7fa, #fff);
        height: 100vh;
        display: flex;
        justify-content: center;
        align-items: center;
        overflow: hidden;
    }
    .container {
        text-align: center;
        padding: 2rem;
        max-width: 600px;
        animation: fadeIn 1.5s ease;
    }
    .branding h1 {
        font-size: 3rem;
        color: #00a8cc;
        font-weight: 700;
        letter-spacing: 1px;
    }
    .illustration img {
        width: 100%;
        max-width: 400px;
        margin: 2rem auto;
        border-radius: 20px;
        box-shadow: 0 10px 20px rgba(0, 168, 204, 0.1);
        transition: transform 0.5s ease;
    }
    .illustration img:hover {
        transform: scale(1.05);
    }
    .loading-dots {
        display: flex;
        justify-content: center;
        gap: 10px;
        margin-bottom: 20px;
    }
    .dot {
        width: 12px;
        height: 12px;
        background-color: #00a8cc;
        border-radius: 50%;
        animation: bounce 1.2s infinite ease-in-out;
    }
    .dot:nth-child(2) { animation-delay: 0.2s; }
    .dot:nth-child(3) { animation-delay: 0.4s; }
    @keyframes bounce {
        0%, 80%, 100% { transform: scale(0); }
        40% { transform: scale(1); }
    }
    .footer-text {
        color: #666;
        font-size: 1rem;
        margin-top: 20px;
    }
    #typing-text {
        display: inline-block;
        border-right: 2px solid #00a8cc;
        white-space: nowrap;
        overflow: hidden;
    }
    @keyframes fadeIn {
        from { opacity: 0; transform: translateY(10%);}
        to { opacity: 1; transform: translateY(0);}
    }

- The CSS ensures a modern, responsive, and visually engaging landing page.
- Animations are used for user engagement and to indicate loading.

**JavaScript**

.. code-block:: javascript

    const text = "Get things done with our fast-tracking scheduling app!";
    const typingTextElement = document.querySelector('#typing-text');
    let index = 0;
    const typingSpeed = 100;

    function typeText() {
        if (index < text.length) {
            typingTextElement.textContent += text.charAt(index);
            index++;
            setTimeout(typeText, typingSpeed);
        } else {
            setTimeout(clearText, 2000); // Pause for 2 seconds before resetting
        }
    }

    function clearText() {
        typingTextElement.textContent = '';
        index = 0;
        typeText();
    }

    typeText();
    // Redirect to login page after 10 seconds
    setTimeout(function () {
        window.location.href = "/SETAP-coursework/frontend/loginpage/login.html";
    }, 10000);

- The typing effect animates the tagline, looping with a pause.
- After 10 seconds, the user is redirected to the login page.

Interface Comments
~~~~~~~~~~~~~~~~~~

**Displayed Elements**

- Branding: App name ("Slot-ify").
- Illustration: Visual representation of the app's purpose.
- Loading Dots: Animated to indicate loading.
- Typing Tagline: Animated text for engagement.

**Navigation**

- Automatic: Redirects to the login page after 10 seconds.

----

.. note::
   Update the redirect URL in the JavaScript if the login page location changes.

Index
-----

* :ref:`genindex`
* :ref:`modindex`
* :ref:`search`

