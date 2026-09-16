# HTML Component SDK

> Reusable HTML structure for real-world projects.

---

## 1. Basic HTML Structure

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <title>My Website</title>

    <link rel="stylesheet" href="style.css">
</head>

<body>

    <main>
        <!-- Page Content -->
    </main>

    <script src="script.js"></script>
</body>
</html>
```

---

# 2. Semantic Page Structure

```html
<header>
    <!-- Navbar / Header -->
</header>

<nav>
    <!-- Navigation -->
</nav>

<main>

    <section>
        <!-- Section -->
    </section>

    <article>
        <!-- Article -->
    </article>

</main>

<aside>
    <!-- Sidebar -->
</aside>

<footer>
    <!-- Footer -->
</footer>
```

---

# 3. Container

```html
<div class="container">

    <h1>Page Title</h1>

    <p>
        Page content goes here.
    </p>

</div>
```

---

# 4. Navbar

```html
<header class="navbar">

    <div class="navbar-logo">
        <a href="/">MyLogo</a>
    </div>

    <nav class="navbar-links">

        <a href="/">Home</a>
        <a href="/about">About</a>
        <a href="/services">Services</a>
        <a href="/contact">Contact</a>

    </nav>

    <div class="navbar-actions">

        <a href="/login" class="btn">
            Login
        </a>

        <a href="/signup" class="btn">
            Sign Up
        </a>

    </div>

</header>
```

---

# 5. Mobile Navbar

```html
<header class="navbar">

    <a href="/" class="logo">
        MyLogo
    </a>

    <button
        class="menu-btn"
        id="menuBtn"
        aria-label="Open menu"
    >
        ☰
    </button>

    <nav class="mobile-menu" id="mobileMenu">

        <a href="/">Home</a>
        <a href="/about">About</a>
        <a href="/services">Services</a>
        <a href="/contact">Contact</a>

    </nav>

</header>
```

---

# 6. Hero Section

```html
<section class="hero">

    <div class="hero-content">

        <span class="badge">
            New
        </span>

        <h1>
            Build Something Amazing
        </h1>

        <p>
            Create modern and powerful websites
            using reusable components.
        </p>

        <div class="hero-actions">

            <a href="#get-started" class="btn">
                Get Started
            </a>

            <a href="#learn-more" class="btn">
                Learn More
            </a>

        </div>

    </div>

</section>
```

---

# 7. Section Header

```html
<div class="section-header">

    <span class="badge">
        Features
    </span>

    <h2>
        Everything You Need
    </h2>

    <p>
        Simple tools for building modern applications.
    </p>

</div>
```

---

# 8. Card

```html
<div class="card">

    <h3>
        Card Title
    </h3>

    <p>
        This is a reusable card component.
    </p>

    <a href="#" class="btn">
        Learn More
    </a>

</div>
```

---

# 9. Card with Image

```html
<article class="card">

    <img
        src="image.jpg"
        alt="Product image"
    >

    <div class="card-content">

        <span class="badge">
            Technology
        </span>

        <h3>
            Product Title
        </h3>

        <p>
            Product description goes here.
        </p>

        <a href="#" class="btn">
            View Details
        </a>

    </div>

</article>
```

---

# 10. Card Grid

```html
<section class="card-grid">

    <article class="card">
        <h3>Card One</h3>
        <p>Card description.</p>
    </article>

    <article class="card">
        <h3>Card Two</h3>
        <p>Card description.</p>
    </article>

    <article class="card">
        <h3>Card Three</h3>
        <p>Card description.</p>
    </article>

</section>
```

---

# 11. Profile Card

```html
<div class="profile-card">

    <img
        src="profile.jpg"
        alt="John Doe"
        class="avatar"
    >

    <h3>
        John Doe
    </h3>

    <p>
        Full Stack Developer
    </p>

    <div class="profile-actions">

        <button class="btn">
            Follow
        </button>

        <button class="btn">
            Message
        </button>

    </div>

</div>
```

---

# 12. Avatar

```html
<img
    src="profile.jpg"
    alt="User profile"
    class="avatar"
>
```

---

# 13. Badge / Tag

```html
<span class="badge">
    New
</span>

<span class="badge">
    Featured
</span>

<span class="badge">
    Popular
</span>
```

---

# 14. Button

```html
<button type="button" class="btn">
    Click Me
