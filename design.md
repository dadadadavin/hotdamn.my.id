# Design Specification & Style Guide: hotdamn.my.id

> **Document Type:** Design Brief & UI/UX Specification for Designer  
> **Core Direction:** **Option 1 (Pure Medium Minimalist)** + **Curated Editorial Upgrades**  
> **Motto:** *"White, Simple, Not Sloppy."*  
> **Target Audience:** Indonesian tech enthusiasts, political observers, youth, and digital professionals who value sharp journalism over noisy tabloid clickbait.

---

## 1. Brand Identity & Design Philosophy

`hotdamn.my.id` covers heavy-hitting, provocative topics—**Tech & AI, Politics, Scandals, National Conflicts, and Spicy Takes**. 

The design contrast is the key: **the topics are spicy and raw, but the design is sophisticated, calm, and pure white like Medium**. 

### Guiding Principles
1. **White & Distraction-Free:** No noisy ad grids, no floating popups, no garish colors. Let the words and stories command 100% of the reader's attention.
2. **Editorial Gravitas:** Elegant serif headlines paired with modern sans-serif body copy that feels like an upscale international publication (The Atlantic, Medium, Rest of World).
3. **Subtle "Spicy" Energy:** A single high-voltage accent color (Crimson / Fiery Vermilion) used with surgical precision—only for category badges, active links, and "Hot Take" callouts.
4. **Indonesian Mobile-First:** Over 85% of traffic will be mobile (WhatsApp/Telegram links). The layout must feel featherlight, buttery-smooth on 4G/5G, and effortless to read while commuting in Jakarta or across Indonesia.

---

## 2. Color Palette

| Token Name | Hex Code | Purpose & Usage |
| :--- | :--- | :--- |
| **Canvas Base** | `#FFFFFF` | Primary page background; pure crisp white. |
| **Canvas Subtle** | `#F9FAFB` | Card surfaces, blockquote backgrounds, code block panels. |
| **Text Primary** | `#111827` | Headings, titles, and body copy (softer than harsh `#000000`). |
| **Text Secondary** | `#4B5563` | Excerpts, secondary descriptions, author names. |
| **Text Muted** | `#9CA3AF` | Reading time, dates, copyright, placeholder text. |
| **Border Hairline**| `#E5E7EB` | 1px horizontal dividers between stories and header line. |
| **Border Subtle**  | `#F3F4F6` | Card borders, image borders. |
| **Accent Primary** | `#E11D48` | **"Hot Damn Crimson"** — Category pills, active indicators, WhatsApp hover states. |
| **WhatsApp Green** | `#25D366` | Dedicated 1-click Indonesian share button accent. |
| **Telegram Blue**  | `#229ED9` | Dedicated 1-click share button accent. |

*(Optional Dark Mode: Surface `#0D1117`, Text `#F0F6FC`, Border `#21262D`)*

---

## 3. Typography Hierarchy

We recommend pairing an editorial serif with **Plus Jakarta Sans** (a world-class Indonesian-designed sans-serif font) to give the site international polish with subtle Indonesian DNA.

```
Headlines:        Lora / Newsreader / Merriweather (Serif)
Body Text:        Plus Jakarta Sans / Inter (Sans-Serif)
Data / Metadata:  Geist Mono / JetBrains Mono (Monospace)
```

### Typographic Scale & Specs

| Element | Font Family | Size (Desktop / Mobile) | Weight | Line Height |
| :--- | :--- | :--- | :--- | :--- |
| **Site Masthead Logo** | Sans-Serif | `24px / 20px` | Bold 800 (tracking -0.04em) | `1.0` |
| **Article Main Title (H1)** | Editorial Serif | `40px / 28px` | SemiBold 600 | `1.25` |
| **Section Heading (H2)** | Editorial Serif | `28px / 22px` | SemiBold 600 | `1.35` |
| **Subheading (H3)** | Sans-Serif | `20px / 18px` | Medium 500 | `1.4` |
| **Story Card Title (Feed)** | Editorial Serif | `22px / 18px` | SemiBold 600 | `1.3` |
| **Story Excerpt** | Sans-Serif | `15px / 14px` | Regular 400 | `1.6` |
| **Article Body Copy** | Sans-Serif | `18px / 17px` | Regular 400 | `1.8` (Relaxed reading) |
| **Meta / Reading Time** | Monospace / Sans | `12px / 11px` | Medium 500 | `1.5` |

---

## 4. Page Layout & Grid Structure

### 4.1. Global Grid Specs
- **Reading Measure:** Max-width `720px` centered for single articles (ensures 65–75 characters per line, the gold standard for reading comfort).
- **Feed Container:** Max-width `840px` centered for homepage and category archives.
- **Outer Padding:** `24px` on desktop, `16px` on mobile screens.

