# Portfolio Website Guidelines

This is a personal portfolio for **Ahmad Afif Aulia Hariz**, hosted as a static site on GitHub Pages at `https://afifhrz.github.io/`. It uses **native HTML, CSS, and vanilla JavaScript only** — no build tools, no frameworks, no preprocessors.

## Stack Constraints

- **No frameworks**: Pure HTML5, CSS3, and vanilla JS. Do not suggest or introduce React, Vue, Tailwind, SCSS, or any bundlers.
- **No server-side logic**: GitHub Pages serves static files only. All functionality must work client-side.
- **No `<base>` tag tricks**: Use root-relative paths (`/docs/styles.css`) or relative paths consistently.
- **Entry point**: `docs/index.html` is the primary page served at `https://afifhrz.github.io/`.

## SEO: Meta Tags

Every page must include all of the following in `<head>`, in this order:

1. `<meta charset="UTF-8">`
2. `<meta name="viewport" content="width=device-width, initial-scale=1.0">`
3. `<meta name="description">` — 120–160 characters, front-load primary keywords (name, role, specialization).
4. `<meta name="keywords">` — comma-separated, include: full name, job title, tech stack keywords, "remote software engineer".
5. `<meta name="author" content="Ahmad Afif Aulia Hariz">`
6. `<meta name="robots" content="index, follow">`
7. `<link rel="canonical" href="https://afifhrz.github.io/[page-path]">` — always include to prevent duplicate content.
8. `<title>` — format: `{Page Topic} | Ahmad Afif Aulia Hariz - Software Engineer`.

Title must be 50–60 characters. Never omit the full name in the title.

## SEO: Open Graph & Twitter Cards

All pages must include complete OG and Twitter Card meta tags for rich social sharing:

```html
<!-- Open Graph -->
<meta property="og:title" content="...">
<meta property="og:description" content="...">
<meta property="og:type" content="website">
<meta property="og:url" content="https://afifhrz.github.io/[page-path]">
<meta property="og:image" content="https://afifhrz.github.io/profile.jpg">
<meta property="og:site_name" content="Ahmad Afif Aulia Hariz Portfolio">

<!-- Twitter Card -->
<meta name="twitter:card" content="summary_large_image">
<meta name="twitter:title" content="...">
<meta name="twitter:description" content="...">
<meta name="twitter:image" content="https://afifhrz.github.io/profile.jpg">
```

OG description: 155–200 characters. OG image: must be an absolute URL with `https://afifhrz.github.io/` base.

## SEO: Structured Data (JSON-LD)

The main `index.html` must include a `<script type="application/ld+json">` block using `@type: "Person"` schema. When adding project pages, also include `@type: "SoftwareSourceCode"` or `"CreativeWork"` for each project. 

Schema must always include:
- `name`, `jobTitle`, `url`, `email`
- `worksFor` with `@type: "Organization"`
- `sameAs` array with GitHub and LinkedIn profile URLs
- `knowsAbout` array listing key technologies

## SEO: Semantic HTML Structure

- Use exactly **one `<h1>`** per page. On `index.html` the `<h1>` is the hero headline; it must be descriptive (e.g., "Software Engineer" is acceptable since name is in `<title>` and meta).
- Heading hierarchy must be strict: `h1 → h2 → h3 → h4`. Never skip levels.
- Use semantic sectioning: `<header>`, `<nav>`, `<main>`, `<section>`, `<article>`, `<footer>`. Do not use `<div>` where a semantic element fits.
- Every `<section>` must have either an `aria-label` attribute or contain a visible heading that labels it.
- Navigation `<nav>` must have `aria-label="Main navigation"`.

## SEO: Images & Media

- Every `<img>` must have a descriptive `alt` attribute. Never use empty `alt=""` for content images; only use it for purely decorative images.
- Prefer descriptive filenames: `ahmad-afif-backend-engineer.jpg` over `photo.jpg`.
- Use `loading="lazy"` on all images below the fold.
- Specify `width` and `height` attributes on images to prevent layout shift (CLS).

## SEO: Links & Anchors

- All external links must have `rel="noopener noreferrer"` and open in a new tab with `target="_blank"`.
- Internal anchor links (e.g., `href="#projects"`) are fine as-is.
- Use descriptive link text — never "click here" or "read more". Use the destination/action as text (e.g., "View High Throughput Order System project").

## Performance (Core Web Vitals)

Poor Core Web Vitals directly hurt SEO rankings. Follow these rules:
- **CSS**: Keep all styles in `styles.css`. Do not use inline `style=` attributes for anything other than dynamic JS-driven values.
- **JS**: Place `<script>` tags before `</body>` or use `defer`. Never block rendering with scripts in `<head>` unless they set critical CSS variables.
- **Fonts**: If using Google Fonts, use `rel="preconnect"` and `rel="preload"` to reduce render-blocking.
- **No unused CSS**: Do not add CSS classes or rules unless they are actively used in markup.

## Content Keywords

When adding or editing content text, naturally include these high-value keywords where contextually appropriate:
- Ahmad Afif Aulia Hariz, Afif Hariz
- Software Engineer, Backend Engineer, Senior Software Engineer
- .NET, ASP.NET Core, Python, Django, FastAPI, Go
- Microservices, Distributed Systems, Cloud Infrastructure, System Design
- AWS, Kubernetes, Docker
- Remote Software Engineer, Indonesia

Do **not** keyword-stuff — every keyword must appear in a natural sentence.

## Project Sub-pages

When adding new project pages (e.g., `/docs/projects/order-system/index.html`):
- Repeat all meta tags, OG tags, Twitter cards, and JSON-LD for that page.
- Use `@type: "SoftwareSourceCode"` in JSON-LD with `name`, `description`, `programmingLanguage`, `codeRepository`, and `author`.
- Include a `<link rel="canonical">` pointing to the project's canonical URL.
- Add a breadcrumb `<nav aria-label="Breadcrumb">` with structured `BreadcrumbList` JSON-LD.