</button>
```

---

# 15. Button Group

```html
<div class="btn-group">

    <button class="btn">
        Save
    </button>

    <button class="btn">
        Cancel
    </button>

</div>
```

---

# 16. Login Form

```html
<form class="form">

    <h2>
        Login
    </h2>

    <div class="form-group">

        <label for="email">
            Email
        </label>

        <input
            type="email"
            id="email"
            name="email"
            placeholder="Enter your email"
            required
        >

    </div>

    <div class="form-group">

        <label for="password">
            Password
        </label>

        <input
            type="password"
            id="password"
            name="password"
            placeholder="Enter your password"
            required
        >

    </div>

    <button
        type="submit"
        class="btn"
    >
        Login
    </button>

</form>
```

---

# 17. Signup Form

```html
<form class="form">

    <h2>
        Create Account
    </h2>

    <div class="form-group">

        <label for="name">
            Full Name
        </label>

        <input
            type="text"
            id="name"
            name="name"
            placeholder="Enter your name"
            required
        >

    </div>

    <div class="form-group">

        <label for="email">
            Email
        </label>

        <input
            type="email"
            id="email"
            name="email"
            placeholder="Enter your email"
            required
        >

    </div>

    <div class="form-group">

        <label for="password">
            Password
        </label>

        <input
            type="password"
            id="password"
            name="password"
            placeholder="Create password"
            required
        >

    </div>

    <button type="submit" class="btn">
        Create Account
    </button>

</form>
```

---

# 18. Search Box

```html
<form class="search-box">

    <input
        type="search"
        name="search"
        placeholder="Search..."
        aria-label="Search"
    >

    <button type="submit" class="btn">
        Search
    </button>

</form>
```

---

# 19. Select Dropdown

```html
<div class="form-group">

    <label for="category">
        Category
    </label>

    <select id="category" name="category">

        <option value="">
            Select Category
        </option>

        <option value="tech">
            Technology
        </option>

        <option value="business">
            Business
        </option>

        <option value="education">
            Education
        </option>

    </select>

</div>
```

---

# 20. Checkbox

```html
<label class="checkbox">

    <input
        type="checkbox"
        name="terms"
    >

    <span>
        I agree to the Terms & Conditions
    </span>

</label>
```

---

# 21. Radio Buttons

```html
<fieldset>

    <legend>
        Select Gender
    </legend>

    <label>
        <input
            type="radio"
            name="gender"
            value="male"
        >
        Male
    </label>

    <label>
        <input
            type="radio"
            name="gender"
            value="female"
        >
        Female
    </label>

</fieldset>
```

---

# 22. Textarea

```html
<div class="form-group">

    <label for="message">
        Message
    </label>

    <textarea
        id="message"
        name="message"
        rows="5"
        placeholder="Write your message..."
    ></textarea>

</div>
```

---

# 23. File Upload

```html
<div class="form-group">

    <label for="file">
        Upload File
    </label>

    <input
        type="file"
        id="file"
        name="file"
    >

</div>
```

---

# 24. Alert

```html
<div class="alert">

    <strong>
        Success!
    </strong>

    <p>
        Your changes have been saved.
    </p>

</div>
```

---

# 25. Error Message

```html
<div class="alert alert-error">

    <strong>
        Error
    </strong>

    <p>
        Something went wrong.
    </p>

</div>
```

---

# 26. Modal / Popup

```html
<div
    class="modal"
    id="modal"
    role="dialog"
    aria-modal="true"
    aria-labelledby="modalTitle"
>

    <div class="modal-content">

        <button
            class="modal-close"
            type="button"
            aria-label="Close"
        >
            ×
        </button>

        <h2 id="modalTitle">
            Confirm Action
        </h2>

        <p>
            Are you sure you want to continue?
        </p>

        <div class="modal-actions">

            <button class="btn">
                Cancel
            </button>

            <button class="btn">
                Confirm
            </button>

        </div>

    </div>

</div>
```

---

# 27. Sidebar

```html
<aside class="sidebar">

    <div class="sidebar-header">

        <h2>
            Dashboard
        </h2>

    </div>

    <nav class="sidebar-menu">

        <a href="/dashboard">
            Dashboard
        </a>

        <a href="/users">
            Users
        </a>

        <a href="/orders">
            Orders
        </a>

        <a href="/settings">
            Settings
        </a>

    </nav>

