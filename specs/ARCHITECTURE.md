# umwai.github.io - Architecture

**Version**: 1.0
**Last Updated**: December 2025

---

## Architecture Overview

This is a minimalist static site architecture optimized for performance, simplicity, and maintainability. The site has zero external dependencies and deploys automatically via GitHub Pages.

```
+------------------------------------------------------------------+
|                    Site Architecture                              |
+------------------------------------------------------------------+
|                                                                   |
|  +------------------+        +------------------+                 |
|  |   GitHub Repo    |------->|   GitHub Pages   |                 |
|  |   (Source)       |        |   (Hosting)      |                 |
|  +------------------+        +------------------+                 |
|                                       |                           |
|                              +--------v---------+                 |
|                              |   CloudFlare     |                 |
|                              |   (CDN/DNS)      |                 |
|                              +--------+---------+                 |
|                                       |                           |
|                              +--------v---------+                 |
|                              |   Browser        |                 |
|                              |   (Client)       |                 |
|                              +------------------+                 |
|                                                                   |
+------------------------------------------------------------------+
```

---

## File Structure

```
umwai.github.io/
├── index.html          # Complete site (HTML + inline CSS + JS)
├── favicon.svg         # Animated SVG favicon
├── CLAUDE.md          # AI assistant instructions
├── README.md          # Project documentation
└── specs/
    ├── ROADMAP.md     # Product roadmap
    └── ARCHITECTURE.md # This file
```

### Future Structure (with Blog)

```
umwai.github.io/
├── index.html
├── favicon.svg
├── og-image.png        # Open Graph image
├── sitemap.xml         # SEO sitemap
├── robots.txt          # Search engine directives
├── blog/
│   ├── index.html      # Blog listing page
│   ├── context-engineering.html
│   ├── multi-agent-patterns.html
│   └── ...
├── assets/
│   ├── images/
│   └── css/            # If CSS is externalized
├── CLAUDE.md
├── README.md
└── specs/
```

---

## Technology Stack

### Frontend

| Technology | Purpose | Rationale |
|------------|---------|-----------|
| HTML5 | Structure | Universal, no build step |
| CSS3 (inline) | Styling | Single file, instant load |
| Vanilla JS | Interactivity | Minimal, no dependencies |
| SVG | Graphics | Scalable, animatable |

### Hosting

| Service | Purpose | Cost |
|---------|---------|------|
| GitHub Pages | Static hosting | Free |
| GitHub Actions | CI/CD (future) | Free |
| CloudFlare (optional) | CDN/DNS | Free tier |

### No Dependencies By Design

The site intentionally has:
- No package.json
- No node_modules
- No build step
- No CSS framework
- No JavaScript framework
- No external fonts (system fonts)

**Benefits**:
- Zero maintenance overhead
- Maximum performance
- No security vulnerabilities from dependencies
- Works forever without updates

---

## Component Architecture

### HTML Structure

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <!-- Meta tags -->
    <!-- Inline CSS -->
</head>
<body>
    <div id="particles"></div>      <!-- Background animation -->

    <div class="container">
        <header class="section">     <!-- Name, role, tagline -->
        <section class="section">    <!-- Philosophy -->
        <section class="section">    <!-- Background -->
        <section class="section">    <!-- Experience timeline -->
        <section class="section">    <!-- Focus areas -->
        <section class="section">    <!-- Tech stack -->
        <section class="section">    <!-- Projects -->
        <section class="section">    <!-- Connect links -->
        <div class="footer">         <!-- Footer -->
    </div>

    <script>
        <!-- Particle animation -->
    </script>
</body>
</html>
```

### CSS Architecture

All CSS is inline in `<style>` tags for optimal performance:

```css
/* Reset */
* { margin: 0; padding: 0; box-sizing: border-box; }

