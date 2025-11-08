# LESSON TWELVE - HTML & CSS tables, flex and media query #

## 1. Structure and Style Separation ##

When using many CSS classes excessively, HTML tends to mix structure and style, which makes the code harder to maintain. The cleaner approach is to use fewer, more meaningful classes. This keeps the HTML document readable and allows style designers and content developers to work independently.

### Example: Styling table rows dynamically ###

CSS pseudo-classes such as `:nth-child()` can apply alternating row colours automatically — even for future-added elements.

```css
tbody tr:nth-child(odd) {
  background-color: antiquewhite;
}
tbody tr:nth-child(even) {
  background-color: chocolate;
}
```

You can also replace `even` with numeric formulas like `2n`, `3n`, or `4n+1` for more complex patterns.

### Example: Styling Columns ###

You can target specific table columns:

```css
tbody tr td:first-child {
  background-color: aqua;
}
```

### Adding Padding to Table Cells ###

Padding improves spacing and readability inside cells:

```css
th, td {
  border: 1px solid #000;
  padding: 0.5rem;
}
```

### Customising Captions ###

Captions describe the table content and can be styled like any block element:

```html
<caption>Register of students enrolled at Labforweb school</caption>
```

```css
caption {
  font-weight: bold;
  text-align: left;
  margin-bottom: 0.5rem;
}
```

---

## 2. Fonts and Typography ##

On screens, **sans-serif** fonts are generally more readable, while **serif** fonts are preferable for print. By default, browsers use serif fonts. You can set the preferred typefaces as follows:

```css
font-family: Verdana, Geneva, Tahoma, sans-serif;
```

### Notes: ###
- **Verdana** was designed by *Matthew Carter* (1995) for Microsoft and optimised for screen readability.  
- **Fallback fonts** (e.g. *Geneva*, *Tahoma*) ensure cross-platform consistency.  
- Always verify font licensing before distributing them commercially.  

Some companies (e.g. *Mercedes*, *TIM*, *Corriere della Sera*) use custom corporate fonts for brand recognition.

---

## 3. Flexbox Layout ##

Flexbox simplifies responsive layouts without relying heavily on media queries. It provides flexibility in distributing space among items within a container.

### Example: Creating a flexible container

```css
.container {
  display: flex;
  justify-content: space-around;
  align-items: flex-start;
  flex-wrap: wrap;
  background-color: antiquewhite;
  padding: 30px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}
```

### Fixed vs Flexible Children ###

- **`width: 300px`** keeps elements static.
- **`flex: 300px`** makes them grow or shrink according to available space.

### Understanding `flex` shorthand ###

`flex: 1` means:

```css
flex-grow: 1;
flex-shrink: 1;
flex-basis: 0;
```

It lets items expand and contract evenly within a container. However, behaviour may differ when children have variable content (e.g., images or long text).

---

## 4. Responsive Design and Media Queries ##

Media queries allow CSS to adapt layouts across devices and screen sizes.

### Basic Syntax ###

```css
@media screen and (max-width: 768px) {
  body {
    background-color: orange;
  }
}
```

### Common Breakpoints ###

| Device Type             | Width Range (px) |
| ----------------------- | ---------------- |
| Smartphone (old-gen)    | 320–480          |
| Smartphone & Tablet     | 481–768          |
| Small landscape devices | 769–1024         |
| Desktop & Laptop        | 1025–1200        |
| HD/4K screens           | 1201+            |

### Mobile First vs Desktop First ###

- **Desktop First:** use `max-width` to handle smaller screens.  
- **Mobile First:** use `min-width` to build up from smaller to larger displays.

### Orientation Example ###

```css
@media screen and (max-width: 1024px) and (orientation: landscape) {
  body {
    background-color: lightblue;
  }
}
```

### Viewport Meta Tag ###

Ensures the correct scaling on mobile browsers:

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

---

## 5. Elastic and Hybrid Layouts ##

### Elastic Layouts ###

An elastic layout adapts both structure and media content. To make images scale within their container:

```css
img {
  max-width: 100%;
  height: auto;
}
```
**Note** Unlike a **fluid layout**, which scales container widths but may leave media elements fixed, an **elastic layout** ensures that both containers and all internal media, like images and videos, scale proportionally to the viewport. 

### Hybrid Layouts ###

Combines fixed and flexible elements. Ideal when some sections (e.g. ads) must remain static.

```css
#ad {
  width: 200px;
  height: 420px;
  margin-right: 10px;
}

section {
  width: calc(100% - 210px);
  height: 420px;
}
```

---

## 6. Box and Text Shadows ##

### Box Shadow ###

Adds visual depth to elements.
- 1st value (5px): horizontal offset (how far the shadow moves to the right)
- 2nd value (5px): vertical offset (how far the shadow moves down)
- 3rd value (10px): blur radius (how soft or blurred the shadow appears)
- 4th value (rgba color): shadow colour and transparency

```css
box-shadow: 5px 5px 10px rgba(0,0,0,0.2);
```

### Text Shadow ###

Adds emphasis or stylistic effects to text.

```css
text-shadow: 2px 2px 4px rgba(0,0,0,0.3);
```
- 1st value (2px): horizontal offset (shadow shift to the right)
- 2nd value (2px): vertical offset (shadow shift down)
- 3rd value (4px): blur radius (softness of the shadow)
- 4th value (rgba color): shadow colour and transparency
---

## 7. Printing Styles ##

You can provide print-specific styles using the `media="print"` attribute or a media query.

```html
<link rel="stylesheet" href="style/template.css" media="all">
<link rel="stylesheet" href="style/print.css" media="print">
```

### Hiding Images for Print ###

```css
img {
  display: none;
}
.show {
  display: block;
}
```

### Adjusting Fonts for Print ###

Printed pages benefit from serif fonts for readability:

```css
body {
  font-family: 'Times New Roman', Times, serif;
  font-size: 1.2rem;
}
```

---

** Useful Links **

- https://en.wikipedia.org/wiki/Matthew_Carter
- https://en.wikipedia.org/wiki/Verdana
- https://en.wikipedia.org/wiki/Georgia_(typeface)
- https://en.wikipedia.org/wiki/Tahoma_(typeface)
- https://en.wikipedia.org/wiki/Claude_Garamond
- https://www.w3resource.com/html/attributes/html-valign-attribute.php
- https://sensible.com/about/
- https://www.lukew.com/about/
- https://html5please.com/
- https://camendesign.com/code/video_for_everybody
- https://sensible.com/dont-make-me-think/
- https://mobile-first.abookapart.com/
- https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/At-rules/@media#media_features
- https://www.nngroup.com/articles/top-10-mistakes-web-design/
- https://code.visualstudio.com/docs/configure/keybindings#_basic-editing
- https://css-tricks.com/the-checkbox-hack/
- https://css3generator.com/