</aside>
```

---

# 28. Dashboard Layout

```html
<div class="dashboard">

    <aside class="sidebar">

        <nav>

            <a href="#">
                Dashboard
            </a>

            <a href="#">
                Users
            </a>

            <a href="#">
                Orders
            </a>

            <a href="#">
                Settings
            </a>

        </nav>

    </aside>

    <main class="dashboard-content">

        <header>
            <h1>
                Dashboard
            </h1>
        </header>

        <section>
            <!-- Dashboard Content -->
        </section>

    </main>

</div>
```

---

# 29. Stats Card

```html
<div class="stats-card">

    <span class="stats-label">
        Total Users
    </span>

    <strong class="stats-value">
        12,540
    </strong>

    <span class="stats-change">
        +12.5%
    </span>

</div>
```

---

# 30. Pricing Card

```html
<div class="pricing-card">

    <span class="badge">
        Popular
    </span>

    <h3>
        Pro
    </h3>

    <div class="price">
        ₹499
        <span>/month</span>
    </div>

    <ul>

        <li>
            Unlimited Projects
        </li>

        <li>
            Priority Support
        </li>

        <li>
            Advanced Analytics
        </li>

    </ul>

    <button class="btn">
        Choose Plan
    </button>

</div>
```

---

# 31. Table

```html
<div class="table-wrapper">

    <table>

        <thead>

            <tr>
                <th>ID</th>
                <th>Name</th>
                <th>Email</th>
                <th>Status</th>
            </tr>

        </thead>

        <tbody>

            <tr>
                <td>1</td>
                <td>Adnan</td>
                <td>adnan@example.com</td>
                <td>Active</td>
            </tr>

            <tr>
                <td>2</td>
                <td>Rahul</td>
                <td>rahul@example.com</td>
                <td>Inactive</td>
            </tr>

        </tbody>

    </table>

</div>
```

---

# 32. Pagination

```html
<nav
    class="pagination"
    aria-label="Pagination"
>

    <a href="#">
        Previous
    </a>

    <a href="#">
        1
    </a>

    <a href="#">
        2
    </a>

    <a href="#">
        3
    </a>

    <a href="#">
        Next
    </a>

</nav>
```

---

# 33. Toast Notification

```html
<div
    class="toast"
    role="alert"
>

    <strong>
        Success
    </strong>

    <p>
        Profile updated successfully.
    </p>

    <button
        type="button"
        aria-label="Close"
    >
        ×
    </button>

</div>
```

---

# 34. Loading Spinner

```html
<div
    class="spinner"
    role="status"
    aria-label="Loading"
></div>
```

---

# 35. Skeleton Loading

```html
<div class="skeleton-card">

    <div class="skeleton skeleton-image"></div>

    <div class="skeleton skeleton-title"></div>

    <div class="skeleton skeleton-text"></div>

    <div class="skeleton skeleton-text"></div>

</div>
```

---

# 36. Progress Bar

```html
<div class="progress-container">

    <div class="progress-info">

        <span>
            Progress
        </span>

        <span>
            75%
        </span>

    </div>

    <div class="progress">

        <div
            class="progress-bar"
            style="width: 75%;"
        ></div>

    </div>

</div>
```

---

# 37. Accordion

```html
<div class="accordion">

    <details>

        <summary>
            What is HTML?
        </summary>

        <p>
            HTML is used to structure web pages.
        </p>

    </details>

    <details>

        <summary>
            What is CSS?
        </summary>

        <p>
            CSS is used to style web pages.
        </p>

    </details>

</div>
```

---

# 38. Breadcrumb

```html
<nav
    class="breadcrumb"
    aria-label="Breadcrumb"
>

    <a href="/">
        Home
    </a>

    <span>
        /
    </span>

    <a href="/products">
        Products
    </a>

    <span>
        /
    </span>

    <span>
        Product Details
    </span>

</nav>
```

---

# 39. Image Gallery

```html
<section class="gallery">

    <figure>
        <img
            src="image1.jpg"
            alt="Gallery image 1"
        >
    </figure>

    <figure>
        <img
            src="image2.jpg"
            alt="Gallery image 2"
        >
    </figure>

    <figure>
        <img
            src="image3.jpg"
            alt="Gallery image 3"
        >
    </figure>

</section>
```

---

# 40. Video

```html
<video
    controls
    width="100%"