/* Base */
body { font-family: monospace; background: #0a0a0a; }

/* Layout */
.container { max-width: 760px; margin: 0 auto; }

/* Components */
.section { /* Fade-in animation */ }
.timeline { /* Vertical timeline */ }
.focus-grid { /* 2-column grid */ }
.stack-grid { /* Flex wrap */ }
.projects { /* Project cards */ }

/* Animations */
@keyframes float { /* Particle animation */ }
@keyframes fadeIn { /* Section fade-in */ }
@keyframes blink { /* Cursor blink */ }
```

### JavaScript

Minimal vanilla JS for particle animation:

```javascript
// Generate floating particles
const particleContainer = document.getElementById('particles');
const particleCount = 30;

for (let i = 0; i < particleCount; i++) {
    const particle = document.createElement('div');
    particle.className = 'particle';
    particle.style.left = Math.random() * 100 + '%';
    particle.style.top = Math.random() * 100 + '%';
    particle.style.animationDelay = Math.random() * 20 + 's';
    particle.style.animationDuration = (15 + Math.random() * 15) + 's';
    particleContainer.appendChild(particle);
}
```

---

## Design System

### Colors

| Token | Value | Usage |
|-------|-------|-------|
| `--bg-primary` | #0a0a0a | Page background |
| `--bg-secondary` | #111 | Card backgrounds |
| `--bg-tertiary` | #1a1a1a | Borders |
| `--text-primary` | #fff | Headings |
| `--text-secondary` | #e0e0e0 | Body text |
| `--text-tertiary` | #888 | Muted text |
| `--text-muted` | #555 | Labels |
| `--accent` | #4a9eff | Links, highlights |

### Typography

```css
font-family: 'SF Mono', 'Fira Code', 'Consolas', monospace;

/* Scale */
h1: 1.75rem
body: 1rem (base)
small: 0.85rem
labels: 0.7rem
```

### Spacing

```css
/* Section spacing */
.section { margin-bottom: 64px; }

/* Container padding */
.container { padding: 80px 24px; }

/* Grid gaps */
.focus-grid { gap: 16px; }
.stack-grid { gap: 10px; }
```

### Responsive Breakpoints

```css
@media (max-width: 600px) {
    .focus-grid { grid-template-columns: 1fr; }
}
```

---

## Performance Architecture

### Critical Rendering Path

```
1. HTML downloaded (~18KB)
2. CSS parsed (inline, no blocking)
3. DOM constructed
4. First paint (< 100ms)
5. JS executed (particle animation)
6. Interactive (< 200ms)
```

### Performance Optimizations

| Optimization | Implementation | Impact |
|--------------|----------------|--------|
| Inline CSS | No external stylesheet | -1 request |
| System fonts | No font download | -100KB |
| Inline JS | No external scripts | -1 request |
| SVG favicon | No PNG/ICO | -5KB |
| No images | Text-only content | -200KB+ |
| No tracking | No analytics scripts | -50KB |

### Lighthouse Targets

| Metric | Target | Current |
|--------|--------|---------|
| Performance | 100 | ~98 |
| Accessibility | 100 | ~95 |
| Best Practices | 100 | ~100 |
| SEO | 100 | ~90 |

---

## Deployment Architecture

### GitHub Pages Workflow

```
+------------------+        +------------------+
|   Local Dev      |        |   GitHub         |
|   (index.html)   |------->|   Repository     |
+------------------+  push  +--------+---------+
                                     |
                            +--------v---------+
                            |   GitHub Pages   |
                            |   Build          |
                            +--------+---------+
                                     |
                            +--------v---------+
                            |   umwai.github.io|
                            |   (Live Site)    |
                            +------------------+
```

### Deployment Process

1. Edit `index.html` locally
2. `git add . && git commit -m "Update site"`
3. `git push origin main`
4. GitHub Pages automatically deploys (~30 seconds)
5. Site live at umwai.github.io

### No CI/CD Required

The simplicity of static HTML means:
- No build step needed
- No test suite required
- No staging environment necessary
- Instant rollback via `git revert`

---

## SEO Architecture

### Current Meta Tags

```html
<meta name="description" content="Senior Data Engineer...">
<meta property="og:type" content="website">
<meta property="og:url" content="https://umwai.github.io/">
<meta property="og:title" content="Wai Yang | Data Engineer">
<meta property="og:description" content="...">
<meta property="og:image" content="https://umwai.github.io/og-image.png">
<meta name="twitter:card" content="summary_large_image">
```

### Future SEO Enhancements

```html
<!-- Structured Data -->
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "Person",
  "name": "Wai Yang",
  "jobTitle": "Senior Data Engineer",
  "url": "https://umwai.github.io"
}
</script>

<!-- Canonical URL -->
<link rel="canonical" href="https://umwai.github.io/">

