# CSS SDK BY MD
## HERE ALL TYPE OF METHODS TO MAKE WELL DESIGN>>
```
@import url("https://fonts.googleapis.com/css2?family=Mulish:ital,wght@0,200..1000;1,200..1000&display=swap");

:root {
  --primary-color: #fe5b3e;
  --text-dark: #0f172a;
  --text-light: #475569;
  --extra-light: #f2f2f2;
  --white: #ffffff;
  --max-width: 1200px;
  --gradient: linear-gradient(to bottom, #fe5c3c, #fc8023);
}
```
### This is root to use all css file...
```
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
```
### This is body css style...
### NOTE :- All size in rem

# CSS Component Library / Reusable CSS Notes

Ye notes real-world web development me commonly used CSS structures aur components ke liye hain.

---

# 1. CSS Reset

CSS reset ka use browser ke default margin, padding aur sizing ko reset karne ke liye hota hai.

```css
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

html {
    scroll-behavior: smooth;
}

body {
    font-family: Arial, sans-serif;
    line-height: 1.6;
    color: #111827;
    background: #ffffff;
}

img {
    max-width: 100%;
    display: block;
}

a {
    text-decoration: none;
    color: inherit;
}

button,
input,
textarea,
select {
    font: inherit;
}
```

---

# 2. CSS Variables

Variables me common colors, radius, shadows aur transition store kar sakte hain.

```css
:root {
    --primary: #2563eb;
    --primary-dark: #1d4ed8;

    --success: #16a34a;
    --danger: #dc2626;
    --warning: #f59e0b;

    --dark: #111827;
    --text: #374151;
    --muted: #6b7280;

    --white: #ffffff;
    --light: #f3f4f6;
    --border: #e5e7eb;

    --radius-sm: 6px;
    --radius-md: 10px;
    --radius-lg: 16px;

    --shadow-sm: 0 2px 6px rgba(0, 0, 0, 0.08);
    --shadow-md: 0 5px 15px rgba(0, 0, 0, 0.10);

    --transition: 0.3s ease;
}
```

---

# 3. Container

Website ke content ko center me rakhne ke liye container use hota hai.

```css
.container {
    width: 90%;
    max-width: 1200px;
    margin: auto;
}
```

---

# 4. Navbar

## HTML

```html
<nav class="navbar">
    <div class="container navbar-container">

        <a href="#" class="logo">
            MyWebsite
        </a>

        <div class="nav-links">
            <a href="#">Home</a>
            <a href="#">About</a>
            <a href="#">Services</a>
            <a href="#">Contact</a>
        </div>

        <button class="menu-btn">
            ☰
        </button>

    </div>
</nav>
```

## CSS

```css
.navbar {
    width: 100%;
    padding: 18px 0;
    border-bottom: 1px solid var(--border);
    background: var(--white);
}

.navbar-container {
    display: flex;
    align-items: center;
    justify-content: space-between;
}

.logo {
    font-size: 24px;
    font-weight: bold;
    color: var(--primary);
}

.nav-links {
    display: flex;
    gap: 30px;
}

.nav-links a {
    color: var(--text);
    transition: var(--transition);
}

.nav-links a:hover {
    color: var(--primary);
}

.menu-btn {
    display: none;
}
```

---

# 5. Buttons

```css
.btn {
    display: inline-flex;
    align-items: center;
    justify-content: center;
    gap: 8px;

    padding: 12px 22px;

    border: none;
    border-radius: var(--radius-md);

    cursor: pointer;

    transition: var(--transition);
}

.btn-primary {
    background: var(--primary);
    color: white;
}

.btn-primary:hover {
    background: var(--primary-dark);
}

.btn-secondary {
    background: var(--light);
    color: var(--dark);
}

.btn-success {
    background: var(--success);
    color: white;
}

.btn-danger {
    background: var(--danger);
    color: white;
}

.btn-outline {
    background: transparent;
    border: 1px solid var(--primary);
    color: var(--primary);
}

.btn-outline:hover {
    background: var(--primary);
    color: white;
}

.btn-sm {
    padding: 8px 14px;
    font-size: 14px;
}

.btn-lg {
    padding: 15px 30px;
    font-size: 18px;
}
```

