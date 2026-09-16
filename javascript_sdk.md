# JavaScript Website UI SDK

> Reusable vanilla JavaScript components for modern websites.

---

# 1. Basic JavaScript Setup

```html
<script src="script.js"></script>
```

```javascript
document.addEventListener("DOMContentLoaded", () => {

    console.log("Website loaded");

});
```

---

# 2. DOM Selection

```javascript
const element = document.querySelector(".card");

const elements = document.querySelectorAll(".card");

const button = document.getElementById("btn");
```

### Common Methods

```javascript
document.getElementById("id");

document.querySelector(".class");

document.querySelector("#id");

document.querySelectorAll(".class");
```

---

# 3. Change Text

```javascript
const title = document.querySelector("#title");

title.textContent = "Hello World";
```

---

# 4. Change HTML

```javascript
const container = document.querySelector("#container");

container.innerHTML = `
    <h2>Hello</h2>
    <p>Welcome to my website.</p>
`;
```

---

# 5. Change CSS

```javascript
const box = document.querySelector(".box");

box.style.backgroundColor = "black";
box.style.color = "white";
box.style.padding = "20px";
```

---

# 6. Add / Remove Class

```javascript
const menu = document.querySelector(".menu");

menu.classList.add("active");

menu.classList.remove("active");

menu.classList.toggle("active");

menu.classList.contains("active");
```

---

# 7. Button Click

```javascript
const button = document.querySelector("#btn");

button.addEventListener("click", () => {

    console.log("Button clicked");

});
```

---

# 8. Navbar Mobile Menu

### HTML

```html
<button id="menuBtn">
    ☰
</button>

<nav id="mobileMenu">

    <a href="/">Home</a>
    <a href="/about">About</a>
    <a href="/contact">Contact</a>

</nav>
```

### JavaScript

```javascript
const menuBtn = document.querySelector("#menuBtn");
const mobileMenu = document.querySelector("#mobileMenu");

menuBtn.addEventListener("click", () => {

    mobileMenu.classList.toggle("active");

});
```

---

# 9. Close Mobile Menu on Link Click

```javascript
const menuLinks = document.querySelectorAll("#mobileMenu a");

menuLinks.forEach(link => {

    link.addEventListener("click", () => {

        mobileMenu.classList.remove("active");

    });

});
```

---

# 10. Navbar on Scroll

```javascript
const navbar = document.querySelector(".navbar");

window.addEventListener("scroll", () => {

    if (window.scrollY > 50) {

        navbar.classList.add("scrolled");

    } else {

        navbar.classList.remove("scrolled");

    }

});
```

---

# 11. Smooth Scroll

```javascript
document.querySelectorAll('a[href^="#"]')
    .forEach(link => {

        link.addEventListener("click", event => {

            event.preventDefault();

            const target = document.querySelector(
                link.getAttribute("href")
            );

            target?.scrollIntoView({
                behavior: "smooth"
            });

        });

    });
```

---

# 12. Modal / Popup

### HTML

```html
<button id="openModal">
    Open Modal
</button>

<div id="modal" class="modal">

    <div class="modal-content">

        <button id="closeModal">
            ×
        </button>

        <h2>
            Hello
        </h2>

        <p>
            This is a modal.
        </p>

    </div>

</div>
```

### JavaScript

```javascript
const modal = document.querySelector("#modal");

const openModal = document.querySelector("#openModal");

const closeModal = document.querySelector("#closeModal");

openModal.addEventListener("click", () => {

    modal.classList.add("active");

});

closeModal.addEventListener("click", () => {

    modal.classList.remove("active");

});
```

---

# 13. Close Modal Outside

```javascript
modal.addEventListener("click", event => {

    if (event.target === modal) {

        modal.classList.remove("active");

    }

});
```

---

# 14. Close Modal with Escape

```javascript
document.addEventListener("keydown", event => {

    if (event.key === "Escape") {

        modal.classList.remove("active");

    }

});
```

---

# 15. Dropdown

### HTML

