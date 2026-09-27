# Design Specification & Style Guide: hotdamn.my.id

> **Document Type:** Finalized Design Specification & UI/UX Style Guide  
> **Aesthetic Architecture:** Modern 2-Column Newsroom Editorial (*Wired* / *The Verge* meets *Medium* readability)  
> **Brand Motto:** *"White, Clean, Sharp."*  
> **Target Audience:** Indonesian tech leaders, political observers, youth, and digital professionals who demand uncompromising journalism without noisy tabloid clickbait.

---

## 1. Brand Identity & Design Philosophy

`hotdamn.my.id` delivers hard-hitting, independent analysis of **Tech & AI, Politics, Scandals, and Power Dynamics in Indonesia**.

The visual philosophy relies on high-contrast elegance:
- **Clean White Canvas:** Pure `#FFFFFF` background with subtle `#FAFAFA` card surfaces and delicate `#F0F0F0` hairline dividers.
- **Hand-Crafted Signature Wordmark:** A distinct human touch using Google Font **`Playwrite BE WAL`**, signaling independence from corporate media conglomerates.
- **Zero Gimmicks / Zero Slop:** No flashing animations, no fake live green lights, no noisy banner ads. Pure, comfortable editorial readability.

---

## 2. Color Palette & Design Tokens

| Token Name | Value | Purpose |
| :--- | :--- | :--- |
| **`--color-canvas`** | `#FFFFFF` | Primary page background. |
| **`--color-card-bg`** | `#FAFAFA` | Sidebar widgets, cards, and author containers. |
| **`--color-primary`** | `#191919` | Headings, article titles, and body prose. |
| **`--color-secondary`**| `#555555` | Excerpts, subtitle leads, and secondary navigation. |
| **`--color-muted`** | `#767676` | Publication dates, reading durations, and copyright text. |
| **`--color-border`** | `#F0F0F0` | 1px horizontal and card dividers. |
| **`--color-tag-bg`** | `#F2F2F2` | Category badges and topic pill tags. |
| **`--color-accent`** | `#E11D48` | **Hot Damn Crimson** — Category labels, active indicators, and logo period. |

---

## 3. Typography Hierarchy

```
Logo Wordmark:       Playwrite BE WAL (Cursive Script)
UI, Meta & Headers:  Plus Jakarta Sans (Modern Geometric Sans)
Reading Prose:       Newsreader (High-Legibility Editorial Serif)
```

### Typographic Scales

| Component | Font Family | Size (Desktop / Mobile) | Weight | Line Height |
| :--- | :--- | :--- | :--- | :--- |
| **Masthead Logo** | `Playwrite BE WAL` | `34px / 28px` | Regular 400 | `1.0` |
| **Article Title (H1)** | `Plus Jakarta Sans` | `38px / 28px` | Bold 700 | `1.25` |
| **Article Subtitle** | `Plus Jakarta Sans` | `19px / 16px` | Regular 400 | `1.55` |
| **Section Header (H2)**| `Plus Jakarta Sans` | `26px / 22px` | Bold 700 | `1.3` |
| **Subheading (H3)** | `Plus Jakarta Sans` | `20px / 18px` | SemiBold 600 | `1.35` |
| **Story Title (Feed)** | `Plus Jakarta Sans` | `22px / 18px` | Bold 700 | `1.3` |
| **Article Body Prose** | `Newsreader` | `20px / 18px` | Regular 400 | `1.8` |
| **Pull Quotes** | `Newsreader` | `22px / 19px` | Italic 400 | `1.5` |
| **Metadata / Badges** | `Plus Jakarta Sans` | `12px / 11px` | Medium 500 | `1.4` |

---

## 4. Grid System & Responsive Architecture

### Desktop View ($\ge 960\text{px}$)
- **Max Width:** `1140px` centered with `24px` gutters.
- **2-Column Asymmetric Grid:**
  - **Main Column (`minmax(0, 1fr)` / `720px`):** Houses the stories feed or the article reading view.
  - **Sidebar Column (`340px`):** Sticky column containing "Liputan Terkait", "Kirim Bocoran Tip", and "Topik Populer".
  - **Gap:** `72px` between columns for breathing room.

```
+-------------------------------------------------------------------------+
|  hotdamn.                        Tech & AI    Politik   Konflik  Tentang|
+-------------------------------------------------------------------------+
|                                        |                                |
|  [Terkini]  [Tech & AI]  [Politik]     |  [Tentang hotdamn.]            |
|  ---------------------------------     |  Jurnalisme & analisis...      |
|                                        |                                |
|  ARTICLE FEED / READING VIEW           |  [Liputan Terkait]             |
|  Title, Excerpt, Metadata              |  Story 1...                    |
|  (720px optimal reading measure)       |  Story 2...                    |
|                                        |                                |
|                                        |  [Kirim Bocoran Tip]           |
|                                        |  redaksi@hotdamn.my.id         |
|                                        |                                |
|                                        |  [Topik Populer]               |
+-------------------------------------------------------------------------+
```

### Mobile & Tablet View ($< 960\text{px}$)
- Collapses seamlessly into a clean, single-column reading stream (`100%` width with `20px` side padding).
- Sidebar items flow naturally beneath the content at the bottom of the page.
- Category navigation scrolls horizontally with zero awkward wrap.

---

## 5. Component Specifications

1. **Header:** Height `72px`, fixed top with `1px solid #F0F0F0`, clean horizontal flex alignment.
2. **Category Tabs:** Minimal text links with clean `2px` black bottom border on active states (zero default browser outline rings).
3. **Story Cards:** Clean vertical flow with author circle avatar, publication date, bold title link, 2-line summary, category badge pill, and read time.
4. **Article Reading Prose:** Relaxed `1.8` line-height with generous `28px` paragraph spacing. Blockquotes feature a clean `3px solid #191919` left border.
5. **Distribution Bar:** Clean pill buttons for WhatsApp, Telegram, X, and one-tap Copy Link with floating toast confirmation.
6. **Whistleblower / Tip Card:** Subtle tinted widget (`#FFFBFB`, `#F7DEDE` border) encouraging readers to submit confidential news tips.