<!-- Sitemap -->
<link rel="sitemap" type="application/xml" href="/sitemap.xml">
```

---

## Accessibility Architecture

### Current Implementation

| Feature | Status | Notes |
|---------|--------|-------|
| Semantic HTML | Yes | header, section, nav |
| Color contrast | Yes | 4.5:1+ ratio |
| Keyboard navigation | Partial | Links focusable |
| ARIA labels | Partial | Needs improvement |
| Alt text | N/A | No images |
| Reduced motion | No | Add `prefers-reduced-motion` |

### Future Improvements

```css
/* Respect user motion preferences */
@media (prefers-reduced-motion: reduce) {
    .particle { animation: none; }
    .section { animation: none; opacity: 1; transform: none; }
}
```

```html
<!-- Skip link for keyboard users -->
<a href="#main" class="skip-link">Skip to content</a>

<!-- ARIA labels -->
<nav aria-label="Main navigation">
<section aria-labelledby="experience-heading">
```

---

## Security Architecture

### Current Security

| Measure | Implementation |
|---------|----------------|
| HTTPS | GitHub Pages default |
| No user input | No forms, no XSS risk |
| No backend | No server vulnerabilities |
| No cookies | No tracking, GDPR compliant |
| No dependencies | No supply chain attacks |

### Future Considerations (if adding forms)

```html
<!-- CSP Header (via _headers file) -->
Content-Security-Policy: default-src 'self'; script-src 'self' 'unsafe-inline'

<!-- Form spam protection -->
<input type="hidden" name="_gotcha" style="display:none">
```

---

## Analytics Architecture (Future)

### Recommended: Plausible Analytics

```html
<!-- Privacy-respecting analytics -->
<script defer data-domain="umwai.github.io"
        src="https://plausible.io/js/script.js"></script>
```

### Metrics to Track

| Metric | Purpose |
|--------|---------|
| Page views | Traffic volume |
| Unique visitors | Audience size |
| Referrers | Traffic sources |
| Top pages | Popular content |
| Countries | Geographic reach |
| Device types | Mobile vs desktop |

### Event Tracking (Future)

```javascript
// Track project clicks
document.querySelectorAll('.project').forEach(el => {
    el.addEventListener('click', () => {
        plausible('Project Click', {
            props: { project: el.dataset.project }
        });
    });
});
```

---

## Extension Points

### Adding a Blog

**Option 1: Static HTML Files**
```
blog/
├── index.html           # Blog listing
├── post-1.html          # Individual post
└── post-2.html
```

**Option 2: Build Tool (Astro)**
```
src/
├── pages/
│   ├── index.astro
│   └── blog/
│       └── [...slug].astro
├── content/
│   └── blog/
│       ├── post-1.md
│       └── post-2.md
└── layouts/
    └── BlogPost.astro
```

### Adding Dark/Light Mode

```javascript
// Toggle theme
function toggleTheme() {
    document.body.classList.toggle('light-mode');
    localStorage.setItem('theme',
        document.body.classList.contains('light-mode') ? 'light' : 'dark'
    );
}

// Respect system preference
if (window.matchMedia('(prefers-color-scheme: light)').matches) {
    document.body.classList.add('light-mode');
}
```

### Adding Contact Form

```html
<!-- Formspree integration -->
<form action="https://formspree.io/f/xxxxx" method="POST">
    <input type="email" name="email" required>
    <textarea name="message" required></textarea>
    <button type="submit">Send</button>
</form>
```

---

## Maintenance

### Regular Tasks

| Task | Frequency | Automation |
|------|-----------|------------|
| Update content | As needed | Manual |
| Check links | Monthly | Manual or tool |
| Review analytics | Weekly | Dashboard |
| Security audit | N/A | No dependencies |
| SSL renewal | Never | GitHub Pages auto |

### Backup Strategy

- GitHub repository is the source of truth
- No database to backup
- Version history via git

---

## Decision Log

| Date | Decision | Rationale |
|------|----------|-----------|
| Dec 2025 | No build system | Simplicity, performance |
| Dec 2025 | Inline CSS/JS | Single file, no requests |
| Dec 2025 | System fonts | No download latency |
| Dec 2025 | GitHub Pages | Free, simple, reliable |
| Dec 2025 | Dark theme | Developer aesthetic |

---

*This architecture document reflects the current state and planned evolution of the site.*