```html
<button id="dropdownBtn">
    Menu
</button>

<div id="dropdownMenu" class="dropdown">

    <a href="#">Profile</a>
    <a href="#">Settings</a>
    <a href="#">Logout</a>

</div>
```

### JavaScript

```javascript
const dropdownBtn =
    document.querySelector("#dropdownBtn");

const dropdownMenu =
    document.querySelector("#dropdownMenu");

dropdownBtn.addEventListener("click", () => {

    dropdownMenu.classList.toggle("active");

});
```

---

# 16. Close Dropdown Outside

```javascript
document.addEventListener("click", event => {

    if (
        !dropdownBtn.contains(event.target) &&
        !dropdownMenu.contains(event.target)
    ) {

        dropdownMenu.classList.remove("active");

    }

});
```

---

# 17. Accordion

### HTML

```html
<div class="accordion">

    <button class="accordion-btn">
        What is HTML?
    </button>

    <div class="accordion-content">

        <p>
            HTML structures a webpage.
        </p>

    </div>

</div>
```

### JavaScript

```javascript
const accordionButtons =
    document.querySelectorAll(".accordion-btn");

accordionButtons.forEach(button => {

    button.addEventListener("click", () => {

        button.classList.toggle("active");

        const content = button.nextElementSibling;

        content.classList.toggle("active");

    });

});
```

---

# 18. Tabs

### HTML

```html
<div class="tabs">

    <button class="tab-btn active" data-tab="home">
        Home
    </button>

    <button class="tab-btn" data-tab="about">
        About
    </button>

    <button class="tab-btn" data-tab="contact">
        Contact
    </button>

</div>

<div id="home" class="tab-content active">
    Home Content
</div>

<div id="about" class="tab-content">
    About Content
</div>

<div id="contact" class="tab-content">
    Contact Content
</div>
```

### JavaScript

```javascript
const tabButtons =
    document.querySelectorAll(".tab-btn");

const tabContents =
    document.querySelectorAll(".tab-content");

tabButtons.forEach(button => {

    button.addEventListener("click", () => {

        tabButtons.forEach(btn => {
            btn.classList.remove("active");
        });

        tabContents.forEach(content => {
            content.classList.remove("active");
        });

        button.classList.add("active");

        const target =
            document.getElementById(
                button.dataset.tab
            );

        target.classList.add("active");

    });

});
```

---

# 19. Dark Mode

### HTML

```html
<button id="themeToggle">
    🌙
</button>
```

### JavaScript

```javascript
const themeToggle =
    document.querySelector("#themeToggle");

themeToggle.addEventListener("click", () => {

    document.body.classList.toggle("dark");

});
```

---

# 20. Dark Mode with LocalStorage

```javascript
const themeToggle =
    document.querySelector("#themeToggle");

const savedTheme =
    localStorage.getItem("theme");

if (savedTheme === "dark") {

    document.body.classList.add("dark");

}

themeToggle.addEventListener("click", () => {

    document.body.classList.toggle("dark");

    const theme =
        document.body.classList.contains("dark")
            ? "dark"
            : "light";

    localStorage.setItem("theme", theme);

});
```

---

# 21. Form Submit

```javascript
const form = document.querySelector("#form");

form.addEventListener("submit", event => {

    event.preventDefault();

    console.log("Form submitted");

});
```

---

# 22. Form Validation

```javascript
const form = document.querySelector("#form");

form.addEventListener("submit", event => {

    event.preventDefault();

    const name =
        document.querySelector("#name").value.trim();

    const email =
        document.querySelector("#email").value.trim();

    if (!name) {

        alert("Please enter your name");
        return;

    }

    if (!email) {

        alert("Please enter your email");
        return;

    }

    console.log("Form valid");

});
```

---

# 23. Email Validation

```javascript
function isValidEmail(email) {

    return /^[^\s@]+@[^\s@]+\.[^\s@]+$/
        .test(email);

}
```

### Usage

```javascript
if (!isValidEmail(email)) {

    alert("Invalid email");

    return;

}
```

---

# 24. Password Validation

```javascript
function isValidPassword(password) {

    return password.length >= 8;

}
```

