# Webora — Website Design Agency Website

A complete, static, GitHub Pages–ready website for **Webora**, built with plain HTML5, CSS3 and vanilla JavaScript — no build tools, no frameworks, no backend required.

---

## 📁 Folder Structure

```
webora/
├── index.html                 Homepage
├── about.html
├── services.html              Services overview
├── portfolio.html             Portfolio overview (filterable)
├── pricing.html
├── calculator.html            Website cost calculator
├── blog.html                  Blog listing (search + filters)
├── contact.html
│
├── privacy-policy.html
├── terms-and-conditions.html
├── refund-policy.html
├── 404.html
│
├── css/
│   └── style.css              All site styling (one file, CSS variables at the top)
│
├── js/
│   ├── main.js                 Nav, scroll effects, FAQ, testimonials, quote modal, WhatsApp
│   ├── calculator.js           Cost calculator logic
│   └── blog.js                 Blog search + category filtering
│
├── services/                   8 individual service pages
├── projects/                   6 project case study pages
├── blog/                       6 individual blog posts
│
├── sitemap.xml
├── robots.txt
└── README.md
```

---

## 🚀 How to Deploy on GitHub Pages

1. Create a [GitHub](https://github.com) account if you don't already have one.
2. Create a **new repository** (e.g. `webora-website`).
3. Upload **all the files and folders** in this project to the repository, keeping the folder structure exactly as it is (drag-and-drop upload on github.com works fine for this).
4. Open your repository and go to **Settings**.
5. In the left sidebar, click **Pages**.
6. Under **Build and deployment → Source**, select **Deploy from a branch**.
7. Under **Branch**, select **main** (or `master`, whichever your repo uses).
8. Select the **/ (root)** folder.
9. Click **Save**.
10. GitHub will publish the site at `https://yourusername.github.io/webora-website/` — open the URL shown at the top of the Pages settings once it finishes building (usually 1–2 minutes).

That's it — no build step, no npm install, nothing else required.

---

## ✏️ How to Change Key Business Information

### WhatsApp Number
Open **`js/main.js`** and edit the top of the file:
```js
const WEBORA_CONFIG = {
  whatsappNumber: "919876543210", // ← change this (country code + number, no + or spaces)
  email: "hello@webora.in",
  domain: "https://yourdomain.com"
};
```
This number is also hardcoded in a few `wa.me` links inside `services/*.html`, `projects/*.html`, `blog/*.html` and `contact.html` (search for `919876543210` and replace all occurrences with your number).

### Email
Update the `email` value in `js/main.js`, and replace `hello@webora.in` wherever it appears across the HTML files (footers, contact page, legal pages).

### Domain
Once you have a real domain, replace `https://yourdomain.com` in:
- Every `<link rel="canonical">` tag
- `sitemap.xml`
- `robots.txt`

### Pricing
Edit the `pricing` array inside:
- `index.html` (bottom `<script>` block)
- `pricing.html` (bottom `<script>` block)

Edit the calculator's numbers separately in `js/calculator.js` (`BASE_PRICE`, `PAGE_ADDON`, `FEATURE_ADDON`).

### Portfolio Projects
Edit the `folio` array in `index.html` and `portfolio.html`, and edit/replace the individual files in `projects/`. Update `sitemap.xml` if you add or remove projects.

### Blog Posts
Add new posts to the `POSTS` array in `js/blog.js`, and create a matching HTML file in `blog/` (copy an existing post as a starting template — it already includes the breadcrumb, table of contents, related posts and CTA structure). Add the new URL to `sitemap.xml`.

### Images
This build uses CSS gradients and inline SVG icons instead of photos, so there are no broken image links out of the box. To add real photos:
1. Create the `images/` subfolders shown in the structure above (`logo/`, `hero/`, `portfolio/`, `blog/`, `icons/`).
2. Replace the relevant `<div>` mockup/thumbnail elements with `<img>` tags, e.g. `<img src="images/portfolio/project-1.jpg" alt="Description of the project">`.
3. Always add meaningful `alt` text for accessibility and SEO.

### Social Media Links
Update the `href="#"` placeholders in every footer's **Connect** section (Instagram, Facebook, LinkedIn) with your real profile URLs.

---

## 🧩 Notable Features

- Sticky navbar with scroll blur effect
- Mobile hamburger menu with overlay
- Scroll-reveal animations (respects `prefers-reduced-motion`)
- Animated counters on the trust bar
- Filterable portfolio (by category)
- Accessible FAQ accordion (used across multiple pages)
- Testimonial slider with dots + arrows
- 4-step "Get a Free Quote" modal that generates a pre-filled WhatsApp message
- Website Cost Calculator with a live estimate and WhatsApp hand-off
- Blog with live search + category filtering
- Floating WhatsApp button on every page
- Custom 404 page

---

## 🛠️ Notes on the Contact Form

`contact.html` does **not** submit anywhere by default — GitHub Pages has no backend. On submit, it currently:
1. Builds a pre-filled WhatsApp message from the entered fields, and
2. Shows an on-page success message.

To receive real email submissions, connect the `<form id="enquiryForm">` to a service like [Formspree](https://formspree.io) or a Google Apps Script Web App by adding their `action` and `method` attributes — the existing `name` attributes on each field can stay as they are.

---

Built with HTML5, CSS3 and vanilla JavaScript. No dependencies, no build step.