---

# 6. Hero Section

```css
.hero {
    min-height: 80vh;

    display: flex;
    align-items: center;

    padding: 80px 0;
}

.hero-container {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 50px;
    align-items: center;
}

.hero-title {
    font-size: 52px;
    line-height: 1.1;
    margin-bottom: 20px;
}

.hero-description {
    font-size: 18px;
    color: var(--muted);
    margin-bottom: 30px;
}

.hero-buttons {
    display: flex;
    gap: 15px;
}
```

---

# 7. Card

```css
.card {
    background: white;

    border: 1px solid var(--border);
    border-radius: var(--radius-lg);

    padding: 25px;

    box-shadow: var(--shadow-sm);

    transition: var(--transition);
}

.card:hover {
    transform: translateY(-5px);
    box-shadow: var(--shadow-md);
}

.card-title {
    font-size: 20px;
    margin-bottom: 10px;
}

.card-text {
    color: var(--muted);
}

.card-footer {
    margin-top: 20px;
    padding-top: 15px;

    border-top: 1px solid var(--border);
}
```

---

# 8. Card Grid

```css
.card-grid {
    display: grid;

    grid-template-columns: repeat(3, 1fr);

    gap: 25px;
}
```

---

# 9. Image Card

```css
.image-card {
    overflow: hidden;

    border-radius: var(--radius-lg);

    background: white;

    box-shadow: var(--shadow-sm);
}

.image-card img {
    width: 100%;
    height: 220px;

    object-fit: cover;
}

.image-card-content {
    padding: 20px;
}
```

---

# 10. Profile Card

```css
.profile-card {
    text-align: center;

    padding: 30px;

    border: 1px solid var(--border);
    border-radius: var(--radius-lg);
}

.profile-image {
    width: 90px;
    height: 90px;

    margin: auto;
    margin-bottom: 15px;

    border-radius: 50%;

    object-fit: cover;
}

.profile-name {
    font-size: 20px;
    font-weight: bold;
}

.profile-role {
    color: var(--muted);
}
```

---

# 11. Form

```css
.form-group {
    margin-bottom: 20px;
}

.form-label {
    display: block;
    margin-bottom: 8px;
    font-weight: 500;
}

.form-input,
.form-select,
.form-textarea {
    width: 100%;

    padding: 12px 14px;

    border: 1px solid var(--border);
    border-radius: var(--radius-md);

    outline: none;

    transition: var(--transition);
}

.form-input:focus,
.form-select:focus,
.form-textarea:focus {
    border-color: var(--primary);
}

.form-textarea {
    min-height: 120px;
    resize: vertical;
}
```

---

# 12. Search Box

```css
.search-box {
    display: flex;
    align-items: center;

    border: 1px solid var(--border);
    border-radius: var(--radius-md);

    padding: 5px 10px;
}

.search-box input {
    flex: 1;

    border: none;
    outline: none;

    padding: 10px;
}

.search-box button {
    border: none;

    background: var(--primary);
    color: white;

    padding: 10px 15px;

    border-radius: var(--radius-sm);

    cursor: pointer;
}
```

---

# 13. Badge / Tag

```css
.badge {
    display: inline-block;

    padding: 5px 10px;

    border-radius: 50px;

    font-size: 12px;
    font-weight: 600;
}

.badge-primary {
    background: #dbeafe;
    color: #1d4ed8;
}

.badge-success {
    background: #dcfce7;
    color: #15803d;
}

.badge-danger {
    background: #fee2e2;
    color: #b91c1c;
}

.badge-warning {
    background: #fef3c7;
    color: #b45309;
}
```

---

# 14. Alert

```css
.alert {
    padding: 15px 20px;

    border-radius: var(--radius-md);

    margin-bottom: 20px;
}

.alert-success {
    background: #dcfce7;
    color: #166534;
}

.alert-danger {
    background: #fee2e2;
    color: #991b1b;
}

.alert-warning {
    background: #fef3c7;
    color: #92400e;
}

.alert-info {
    background: #dbeafe;
    color: #1e40af;
}
```