>

    <source
        src="video.mp4"
        type="video/mp4"
    >

    Your browser does not support video.

</video>
```

---

# 41. Audio Player

```html
<audio controls>

    <source
        src="audio.mp3"
        type="audio/mpeg"
    >

    Your browser does not support audio.

</audio>
```

---

# 42. FAQ

```html
<section class="faq">

    <h2>
        Frequently Asked Questions
    </h2>

    <div class="faq-item">

        <h3>
            How does it work?
        </h3>

        <p>
            You create an account and start using
            the platform.
        </p>

    </div>

    <div class="faq-item">

        <h3>
            Is it free?
        </h3>

        <p>
            A free plan is available.
        </p>

    </div>

</section>
```

---

# 43. Empty State

```html
<div class="empty-state">

    <div class="empty-icon">
        📦
    </div>

    <h2>
        No Data Found
    </h2>

    <p>
        There is nothing to show here yet.
    </p>

    <button class="btn">
        Add New
    </button>

</div>
```

---

# 44. 404 Page

```html
<main class="error-page">

    <h1>
        404
    </h1>

    <h2>
        Page Not Found
    </h2>

    <p>
        The page you're looking for doesn't exist.
    </p>

    <a href="/" class="btn">
        Go Home
    </a>

</main>
```

---

# 45. Footer

```html
<footer class="footer">

    <div class="footer-container">

        <div class="footer-brand">

            <h2>
                MyLogo
            </h2>

            <p>
                Building simple and powerful products.
            </p>

        </div>

        <div class="footer-links">

            <a href="/about">
                About
            </a>

            <a href="/privacy">
                Privacy
            </a>

            <a href="/terms">
                Terms
            </a>

            <a href="/contact">
                Contact
            </a>

        </div>

    </div>

    <div class="footer-bottom">

        <p>
            © 2026 MyWebsite. All rights reserved.
        </p>

    </div>

</footer>
```

---

# 46. Social Links

```html
<div class="social-links">

    <a
        href="#"
        aria-label="GitHub"
    >
        GitHub
    </a>

    <a
        href="#"
        aria-label="LinkedIn"
    >
        LinkedIn
    </a>

    <a
        href="#"
        aria-label="Instagram"
    >
        Instagram
    </a>

</div>
```

---

# 47. Contact Section

```html
<section class="contact">

    <div class="contact-info">

        <h2>
            Get In Touch
        </h2>

        <p>
            Have a question? Contact us.
        </p>

        <p>
            Email: hello@example.com
        </p>

        <p>
            Phone: +91 9876543210
        </p>

    </div>

    <form class="contact-form">

        <input
            type="text"
            name="name"
            placeholder="Your Name"
            required
        >

        <input
            type="email"
            name="email"
            placeholder="Your Email"
            required
        >

        <textarea
            name="message"
            placeholder="Your Message"
            rows="5"
            required
        ></textarea>

        <button
            type="submit"
            class="btn"
        >
            Send Message
        </button>

    </form>

</section>
```

---

# 48. Product Card

```html
<article class="product-card">

    <img
        src="product.jpg"
        alt="Product name"
    >

    <div class="product-content">

        <span class="badge">
            New
        </span>

        <h3>
            Product Name
        </h3>

        <p>
            Product description.
        </p>

        <strong>
            ₹999
        </strong>

        <button class="btn">
            Add to Cart
        </button>

    </div>

</article>
```

---

# 49. Blog Card

```html
<article class="blog-card">

    <img
        src="blog.jpg"
        alt="Blog thumbnail"
    >

    <div class="blog-content">

        <span class="badge">
            Technology
        </span>

        <h2>
            How to Build a Web Application
        </h2>

        <p>
            Learn the basics of building
            modern web applications.
        </p>

        <a href="/blog/article">
            Read Article →
        </a>

    </div>

</article>
```

---

# 50. Complete Landing Page Structure

```html
<!DOCTYPE html>
<html lang="en">

<head>

    <meta charset="UTF-8">

    <meta
        name="viewport"
        content="width=device-width, initial-scale=1.0"
    >

    <title>My Product</title>

    <link
        rel="stylesheet"
        href="style.css"
    >

</head>