---

# 25. Show / Hide Password

### HTML

```html
<input
    type="password"
    id="password"
>

<button
    type="button"
    id="togglePassword"
>
    Show
</button>
```

### JavaScript

```javascript
const password =
    document.querySelector("#password");

const togglePassword =
    document.querySelector("#togglePassword");

togglePassword.addEventListener("click", () => {

    const isPassword =
        password.type === "password";

    password.type =
        isPassword ? "text" : "password";

    togglePassword.textContent =
        isPassword ? "Hide" : "Show";

});
```

---

# 26. Search Filter

### HTML

```html
<input
    type="search"
    id="search"
    placeholder="Search..."
>

<div class="item">
    Apple
</div>

<div class="item">
    Banana
</div>

<div class="item">
    Orange
</div>
```

### JavaScript

```javascript
const search =
    document.querySelector("#search");

const items =
    document.querySelectorAll(".item");

search.addEventListener("input", () => {

    const query =
        search.value.toLowerCase();

    items.forEach(item => {

        const text =
            item.textContent.toLowerCase();

        item.style.display =
            text.includes(query)
                ? ""
                : "none";

    });

});
```

---

# 27. Show / Hide Element

```javascript
function showElement(element) {

    element.classList.add("active");

}

function hideElement(element) {

    element.classList.remove("active");

}

function toggleElement(element) {

    element.classList.toggle("active");

}
```

---

# 28. Toast Notification

### HTML

```html
<div id="toast" class="toast">
    Message
</div>
```

### JavaScript

```javascript
function showToast(message, duration = 3000) {

    const toast =
        document.querySelector("#toast");

    toast.textContent = message;

    toast.classList.add("active");

    setTimeout(() => {

        toast.classList.remove("active");

    }, duration);

}
```

### Usage

```javascript
showToast("Profile updated successfully!");
```

---

# 29. Loading State

```javascript
function setLoading(button, loading) {

    if (loading) {

        button.disabled = true;

        button.dataset.originalText =
            button.textContent;

        button.textContent =
            "Loading...";

    } else {

        button.disabled = false;

        button.textContent =
            button.dataset.originalText;

    }

}
```

### Usage

```javascript
setLoading(button, true);

setTimeout(() => {

    setLoading(button, false);

}, 2000);
```

---

# 30. Disable Button

```javascript
function disableButton(button) {

    button.disabled = true;

}

function enableButton(button) {

    button.disabled = false;

}
```

---

# 31. Copy to Clipboard

```javascript
async function copyText(text) {

    try {

        await navigator.clipboard.writeText(text);

        showToast("Copied!");

    } catch (error) {

        console.error("Copy failed", error);

    }

}
```

### Usage

```javascript
copyText("Hello World");
```

---

# 32. Copy Button

```javascript
const copyButton =
    document.querySelector("#copyBtn");

copyButton.addEventListener("click", async () => {

    const text =
        document.querySelector("#text").textContent;

    await navigator.clipboard.writeText(text);

    showToast("Copied to clipboard!");

});
```

---

# 33. Character Counter

### HTML

```html
<textarea id="message"></textarea>

<p>
    <span id="count">0</span>/200
</p>
```

### JavaScript

```javascript
const message =
    document.querySelector("#message");

const count =
    document.querySelector("#count");

message.addEventListener("input", () => {

    count.textContent =
        message.value.length;

});
```

---

# 34. Password Strength

```javascript
function getPasswordStrength(password) {

    let score = 0;

    if (password.length >= 8) {
        score++;
    }

    if (/[A-Z]/.test(password)) {
        score++;
    }

    if (/[a-z]/.test(password)) {
        score++;
    }

    if (/[0-9]/.test(password)) {
        score++;
    }

    if (/[^A-Za-z0-9]/.test(password)) {
        score++;
    }

    return score;

}
```

---

# 35. Scroll to Top

### HTML

```html
<button id="scrollTop">
    ↑
</button>
```

### JavaScript

