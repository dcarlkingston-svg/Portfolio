# Web Dev Class Demos

Teaching sandbox for our web development class. Each HTML file demonstrates **one technique**. Open a page, find the matching section in `styles.css`, and read the markup.

This README is the source of truth. Follow it when adding or changing pages so the project stays consistent for demos.

## File layout

Keep paths beginner-friendly. HTML lives at the project root.

```
WebDev/
  index.html          Hub — table of contents linking every demo
  demo-topic.html     One file per technique (name it after the topic)
  styles.css          The only stylesheet
  assets/             Images, video, fonts
  README.md           This guide
```

Rules:

- Every HTML page links the same stylesheet: `<link rel="stylesheet" href="styles.css">`
- Media files go in `assets/` (for example `assets/logo.png`, `assets/clip.mp4`)
- Do not add extra `.css` files

## HTML conventions

Use industry-standard, semantic markup. Prefer a real element over a generic wrapper.

### Document shell (every page)

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Topic — Web Dev Class Demos</title>
    <link rel="stylesheet" href="styles.css" />
  </head>
  <body>
    <header>
      <p><a href="index.html">Class demos</a></p>
      <h1>Topic name</h1>
    </header>
    <main>
      <!-- page content -->
    </main>
    <footer>
      <p>Web development class demonstration</p>
    </footer>
  </body>
</html>
```

### Prefer these over `<div>`

| Instead of wrapping with `<div>` | Use |
| --- | --- |
| Site or page banner | `<header>` |
| Primary navigation | `<nav>` (usually with a `<ul>` of links) |
| Primary content | `<main>` (one per page) |
| A self-contained piece | `<article>` |
| A thematic group with a heading | `<section>` |
| Related side content | `<aside>` |
| Page or section end matter | `<footer>` |
| Image or media with a caption | `<figure>` and `<figcaption>` |
| Lists of links or items | `<ul>`, `<ol>`, `<li>` |

Use `<div>` only when **no semantic element fits** — generic grouping for layout that is not a section of content. Use `<span>` only for inline bits that have no meaning of their own.

### Media, forms, and accessibility

- `<img>` is a void element: no `</img>`. Always include meaningful `alt` (empty `alt=""` only for decorative images).
- Wrap media you caption in `<figure>`. Include fallback text inside `<video>` / `<audio>`.
- Associate every form control with a `<label>`. Use native controls. Use `<button>` for actions, not a styled `<span>` or `<div>`.
- One `<h1>` per page. Do not skip heading levels (`h1` then `h2`, not `h1` then `h3`).
- Link text should make sense on its own (avoid “click here”). Do not rely on color alone to convey meaning.

## CSS: `styles.css` only

All CSS lives in **one** file. Keep it readable: comment sections, shallow selectors, notes for anything non-obvious.

### File order

```css
/* ===== 1. Reset / base ===== */
:root {
  /* colors, spacing, type scale */
}

/* ===== 2. Shared layout ===== */
/* header, nav, main, footer used on every page */

/* ===== 3. Shared components ===== */
/* buttons, figures, etc. — only if more than one page uses them */

/* --- demo-flexbox.html --- */
/* styles that exist only for that demo */

/* --- demo-grid.html --- */
```

Page-specific blocks go **last**, named after the HTML file.

### Rules

- No inline `style=""` attributes
- No extra stylesheets
- No `<style>` in HTML unless that **is** the lesson, and the page title says so
- Prefer element and landmark selectors (`header`, `nav a`, `figure`)
- Add a class only when the same element needs two different looks
- Keep selectors shallow (avoid long chains)
- Comment *why* for non-obvious rules, not *what* the property name already says

## How to add a demo

1. Copy the document shell into `demo-topic.html` (use a short, lowercase, hyphenated name).
2. Append a matching comment block at the **bottom** of `styles.css`, for example `/* --- demo-topic.html --- */`.
3. Add a link on `index.html`.
4. Teach one technique in the HTML with semantic markup. Put that page’s styles only in its CSS section.

## Demo roadmap

`index.html` is the hub. Check items off as pages exist.

| Page | Technique | Status |
| --- | --- | --- |
| `index.html` | Hub / table of contents | Planned |
| `demo-document.html` | Document shell (`DOCTYPE`, `head`, landmarks) | Planned |
| `demo-landmarks.html` | Semantic landmarks (`header`, `nav`, `main`, `aside`, `footer`) | Planned |
| `demo-media.html` | Images, `figure` / `figcaption`, video | Planned |
| `demo-lists-nav.html` | Lists and navigation | Planned |
| `demo-typography.html` | Headings, paragraphs, type in CSS | Planned |
| `demo-box-model.html` | Margin, border, padding, box sizing | Planned |
| `demo-flexbox.html` | Flexbox layout | Planned |
| `demo-grid.html` | CSS Grid | Planned |
| `demo-forms.html` | Labels, inputs, buttons | Planned |

Move a row to **Done** when the HTML file exists, is linked from the hub, and has a section in `styles.css`.

## Out of scope

Unless the class explicitly adds a lesson for it:

- JavaScript
- Frameworks or build tools
- Multiple CSS files or styles copied into each HTML file
- Layouts built only from `<div>`s
