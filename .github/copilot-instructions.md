# AI Coding Agent Instructions for Lux Portfolio

## Project Overview

This is a static personal portfolio website built using the "Luther" template from StyleShout. It's a single-page application showcasing a full-stack developer's work, skills, and experience.

## Architecture & Structure

- **Single-page HTML**: [index.html](../index.html) is the main entry point (613 lines) with multiple sections (`#intro`, `#about`, `#works`, `#contact`)
- **CSS Organization**: Two-layer system - [vendor.css](../css/vendor.css)/[vendor.min.css](../css/vendor.min.css) for libraries, [styles.css](../css/styles.css)/[styles.min.css](../css/styles.min.css) for custom styles
- **JavaScript Architecture**: [js/main.js](../js/main.js) for site interactions, [js/plugins.js](../js/plugins.js) contains vendor libraries (Prism, BasicLightbox, MailtoUI, Swiper)
- **No Build System**: This is a **static HTML site with no build tools**, no package.json, no npm/webpack/gulp - edit files directly

## Key Development Patterns

### 1. CSS Minification

- Production site uses `.min.css` files ([index.html](../index.html) lines 17-18)
- Development uses non-minified versions for easier editing
- Both versions must be maintained manually when making changes

### 2. Animation System (Anime.js)

[main.js](../js/main.js) implements a timeline-based animation sequence:

```javascript
const tl = anime.timeline({
  easing: "easeInOutCubic",
  duration: 800,
  autoplay: false,
});
```

- Animations trigger on page load via preloader
- Scroll-triggered animations use `data-animate-block` and `data-animate-el` attributes
- Animation logic in `ssViewAnimate()` function

### 3. Smooth Scrolling Navigation

- Internal navigation uses `.smoothscroll` class
- Custom MoveTo.js implementation with `easeInOutCubic` easing
- Active section highlighting in navigation via `ssScrollSpy()` function

### 4. Project Portfolio Modals

Portfolio items use hidden modal divs (e.g., `#modal-01`, `#modal-02`, `#modal-03`):

- Click handler triggers BasicLightbox library
- Each modal contains project description, tech stack, and link
- Pattern: `<a class="folio-list__item-link" href="#modal-01">` triggers modal

### 5. Mobile-First Responsive Design

- Mobile menu toggle at 800px breakpoint: [main.js](../js/main.js) line 108
- Grid system defined in [styles.css](../css/styles.css) with breakpoints for tablet/mobile
- Navigation transforms from horizontal to hamburger menu

## Critical Files & Sections

### [index.html](../index.html)

- Lines 78-100: Intro section with hero text and social links
- Lines 111-299: About section with personal bio, expertise list, experience timeline
- Lines 304-500: Works section with project cards and modals
- Update personal info, project descriptions, and tech stacks here

### [js/main.js](../js/main.js)

- Lines 16-62: Page load animation sequence
- Lines 69-86: Preloader initialization
- Lines 92-130: Mobile menu toggle logic
- Lines 138-171: Scroll spy for active nav highlighting
- Lines 177-218: Viewport animation triggers
- Lines 304-342: Smooth scroll implementation

### [css/styles.css](../css/styles.css)

- Lines 1-50: Table of contents and structure overview
- Custom styling follows BEM-like naming with section prefixes (`.s-header`, `.s-intro`, `.s-about`)
- Modify theme colors, spacing, or typography here

## Attribution & Licensing

- Template: "Luther" by StyleShout (free for personal/commercial with attribution)
- **Attribution link required** in footer or site ([readme.txt](../readme.txt) lines 47-52)
- Credit removal available for $10 via [readme.txt](../readme.txt) lines 61-70

## Deployment Notes

- Static files can be hosted on any web server (GitHub Pages, Netlify, Vercel, etc.)
- Ensure [site.webmanifest](../site.webmanifest), favicons, and [cv.pdf](../cv.pdf) are included
- No server-side processing required - pure HTML/CSS/JS

## Common Tasks

### Adding a New Project

1. Add project card in [index.html](../index.html) `<ul class="folio-list">` section (around line 315)
2. Create corresponding modal div with project details (lines 410-515)
3. Add project image to [images/portfolio/gallery/](../images/portfolio/gallery/)
4. Update lightbox click handlers automatically via BasicLightbox

### Updating Personal Info

- Bio text: [index.html](../index.html) lines 125-135
- Skills/expertise: [index.html](../index.html) lines 155-175
- Experience timeline: [index.html](../index.html) lines 180-270
- Social links: [index.html](../index.html) lines 95-101

### Modifying Animations

- Page load sequence: [main.js](../js/main.js) lines 16-62
- Scroll animations: [main.js](../js/main.js) lines 177-218
- Add `data-animate-block` to parent and `data-animate-el` to child elements

## External Dependencies (Embedded in [js/plugins.js](../js/plugins.js))

- **Anime.js**: Animation library (referenced but not in plugins.js - loaded separately)
- **MoveTo.js**: Smooth scroll library
- **BasicLightbox**: Modal/lightbox functionality
- **MailtoUI**: Enhanced mailto link interface
- **Swiper**: Touch slider (currently unused in this version)
- **Prism.js**: Syntax highlighting (currently unused)

These libraries are concatenated and minified - edit individual library behavior in [main.js](../js/main.js), not [plugins.js](../js/plugins.js).