```javascript
const scrollTop =
    document.querySelector("#scrollTop");

scrollTop.addEventListener("click", () => {

    window.scrollTo({
        top: 0,
        behavior: "smooth"
    });

});
```

---

# 36. Show Scroll-to-Top Button

```javascript
window.addEventListener("scroll", () => {

    if (window.scrollY > 300) {

        scrollTop.classList.add("active");

    } else {

        scrollTop.classList.remove("active");

    }

});
```

---

# 37. Intersection Observer

Useful for animations and lazy loading.

```javascript
const elements =
    document.querySelectorAll(".animate");

const observer =
    new IntersectionObserver(entries => {

        entries.forEach(entry => {

            if (entry.isIntersecting) {

                entry.target.classList.add("show");

            }

        });

    });

elements.forEach(element => {

    observer.observe(element);

});
```

---

# 38. Lazy Loading Images

### HTML

```html
<img
    src="placeholder.jpg"
    data-src="real-image.jpg"
    class="lazy-image"
    alt="Image"
>
```

### JavaScript

```javascript
const images =
    document.querySelectorAll(".lazy-image");

const imageObserver =
    new IntersectionObserver(entries => {

        entries.forEach(entry => {

            if (entry.isIntersecting) {

                const image = entry.target;

                image.src =
                    image.dataset.src;

                imageObserver.unobserve(image);

            }

        });

    });

images.forEach(image => {

    imageObserver.observe(image);

});
```

---

# 39. Image Preview

### HTML

```html
<input
    type="file"
    id="imageInput"
    accept="image/*"
>

<img
    id="preview"
    alt="Preview"
>
```

### JavaScript

```javascript
const imageInput =
    document.querySelector("#imageInput");

const preview =
    document.querySelector("#preview");

imageInput.addEventListener("change", event => {

    const file =
        event.target.files[0];

    if (!file) return;

    preview.src =
        URL.createObjectURL(file);

});
```

---

# 40. Image Slider

### HTML

```html
<div class="slider">

    <img
        id="sliderImage"
        src="image1.jpg"
        alt="Slider"
    >

    <button id="prev">
        ←
    </button>

    <button id="next">
        →
    </button>

</div>
```

### JavaScript

```javascript
const images = [
    "image1.jpg",
    "image2.jpg",
    "image3.jpg"
];

let currentIndex = 0;

const sliderImage =
    document.querySelector("#sliderImage");

document.querySelector("#next")
    .addEventListener("click", () => {

        currentIndex++;

        if (currentIndex >= images.length) {

            currentIndex = 0;

        }

        sliderImage.src =
            images[currentIndex];

    });

document.querySelector("#prev")
    .addEventListener("click", () => {

        currentIndex--;

        if (currentIndex < 0) {

            currentIndex = images.length - 1;

        }

        sliderImage.src =
            images[currentIndex];

    });
```

---

# 41. Auto Slider

```javascript
setInterval(() => {

    currentIndex++;

    if (currentIndex >= images.length) {

        currentIndex = 0;

    }

    sliderImage.src =
        images[currentIndex];

}, 3000);
```

---

# 42. Confirmation Dialog

```javascript
function confirmAction(message) {

    return window.confirm(message);

}
```

### Usage

```javascript
const confirmed =
    confirmAction(
        "Are you sure you want to delete?"
    );

if (confirmed) {

    console.log("Deleted");

}
```

---

# 43. Delete Confirmation

```javascript
const deleteButtons =
    document.querySelectorAll(".delete-btn");

deleteButtons.forEach(button => {

    button.addEventListener("click", () => {

        const confirmed =
            confirm(
                "Are you sure you want to delete?"
            );

        if (!confirmed) return;

        button.closest(".item").remove();

    });

});
```

---

# 44. LocalStorage

### Save

```javascript
localStorage.setItem(
    "username",
    "Adnan"
);
```

### Get

```javascript
const username =
    localStorage.getItem("username");
```

### Remove

```javascript
localStorage.removeItem("username");
```

### Clear

```javascript
localStorage.clear();
```

---

# 45. Save Object in LocalStorage