<body>

    <!-- Navbar -->

    <header class="navbar">

        <a href="/" class="logo">
            MyLogo
        </a>

        <nav>

            <a href="#features">
                Features
            </a>

            <a href="#pricing">
                Pricing
            </a>

            <a href="#contact">
                Contact
            </a>

        </nav>

        <a href="/login" class="btn">
            Login
        </a>

    </header>


    <!-- Hero -->

    <main>

        <section class="hero">

            <div class="hero-content">

                <span class="badge">
                    New Platform
                </span>

                <h1>
                    Build Better Products
                </h1>

                <p>
                    A modern platform for building
                    powerful applications.
                </p>

                <a
                    href="#get-started"
                    class="btn"
                >
                    Get Started
                </a>

            </div>

        </section>


        <!-- Features -->

        <section id="features">

            <div class="section-header">

                <h2>
                    Features
                </h2>

                <p>
                    Everything you need.
                </p>

            </div>

            <div class="card-grid">

                <article class="card">

                    <h3>
                        Fast
                    </h3>

                    <p>
                        Fast and reliable performance.
                    </p>

                </article>

                <article class="card">

                    <h3>
                        Secure
                    </h3>

                    <p>
                        Built with security in mind.
                    </p>

                </article>

                <article class="card">

                    <h3>
                        Simple
                    </h3>

                    <p>
                        Easy to use and understand.
                    </p>

                </article>

            </div>

        </section>


        <!-- Pricing -->

        <section id="pricing">

            <h2>
                Pricing
            </h2>

            <div class="pricing-card">

                <h3>
                    Pro
                </h3>

                <strong>
                    ₹499/month
                </strong>

                <button class="btn">
                    Get Started
                </button>

            </div>

        </section>


        <!-- Contact -->

        <section id="contact">

            <h2>
                Contact Us
            </h2>

            <form>

                <input
                    type="text"
                    placeholder="Name"
                    required
                >

                <input
                    type="email"
                    placeholder="Email"
                    required
                >

                <textarea
                    placeholder="Message"
                    required
                ></textarea>

                <button
                    type="submit"
                    class="btn"
                >
                    Send
                </button>

            </form>

        </section>

    </main>


    <!-- Footer -->

    <footer class="footer">

        <p>
            © 2026 MyWebsite
        </p>

    </footer>


    <script src="script.js"></script>

</body>

</html>
```

---

# HTML SDK — Recommended Folder Structure

```text
html-sdk/
│
├── components/
│   ├── navbar.html
│   ├── hero.html
│   ├── card.html
│   ├── form.html
│   ├── modal.html
│   ├── sidebar.html
│   ├── table.html
│   ├── footer.html
│   └── pagination.html
│
├── css/
│   └── style.css
│
├── js/
│   └── script.js
│
└── index.html
```

---

# HTML + CSS + JS Architecture

```text
                    PROJECT
                       │
          ┌────────────┼────────────┐
          │            │            │
         HTML          CSS          JS
          │            │            │
      Structure      Design      Behaviour
          │            │            │
          └────────────┼────────────┘
                       │
                  Web Interface
```

### HTML

```text
HTML = Structure
```

### CSS

```text
CSS = Design / Styling
```

### JavaScript

```text
JS = Logic / Behaviour
```

### Example

```html
<button id="btn">
    Click Me
</button>
```

```css
.btn {
    padding: 10px 20px;
}
```

```javascript
document
    .getElementById("btn")
    .addEventListener("click", () => {

        alert("Button clicked!");

    });
```

---

# Quick Component Checklist

```text
HTML SDK

□ Basic HTML Structure
□ Semantic Layout
□ Container
□ Navbar
□ Mobile Navbar
□ Hero
□ Section Header
□ Button
□ Button Group
□ Card
□ Card Grid
□ Image Card
□ Profile Card
□ Avatar
□ Badge
□ Login Form
□ Signup Form
□ Search
□ Select
□ Checkbox
□ Radio
□ Textarea
□ File Upload
□ Alert
□ Modal
□ Sidebar
□ Dashboard
□ Stats Card
□ Pricing Card
□ Table
□ Pagination
□ Toast
□ Spinner
□ Skeleton
□ Progress Bar
□ Accordion
□ Breadcrumb
□ Gallery
□ Video
□ Audio
□ FAQ
□ Empty State
□ 404 Page
□ Footer
□ Social Links
□ Contact
□ Product Card
□ Blog Card
□ Landing Page
```
