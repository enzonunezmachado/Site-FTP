# Copilot Instructions for TechLearn Website

## Project Overview
This is a static HTML/CSS website for TechLearn, an online education platform teaching web development (HTML, CSS, JavaScript). The site features responsive navigation and multiple pages showcasing services and courses.

**Key Info**: Portuguese language (pt-br), minimal JavaScript, desktop-first design with mobile responsiveness.

## Architecture & Page Structure

### Multi-Page Layout
- **index.html** - Homepage with course overview and hero button
- **servicos.html** - Services listing (web development, maintenance, consulting, training)
- **quem_somos.html** - About page (currently minimal)
- **contato.html** - Contact page (under development, minimal content)

All pages share a consistent header/footer structure using `<header>`, `<main>`, `<footer>` semantic HTML.

### Navigation Pattern
All pages use an identical navigation with a **checkbox hamburger menu**:
```html
<input type="checkbox" id="check">
<label for="check" class="open-menu">☰</label>
<label for="check" class="close-menu">✕</label>
<nav class="menu">
  <ul>
    <li><a href="index.html">Início</a></li>
    <li><a href="servicos.html">Serviços</a></li>
    <li><a href="quem_somos.html">Quem Somos</a></li>
    <li><a href="contato.html">Contatos</a></li>
  </ul>
</nav>
```

When adding new pages, replicate this exact structure and update the menu links.

## Styling Conventions

### File Organization
- **../css/style.css** - Global styles for all pages (header, footer, main, nav, responsive behavior)
- **../css/contato.css** - Contact form styles (currently empty)
- **../css/quem.css** - About page styles
- **../css/serviços.css** - Services page styles

**Rule**: Each page has its own CSS file for page-specific styling; shared styles go in `style.css`.

### Color & Typography Scheme
- **Header/Footer**: Black background (`#000000`), white text, red accents (`#ff0000`)
- **Text Effects**: Webkit text stroke with orange outline (`-webkit-text-stroke-width: 2px; -webkit-text-stroke-color: #ffae00`)
- **Buttons**: Blue (`#0054b4`) with dark blue border (`#003d80`), white text, large padding (90px 180px)
- **Main Content**: Red text (`#ff0000`) with black stroke on light background
- **Font**: Perpetua primary, fallback to Arial/sans-serif

### Responsive Breakpoint
Mobile menu toggle triggers at **max-width: 610px** in **../css/style.css**:
- Desktop: Horizontal nav menu visible
- Mobile: Hamburger icon toggles fixed right-side menu (40% width, 100vh height)

When modifying responsive behavior, update media query and test at 610px boundary.

## Common Patterns & Gotchas

### Known Issues to Avoid
1. **Duplicate headers** - Some pages have duplicate `</header>` tags (e.g., quem_somos.html line 26) - should remove
2. **Unclosed tags** - index.html line 40 has unclosed `<p>` tags - use `</p>` consistently
3. **Broken links** - servicos.html and quem_somos.html link to `sobre.html` but page is named `quem_somos.html`
4. **Placeholder title** - All pages have `<title>Carrinho de Compras</title>` (shopping cart) - should be page-specific
5. **Inconsistent nav links** - Some pages have inconsistent href targets; align with actual filenames

### Content Conventions
- Hero sections use section tags with multiple `<h3>` + `<p>` pairs
- Main content is always wrapped in `<main>` with max-width: 800px
- Buttons use large padding (90px 180px) for visibility
- Images stored in [img/](img/) directory; reference as `img/filename`
- Background image set via HTML `background` attribute, not CSS

## Development Workflow

### No Build System
This is a static HTML/CSS site. No npm, webpack, or build tools - files serve as-is.

### Testing
- Open HTML files directly in browser or use a local server
- Test responsive behavior at 610px width breakpoint
- Verify all navigation links work (check filenames match href values)
- Test hamburger menu on mobile width

### New Feature Guidelines
- **New pages**: Create `.html` file, replicate header/nav/footer structure from index.html, create matching CSS file
- **Styling changes**: Modify ../css/style.css for global changes, page-specific CSS files for individual pages
- **Content updates**: Edit HTML directly; no database or CMS
- **Assets**: Place images in ../img/ folder and reference with relative paths