```
+-------------------------------------------------------------------+
|  [ hot damn. ]         [Topik]  [Tentang]  [Kirim Tip]      [Cari]| (Sticky 56px)
+-------------------------------------------------------------------+
|                                                                   |
|   Category Filters:  [Semua]  [AI & Tech]  [Politik]  [Drama]     |
|   -------------------------------------------------------------   |
|                                                                   |
|   ARTICLE CARD 1 (Featured)                                       |
|   [AI & TECH]  ·  4 min baca  ·  25 Sep 2026                      |
|   Kenapa RUU AI Indonesia Bisa Jadi Bumerang Bagi Startup Lokal   |
|   Regulasi yang digadang-gadang melindungi data pribadi justru    |
|   berpotensi mematikan ekosistem startup tahap awal...            |
|   [Author Avatar + Nama]                                          |
|                                                                   |
|   -------------------------------------------------------------   |
|   ARTICLE CARD 2                                                  |
|   [POLITIK & DRAMA]  ·  3 min baca                                |
|   Di Balik Konflik Internal Koalisi: Siapa Mengorbankan Siapa?    |
|   ...                                                             |
+-------------------------------------------------------------------+
```

---

## 5. Key UI Components & Interactions

### 5.1. Header & Navigation (Medium Style)
- **State:** Sticky on scroll with subtle hairline border (`#E5E7EB`) on scroll.
- **Left:** Typographic wordmark `hotdamn.` (Lowercase, bold sans, crimson period).
- **Right:** Minimal text links (`Topik`, `Tentang`) + quick search icon.

### 5.2. Story Feed Card (Homepage)
- **Layout:** Vertical stack on mobile; side-by-side thumbnail on desktop (text on left, subtle 16:9 or 1:1 image on right).
- **Category Badge:** Tiny uppercase pill badge with subtle background (e.g. background `#FFF1F2`, text `#E11D48`).
- **Dividers:** Soft 1px horizontal rule (`#F3F4F6`) between stories—no heavy card box shadows.

### 5.3. Article Reading View (The Core Experience)
- **Top Bar:** 2px reading progress bar pinned to the top of the browser viewport.
- **Header Block:**
  - Category pill + publication date (`25 September 2026`) + estimated reading time (`5 menit baca`).
  - Large Serif headline.
  - Two-sentence bold standfirst / summary.
  - Author info row: circular avatar (40px), author name, author bio snippet.
- **Body Content:**
  - Generous paragraph spacing (`margin-bottom: 28px`).
  - Pull Quotes: Elegant 32px serif font with a 3px crimson left border and subtle `#F9FAFB` indent.
  - "Hot Take" Callout Box: Light card with rounded corners (`8px`), subtle crimson hairline border, and a bold flame/spark icon for spicy editorial commentary.

### 5.4. Indonesian Viral Distribution Bar (The Secret Weapon)
Since Indonesian content spreads primarily via WhatsApp family/office groups, Telegram channels, and X (Twitter):
- **Desktop:** Elegant sticky sidebar icons alongside the article text.
- **Mobile:** Sticky bottom bar that appears once the user scrolls past 30% of the article.
- **Actions:**
  1. **WhatsApp (Primary):** One-tap share with pre-formatted message:  
     `"[Judul Artikel] - hotdamn.my.id/link"`
  2. **Telegram:** Direct channel share.
  3. **X / Twitter:** Share with pre-filled tags.
  4. **Salin Tautan (Copy Link):** Instant toast notification *"Tautan tersalin!"*.

---

## 6. Micro-Interactions & Details
1. **Link Hover:** Subtle bottom border animation, never jarring.
2. **Image Zoom:** Medium-style lightbox zoom on image click (smooth transition over white overlay).
3. **Clean Code Blocks (for Tech/AI articles):** Minimalist monospace font with subtle copy-to-clipboard button in the top-right corner.
4. **Estimated Reading Time:** Automatically calculated (e.g., 200 words per minute for Indonesian prose).

---

## 7. Deliverables Checklist for the Designer
Please supply:
- [ ] **Figma / UI File:**
  - Desktop View (1440px) & Mobile View (375px/390px)
  - Homepage Feed (with category pills & featured story)
  - Single Article View (Headlines, body typography, blockquote, callout box)
  - Mobile Sticky Share Bar & WhatsApp share modal
- [ ] **Typography Scale & Font Files** (or Google Fonts links)
- [ ] **Favicon & Logo Wordmark Vector** (`hotdamn.` in SVG format)
- [ ] **OpenGraph Social Card Template (1200x630px)** for WhatsApp/X link previews