---

# 15. Modal / Popup

```css
.modal {
    position: fixed;

    inset: 0;

    display: flex;
    align-items: center;
    justify-content: center;

    background: rgba(0, 0, 0, 0.5);

    z-index: 1000;
}

.modal-content {
    width: 90%;
    max-width: 500px;

    background: white;

    padding: 30px;

    border-radius: var(--radius-lg);
}

.modal-header {
    display: flex;
    align-items: center;
    justify-content: space-between;

    margin-bottom: 20px;
}

.modal-close {
    border: none;

    background: none;

    font-size: 24px;

    cursor: pointer;
}
```

---

# 16. Sidebar

```css
.sidebar {
    width: 260px;
    min-height: 100vh;

    padding: 25px;

    background: var(--dark);
    color: white;
}

.sidebar-menu {
    display: flex;
    flex-direction: column;

    gap: 8px;
}

.sidebar-link {
    padding: 12px 15px;

    border-radius: var(--radius-md);

    transition: var(--transition);
}

.sidebar-link:hover {
    background: rgba(255, 255, 255, 0.1);
}
```

---

# 17. Dashboard Layout

```css
.dashboard {
    display: flex;
    min-height: 100vh;
}

.dashboard-main {
    flex: 1;

    padding: 30px;

    background: var(--light);
}
```

---

# 18. Stats Card

```css
.stats-grid {
    display: grid;

    grid-template-columns: repeat(4, 1fr);

    gap: 20px;
}

.stats-card {
    padding: 25px;

    background: white;

    border-radius: var(--radius-lg);

    box-shadow: var(--shadow-sm);
}

.stats-title {
    color: var(--muted);

    font-size: 14px;
}

.stats-number {
    font-size: 30px;
    font-weight: bold;

    margin-top: 8px;
}
```

---

# 19. Pricing Card

```css
.pricing-card {
    padding: 35px;

    text-align: center;

    border: 1px solid var(--border);

    border-radius: var(--radius-lg);
}

.price {
    font-size: 42px;
    font-weight: bold;

    margin: 20px 0;
}

.price span {
    font-size: 16px;
    color: var(--muted);
}

.pricing-features {
    list-style: none;

    margin: 25px 0;

    display: flex;
    flex-direction: column;

    gap: 12px;
}
```

---

# 20. Table

```css
.table-container {
    overflow-x: auto;
}

.table {
    width: 100%;

    border-collapse: collapse;

    background: white;
}

.table th,
.table td {
    padding: 14px;

    text-align: left;

    border-bottom: 1px solid var(--border);
}

.table th {
    background: var(--light);

    font-weight: 600;
}

.table tr:hover {
    background: #f9fafb;
}
```

---

# 21. Pagination

```css
.pagination {
    display: flex;

    gap: 8px;

    margin-top: 25px;
}

.pagination a {
    width: 40px;
    height: 40px;

    display: flex;
    align-items: center;
    justify-content: center;

    border: 1px solid var(--border);

    border-radius: var(--radius-sm);
}

.pagination a.active {
    background: var(--primary);

    color: white;
}
```

---

# 22. Avatar

```css
.avatar {
    width: 45px;
    height: 45px;

    border-radius: 50%;

    object-fit: cover;
}

.avatar-sm {
    width: 32px;
    height: 32px;
}

.avatar-lg {
    width: 70px;
    height: 70px;
}
```

---

# 23. Toast / Notification

```css
.toast {
    position: fixed;

    right: 20px;
    bottom: 20px;

    padding: 15px 20px;

    background: var(--dark);

    color: white;

    border-radius: var(--radius-md);

    box-shadow: var(--shadow-md);

    z-index: 2000;
}
```

---

# 24. Loading Spinner

```css
.spinner {
    width: 40px;
    height: 40px;

    border: 4px solid var(--border);

    border-top-color: var(--primary);

    border-radius: 50%;

    animation: spin 1s linear infinite;
}

@keyframes spin {
    to {
        transform: rotate(360deg);
    }
}
```

---

# 25. Skeleton Loading

