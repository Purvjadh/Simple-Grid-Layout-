# Blog Listing Page

A responsive blog post listing page built with HTML and CSS. Cards display article info including title, description, author, and labels.

🔗 **Live Site:** [View Project](https://effulgent-concha-f02d25.netlify.app/)

---

## Table of Contents

- [Overview](#overview)
- [Screenshot](#screenshot)
- [Built With](#built-with)
- [What I Learned](#what-i-learned)
- [Author](#author)

---

## Overview

A clean, responsive blog card listing page where each card shows:
- Article thumbnail image
- Title and description
- Author info with avatar
- Category labels

The layout automatically adjusts from a single column on mobile to multiple columns on larger screens — no media queries needed for the grid!

---

## Screenshot

![Blog Listing Page](screenshot.png)

---

## Built With

- Semantic HTML5
- CSS Custom Properties
- **CSS Grid** with `auto-fit` and `minmax`
- Flexbox
- Mobile-first workflow
- Google Fonts — Poppins

---

## What I Learned

### 🟣 CSS Grid — `auto-fit` + `minmax` (No Media Queries!)

The biggest thing I learned was how to make a **fully responsive grid without writing a single `@media` query**:

```css
.main {
  --min-col-size: 280px;
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(min(var(--min-col-size), 100%), 1fr));
  gap: 1rem;
}
```

Breaking it down:

| Part | Kya karta hai |
|---|---|
| `auto-fit` | Jitne cards fit ho sakein utne columns khud banao |
| `minmax(280px, 1fr)` | Minimum 280px, maximum available space |
| `min(280px, 100%)` | Mobile pe card kabhi overflow nahi karega |

---

### 🖼️ `aspect-ratio` for Images

Pehle image containers ki height fix karni padti thi. Ab `aspect-ratio` se height automatically calculate hoti hai width ke basis pe:

```css
.img__section {
  width: 100%;
  aspect-ratio: 16/10;
  overflow: hidden;
}
```

Chahe card ki width kuch bhi ho — image hamesha **same proportion** mein rahegi! ✅

---

### ✂️ `object-fit` + `object-position`

Sirf `aspect-ratio` se kaam nahi chalta — image ko container mein sahi se fit karna bhi zaroori tha:

```css
.img__section img {
  width: 100%;
  height: 100%;
  object-fit: cover;       /* crop karo, distort mat karo */
  object-position: center; /* center se crop ho */
}
```

| Value | Result |
|---|---|
| `object-fit: cover` | Container fill, image crop — no distortion ✅ |
| `object-fit: contain` | Full image visible, gaps aate hain |
| `object-fit: fill` | Stretch — distort hoga ❌ |

---

### 📐 `clamp()` for Fluid Typography

Media queries likhe bina font size responsive banane ke liye `clamp()` use kiya:

```css
font-size: clamp(1.1rem, 4vw, 1.5rem);
/*              min     fluid  max   */
```

Screen bade hone pe font smoothly scale karta hai — minimum aur maximum ke beech!

---

## Author

- **GitHub** — [@purvajadhav](https://github.com/purvajadhav)
- **Live Site** — [effulgent-concha-f02d25.netlify.app](https://effulgent-concha-f02d25.netlify.app/)