```javascript
const user = {
    name: "Adnan",
    age: 22
};

localStorage.setItem(
    "user",
    JSON.stringify(user)
);
```

### Get Object

```javascript
const userData =
    JSON.parse(
        localStorage.getItem("user")
    );
```

---

# 46. SessionStorage

```javascript
sessionStorage.setItem(
    "token",
    "123456"
);

const token =
    sessionStorage.getItem("token");

sessionStorage.removeItem("token");
```

---

# 47. Fetch API — GET

```javascript
async function getUsers() {

    try {

        const response =
            await fetch("/api/users");

        if (!response.ok) {

            throw new Error(
                "Failed to fetch users"
            );

        }

        const data =
            await response.json();

        console.log(data);

    } catch (error) {

        console.error(error);

    }

}
```

---

# 48. Fetch API — POST

```javascript
async function createUser(userData) {

    try {

        const response =
            await fetch("/api/users", {

                method: "POST",

                headers: {
                    "Content-Type":
                        "application/json"
                },

                body:
                    JSON.stringify(userData)

            });

        if (!response.ok) {

            throw new Error(
                "Failed to create user"
            );

        }

        const data =
            await response.json();

        return data;

    } catch (error) {

        console.error(error);

    }

}
```

---

# 49. Fetch API — PUT

```javascript
async function updateUser(id, userData) {

    const response =
        await fetch(`/api/users/${id}`, {

            method: "PUT",

            headers: {
                "Content-Type":
                    "application/json"
            },

            body:
                JSON.stringify(userData)

        });

    return await response.json();

}
```

---

# 50. Fetch API — DELETE

```javascript
async function deleteUser(id) {

    const response =
        await fetch(`/api/users/${id}`, {

            method: "DELETE"

        });

    return await response.json();

}
```

---

# 51. API Loading State

```javascript
async function fetchData() {

    setLoading(button, true);

    try {

        const response =
            await fetch("/api/data");

        const data =
            await response.json();

        return data;

    } catch (error) {

        showToast("Something went wrong");

    } finally {

        setLoading(button, false);

    }

}
```

---

# 52. Render Data into HTML

```javascript
function renderUsers(users) {

    const container =
        document.querySelector("#users");

    container.innerHTML = "";

    users.forEach(user => {

        const card =
            document.createElement("div");

        card.className = "card";

        card.innerHTML = `
            <h3>${user.name}</h3>
            <p>${user.email}</p>
        `;

        container.appendChild(card);

    });

}
```

---

# 53. Create HTML Element

```javascript
const card =
    document.createElement("div");

card.className = "card";

card.textContent =
    "Hello World";

document.body.appendChild(card);
```

---

# 54. Remove Element

```javascript
const element =
    document.querySelector(".card");

element.remove();
```

---

# 55. Add Event Dynamically

```javascript
const button =
    document.createElement("button");

button.textContent =
    "Click Me";

button.addEventListener("click", () => {

    showToast("Clicked!");

});

document.body.appendChild(button);
```

---

# 56. Event Delegation

Useful for dynamically generated elements.

```javascript
const container =
    document.querySelector("#container");

container.addEventListener("click", event => {

    if (
        event.target.classList.contains(
            "delete-btn"
        )
    ) {

        event.target
            .closest(".card")
            .remove();

    }

});
```

---

# 57. Debounce

Useful for search boxes and API calls.

```javascript
function debounce(callback, delay = 500) {

    let timer;

    return (...args) => {

        clearTimeout(timer);

        timer = setTimeout(() => {

            callback(...args);

        }, delay);

    };

}
```

### Usage

```javascript
const searchUsers =
    debounce(query => {

        console.log(
            "Searching:",
            query
        );

    }, 500);
```

---

# 58. Throttle

Useful for scroll and resize events.

```javascript
function throttle(callback, delay = 300) {

    let waiting = false;

    return (...args) => {

        if (waiting) return;

        callback(...args);

        waiting = true;

        setTimeout(() => {

            waiting = false;

        }, delay);

    };

}
```

---

# 59. Window Resize