```css
.skeleton {
    background: #e5e7eb;

    border-radius: var(--radius-sm);

    animation: skeleton-loading 1.5s infinite;
}

@keyframes skeleton-loading {
    0% {
        opacity: 0.5;
    }

    50% {
        opacity: 1;
    }

    100% {
        opacity: 0.5;
    }
}
```

---

# 26. Dropdown

```css
.dropdown {
    position: relative;

    display: inline-block;
}

.dropdown-menu {
    position: absolute;

    top: 100%;
    right: 0;

    min-width: 180px;

    margin-top: 8px;

    padding: 8px;

    background: white;

    border: 1px solid var(--border);

    border-radius: var(--radius-md);

    box-shadow: var(--shadow-md);

    z-index: 100;
}

.dropdown-item {
    display: block;

    padding: 10px 12px;

    border-radius: var(--radius-sm);
}

.dropdown-item:hover {
    background: var(--light);
}
```

---

# 27. Checkbox / Radio

```css
.checkbox-group,
.radio-group {
    display: flex;

    align-items: center;

    gap: 8px;

    margin-bottom: 10px;
}

.checkbox-group input,
.radio-group input {
    accent-color: var(--primary);
}
```

---

# 28. Progress Bar

```css
.progress {
    width: 100%;
    height: 10px;

    background: var(--light);

    border-radius: 50px;

    overflow: hidden;
}

.progress-bar {
    height: 100%;

    width: 70%;

    background: var(--primary);

    border-radius: 50px;
}
```

---

# 29. Accordion

```css
.accordion {
    border: 1px solid var(--border);

    border-radius: var(--radius-md);

    overflow: hidden;
}

.accordion-header {
    width: 100%;

    padding: 18px;

    border: none;

    background: white;

    text-align: left;

    cursor: pointer;
}

.accordion-content {
    padding: 18px;

    border-top: 1px solid var(--border);
}
```

---

# 30. Footer

```css
.footer {
    padding: 60px 0;

    background: var(--dark);

    color: white;
}

.footer-grid {
    display: grid;

    grid-template-columns: repeat(4, 1fr);

    gap: 30px;
}

.footer-links {
    display: flex;

    flex-direction: column;

    gap: 10px;
}

.footer-links a {
    color: #d1d5db;
}

.footer-links a:hover {
    color: white;
}
```

---

# 31. Flexbox Utilities

Flexbox ke common reusable classes.

```css
.flex {
    display: flex;
}

.flex-center {
    display: flex;

    align-items: center;
    justify-content: center;
}

.flex-between {
    display: flex;

    align-items: center;
    justify-content: space-between;
}

.flex-column {
    display: flex;

    flex-direction: column;
}

.align-center {
    align-items: center;
}

.justify-center {
    justify-content: center;
}

.justify-between {
    justify-content: space-between;
}

.gap-1 {
    gap: 10px;
}

.gap-2 {
    gap: 20px;
}

.gap-3 {
    gap: 30px;
}
```

---

# 32. Grid Utilities

```css
.grid {
    display: grid;
}

.grid-2 {
    grid-template-columns: repeat(2, 1fr);

    gap: 20px;
}

.grid-3 {
    grid-template-columns: repeat(3, 1fr);

    gap: 20px;
}

.grid-4 {
    grid-template-columns: repeat(4, 1fr);

    gap: 20px;
}
```

---

# 33. Common Utility Classes

```css
.text-center {
    text-align: center;
}

.text-left {
    text-align: left;
}

.text-right {
    text-align: right;
}

.w-full {
    width: 100%;
}

.h-full {
    height: 100%;
}

.hidden {
    display: none;
}

.rounded {
    border-radius: var(--radius-md);
}

.shadow {
    box-shadow: var(--shadow-md);
}

.mt-1 {
    margin-top: 10px;
}

.mt-2 {
    margin-top: 20px;
}

.mt-3 {
    margin-top: 30px;
}

.mb-1 {
    margin-bottom: 10px;
}

.mb-2 {
    margin-bottom: 20px;
}

.mb-3 {
    margin-bottom: 30px;
}
```

---

# 34. Responsive Design

Responsive CSS website ko mobile, tablet aur desktop ke liye adapt karta hai.

```css
@media (max-width: 1024px) {

    .hero-container {
        grid-template-columns: 1fr;
    }

    .stats-grid {
        grid-template-columns: repeat(2, 1fr);
    }

    .card-grid {
        grid-template-columns: repeat(2, 1fr);
    }

    .footer-grid {
        grid-template-columns: repeat(2, 1fr);
    }
}


@media (max-width: 768px) {

    .nav-links {
        display: none;
    }

    .menu-btn {
        display: block;
    }

    .hero-title {
        font-size: 38px;
    }

    .card-grid {
        grid-template-columns: 1fr;
    }

    .stats-grid {
        grid-template-columns: 1fr;
    }

    .footer-grid {
        grid-template-columns: 1fr;
    }

    .dashboard {
        flex-direction: column;
    }

    .sidebar {
        width: 100%;
        min-height: auto;
    }
}


@media (max-width: 480px) {

    .container {
        width: 94%;
    }

    .hero {
        padding: 50px 0;
    }

    .hero-title {
        font-size: 32px;
    }

    .hero-buttons {
        flex-direction: column;
    }

    .btn {
        width: 100%;
    }
}
```

---

# CSS Component List

Real-world projects me commonly ye components baar-baar use hote hain:

* Reset
* CSS Variables
* Container
* Navbar
* Hero Section
* Buttons
* Cards
* Card Grid
* Image Card
* Profile Card
* Forms
* Search Box
* Badge / Tag
* Alert
* Modal
* Sidebar
* Dashboard
* Stats Card
* Pricing Card
* Table
* Pagination
* Avatar
* Toast / Notification
* Loading Spinner
* Skeleton Loading
* Dropdown
* Checkbox
* Radio Button
* Progress Bar
* Accordion
* Footer
* Flexbox Utilities
* Grid Utilities
* Spacing Utilities
* Responsive Design

## Important CSS Concepts

### `display: flex`

Elements ko row ya column me arrange karne ke liye.

```css
.container {
    display: flex;
}
```

### `display: grid`

Rows aur columns based layouts ke liye.

```css
.container {
    display: grid;
}
```

### `position`

Element ki positioning control karne ke liye.

```css
.element {
    position: relative;
}

.child {
    position: absolute;
}
```

Common values:

* `static`
* `relative`
* `absolute`
* `fixed`
* `sticky`

### `margin`

Element ke bahar space.

```css
.box {
    margin: 20px;
}
```

### `padding`

Element ke andar space.

```css
.box {
    padding: 20px;
}
```

### `gap`

Flex/Grid items ke beech space.

```css
.container {
    display: flex;
    gap: 20px;
}
```

### `transition`

Property change ko smooth banane ke liye.

```css
button {
    transition: 0.3s ease;
}
```

### `transform`

Element ko move, rotate ya scale karne ke liye.

```css
.card:hover {
    transform: translateY(-5px);
}
```

### `z-index`

Overlapping elements ka layer order control karta hai.

```css
.modal {
    position: fixed;
    z-index: 1000;
}
```

---

# Recommended CSS File Structure

Large project me CSS ko components ke according separate files me bhi divide kar sakte ho:

```text
css/
│
├── reset.css
├── variables.css
├── global.css
│
├── navbar.css
├── buttons.css
├── cards.css
├── forms.css
├── modal.css
├── sidebar.css
├── dashboard.css
├── table.css
├── footer.css
│
├── utilities.css
└── responsive.css
```

Small project me ek hi `style.css` file rakh sakte ho:

```text
style.css
│
├── Reset
├── Variables
├── Global
├── Navbar
├── Hero
├── Buttons
├── Cards
├── Forms
├── Modal
├── Sidebar
├── Dashboard
├── Footer
├── Utilities
└── Responsive
```

> **Tip:** CSS ka pura code yaad karne ki zarurat nahi hai. Pehle `flex`, `grid`, `position`, `margin`, `padding`, `width`, `height`, `border`, `background`, `font`, `transition`, `transform` aur `@media` ko achhe se samjho. Baaki components ko reference/template ki tarah use kar sakte ho.