```javascript
window.addEventListener(
    "resize",
    () => {

        console.log(
            window.innerWidth
        );

    }
);
```

---

# 60. Detect Mobile

```javascript
function isMobile() {

    return window.innerWidth <= 768;

}
```

---

# 61. Current Date

```javascript
const date =
    new Date();

console.log(date);
```

---

# 62. Format Date

```javascript
function formatDate(date) {

    return new Intl.DateTimeFormat(
        "en-IN",
        {
            day: "2-digit",
            month: "short",
            year: "numeric"
        }
    ).format(new Date(date));

}
```

### Usage

```javascript
console.log(
    formatDate("2026-09-15")
);
```

---

# 63. Countdown Timer

```javascript
function countdown(
    element,
    seconds
) {

    let remaining = seconds;

    const timer =
        setInterval(() => {

            element.textContent =
                remaining;

            remaining--;

            if (remaining < 0) {

                clearInterval(timer);

                element.textContent =
                    "Time's up!";

            }

        }, 1000);

}
```

---

# 64. Scroll Progress

### HTML

```html
<div id="scrollProgress"></div>
```

### JavaScript

```javascript
const scrollProgress =
    document.querySelector(
        "#scrollProgress"
    );

window.addEventListener("scroll", () => {

    const scrollTop =
        window.scrollY;

    const documentHeight =
        document.documentElement.scrollHeight
        - window.innerHeight;

    const progress =
        (scrollTop / documentHeight) * 100;

    scrollProgress.style.width =
        `${progress}%`;

});
```

---

# 65. Prevent Multiple Form Submissions

```javascript
form.addEventListener("submit", async event => {

    event.preventDefault();

    button.disabled = true;

    try {

        await submitForm();

    } finally {

        button.disabled = false;

    }

});
```

---

# 66. URL Query Parameters

### URL

```text
/products?id=25
```

### JavaScript

```javascript
const params =
    new URLSearchParams(
        window.location.search
    );

const id =
    params.get("id");

console.log(id);
```

---

# 67. Redirect

```javascript
window.location.href =
    "/dashboard";
```

---

# 68. Open New Tab

```javascript
window.open(
    "https://example.com",
    "_blank"
);
```

---

# 69. Browser Back

```javascript
window.history.back();
```

---

# 70. Browser Forward

```javascript
window.history.forward();
```

---

# 71. Simple Router

```javascript
function navigate(path) {

    window.history.pushState(
        {},
        "",
        path
    );

    handleRoute();

}

function handleRoute() {

    const path =
        window.location.pathname;

    if (path === "/") {

        console.log("Home");

    } else if (path === "/about") {

        console.log("About");

    } else {

        console.log("404");

    }

}

window.addEventListener(
    "popstate",
    handleRoute
);

handleRoute();
```

---

# 72. Utility Functions

```javascript
const UI = {

    show(element) {

        element.classList.add("active");

    },

    hide(element) {

        element.classList.remove("active");

    },

    toggle(element) {

        element.classList.toggle("active");

    },

    toast(message) {

        showToast(message);

    },

    loading(button, state) {

        setLoading(
            button,
            state
        );

    }

};
```

### Usage

```javascript
UI.show(modal);

UI.hide(modal);

UI.toggle(menu);

UI.toast("Saved!");

UI.loading(button, true);
```

---

# 73. Complete UI SDK Object

```javascript
const AppUI = {

    // Modal
    openModal(modal) {

        modal.classList.add("active");

    },

    closeModal(modal) {

        modal.classList.remove("active");

    },


    // Dropdown
    toggleDropdown(dropdown) {

        dropdown.classList.toggle("active");

    },


    // Toast
    toast(message, duration = 3000) {

        const toast =
            document.querySelector("#toast");

        toast.textContent = message;

        toast.classList.add("active");

        setTimeout(() => {

            toast.classList.remove("active");

        }, duration);

    },


    // Loading
    loading(button, state) {

        button.disabled = state;

        if (state) {

            button.dataset.text =
                button.textContent;

            button.textContent =
                "Loading...";

        } else {

            button.textContent =
                button.dataset.text;

        }

    },


    // Scroll
    scrollTop() {

        window.scrollTo({

            top: 0,

            behavior: "smooth"

        });

    },


    // Storage
    save(key, value) {

        localStorage.setItem(
            key,
            JSON.stringify(value)
        );

    },


    get(key) {

        const value =
            localStorage.getItem(key);

        return value
            ? JSON.parse(value)
            : null;

    },


    remove(key) {

        localStorage.removeItem(key);

    }

};
```

---

# 74. Example Project Structure

```text
project/
│
├── index.html
│
├── css/
│   ├── style.css
│   └── components.css
│
├── js/
│   ├── main.js
│   ├── ui.js
│   ├── api.js
│   ├── form.js
│   └── utils.js
│
└── assets/
    ├── images/
    └── icons/
```

---

# 75. Recommended JS Architecture

```text
                    WEBSITE
                       │
                       ▼
                   main.js
                       │
        ┌──────────────┼──────────────┐
        │              │              │
        ▼              ▼              ▼
       ui.js         api.js        utils.js
        │              │              │
        ▼              ▼              ▼
    UI Logic       Backend API     Helpers
        │              │              │
        └──────────────┼──────────────┘
                       ▼
                   Browser UI
```

---

# 76. JavaScript Responsibility

```text
HTML
  ↓
Structure

CSS
  ↓
Design

JavaScript
  ↓
Behaviour
```

### JavaScript Handles

```text
✓ Button clicks
✓ Navbar menu
✓ Dropdown
✓ Modal
✓ Tabs
✓ Accordion
✓ Forms
✓ Validation
✓ Search
✓ Filter
✓ Slider
✓ Dark mode
✓ Toast
✓ Loading
✓ API calls
✓ LocalStorage
✓ Authentication UI
✓ Dynamic HTML
✓ Animations
✓ Scroll behaviour
✓ File preview
✓ Pagination
✓ Countdown
```

---

# 77. Real Website Flow

```text
User
 │
 ▼
HTML
 │
 ▼
CSS
 │
 ▼
JavaScript Event
 │
 ├── Click
 ├── Submit
 ├── Input
 ├── Scroll
 └── Load
 │
 ▼
JavaScript Logic
 │
 ├── Validate
 ├── Change UI
 ├── Call API
 ├── Store Data
 └── Render Data
 │
 ▼
Updated Website
```

---

# 78. Frontend + Flask Backend Flow

```text
                Browser
                   │
                   ▼
             HTML + CSS + JS
                   │
                   │ fetch()
                   ▼
              Flask API
                   │
                   ▼
              PostgreSQL
                   │
                   ▼
              Flask Response
                   │
                   ▼
             JavaScript
                   │
                   ▼
              Update DOM
```

### Example

```javascript
async function loadUsers() {

    const response =
        await fetch("/api/users");

    const users =
        await response.json();

    renderUsers(users);

}
```

---

# 79. Final JavaScript SDK Checklist

```text
DOM
□ querySelector
□ querySelectorAll
□ getElementById
□ createElement
□ remove
□ classList
□ innerHTML
□ textContent

EVENTS
□ click
□ submit
□ input
□ change
□ scroll
□ resize
□ keydown

UI
□ Navbar
□ Mobile Menu
□ Modal
□ Dropdown
□ Tabs
□ Accordion
□ Toast
□ Loading
□ Slider
□ Dark Mode
□ Scroll Top
□ Progress Bar

FORMS
□ Validation
□ Email Validation
□ Password Validation
□ File Upload
□ Image Preview
□ Character Counter
□ Password Toggle

DATA
□ LocalStorage
□ SessionStorage
□ JSON
□ Fetch GET
□ Fetch POST
□ Fetch PUT
□ Fetch DELETE

UX
□ Smooth Scroll
□ Lazy Loading
□ Intersection Observer
□ Debounce
□ Throttle
□ Countdown
□ Confirmation

ADVANCED
□ Dynamic HTML
□ Event Delegation
□ URL Parameters
□ History API
□ Simple Router
□ API Error Handling
```
