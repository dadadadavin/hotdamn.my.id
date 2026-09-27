# Master Architecture & Production Blueprint: hotdamn.my.id

> **Domain:** [hotdamn.my.id](https://hotdamn.my.id)  
> **Brand & Niche:** Independent Indonesian Journalism & Sharp Commentary on Tech & AI, Politics, Scandals, and Power Dynamics.  
> **Visual Identity:** Modern 2-Column Newsroom Editorial (*Wired* / *The Verge* meets *Medium* readability) with clean signature handwriting logo.  
> **Core Engine:** Hugo (Go-powered Static Engine) + Flat Markdown Database  
> **Editorial Panel:** Private Git CMS at `/admin` (Sveltia / Decap CMS)  
> **Hosting & Edge Delivery:** Vercel (Hobby Free Tier) + Cloudflare Free DNS (Singapore/Jakarta Edge Caching)  
> **Running Cost:** \$0 / month (Zero Server Maintenance, Zero Database Downtime)

---

## 1. System Architecture Overview

```mermaid
flowchart TD
    subgraph Editorial["1. Editorial Workflow"]
        A["Editor / Redaksi"] -->|Opens /admin| B["Sveltia CMS (Web Panel)"]
        B -->|Commits Markdown + Images| C["GitHub Repository"]
    end

    subgraph BuildEngine["2. Automated Build Engine"]
        C -->|Git Push Webhook| D["Vercel Build Environment"]
        D -->|Compiles in < 30ms via Hugo (Go)| E["Static HTML + XML + RSS + CSS"]
    end

    subgraph EdgeCDN["3. Edge Delivery (Indonesia Latency Optimization)"]
        E --> F["Vercel Global Edge (Singapore POP)"]
        F --> G["Cloudflare Edge Proxy (Jakarta/Singapore POP)"]
    end

    subgraph Readers["4. Distribution Channels"]
        G -->|Sub-100ms TTFB| H["Indonesian Readers (Mobile & Desktop)"]
        G -->|News Sitemap + JSON-LD| I["Google News & Google Search"]
        G -->|1-Click Viral Sharing| J["WhatsApp & Telegram Groups"]
    end
```

---

## 2. Approved Visual & UX Specifications

### 2.1. Brand Identity & Typography
- **Masthead Logo:** **`Playwrite BE WAL`** (Google Fonts) — distinctive cursive signature script rendered cleanly without notebook guideline artifacts, accented by a crimson dot (`.`).
- **UI & Navigation:** **`Plus Jakarta Sans`** — Indonesian-designed sans-serif for sharp legibility on mobile screens (Telkomsel, Indosat, XL).
- **Article Reading Prose:** **`Newsreader`** / **`Charter`** — high-comfort editorial serif set at `20px` (desktop) and `18px` (mobile) with `1.8` line-height.
- **Palette:**
  - Background Canvas: `#FFFFFF` (Pure white)
  - Card & Widget Surfaces: `#FAFAFA`
  - Primary Text: `#191919` (High contrast, softer than pure `#000`)
  - Secondary & Metadata Text: `#555555` / `#767676`
  - Subtle Dividers: `#F0F0F0`
  - Accent Color: `#E11D48` (Crimson) for category labels and logo period.

### 2.2. Balanced 2-Column Newsroom Grid
To eliminate empty widescreen void and provide a balanced reading experience:
- **Global Container Width:** `1140px` centered with `24px` horizontal padding.
- **Left Column (`720px`):**
  - **Homepage:** Clean category tab bar (`Terkini`, `Tech & AI`, `Politik`, `Konflik`) with subtle underline active states, followed by story feed cards (Author avatar, date, headline, summary excerpt, category tag, and read duration).
  - **Article Page:** Clean category breadcrumb, prominent headline, 2-line subtitle lead, author metadata row (`Redaksi hotdamn. · X min read · Date`), story prose with pull quotes, topic tags, and 1-click share buttons.
- **Right Column (`340px` Sticky Editorial Sidebar):**
  - **Liputan Terkait:** Contextual cards showcasing other active stories to retain reader engagement.
  - **Kirim Bocoran Tip:** Dedicated whistleblower/insider tip box with one-click email link to `redaksi@hotdamn.my.id`.
  - **Topik Populer:** Clean pill tags for instant category exploration (`Kecerdasan Buatan`, `Infrastruktur`, `Startup`, `Pemilu`, `Data Privasi`).
  - **Sidebar Footer:** Quick links (`Tentang`, `RSS`, `Admin`) and copyright metadata.
  - **Sticky Behavior:** Pins smoothly alongside the reading column as readers scroll down long-form pieces.

---

## 3. SEO & GEO Master Infrastructure (Indonesia-First)

### 3.1. Indonesian Geographic Signals
- **Domain ccTLD:** `.my.id` automatically signals Indonesian geographic intent to Google and Bing.
- **Locale & Language Headers:**
  - `<html lang="id">`
  - `<meta http-equiv="content-language" content="id-ID">`
  - `<meta name="geo.region" content="ID">`
  - `<meta name="geo.placename" content="Indonesia">`
  - `<meta property="og:locale" content="id_ID">`

### 3.2. Google News & Search Indexing
- **Google News XML Sitemap:** Automatically generated at [`/news-sitemap.xml`](https://hotdamn.my.id/news-sitemap.xml) with Google-compliant `<news:news>`, `<news:publication>`, `<news:publication_date>`, and `<news:title>` tags.
- **Standard XML Sitemap:** Clean index generated at [`/sitemap.xml`](https://hotdamn.my.id/sitemap.xml).
- **RSS 2.0 Feed:** Full-text syndication feed at [`/index.xml`](https://hotdamn.my.id/index.xml) for aggregators and newsletter integrations.
- **Schema.org Structured Data:** Valid `NewsArticle` JSON-LD with Indonesian timezone offsets (`+07:00` WIB) on every article page.

### 3.3. Viral Indonesian Distribution Actions
- **WhatsApp Share:** Native 1-click URL with pre-encoded title and short canonical link.
- **Telegram Share:** Direct link for channel and group broadcasts.
- **X (Twitter):** Clean share action with headline and URL.
- **Salin Tautan:** Instant clipboard copy with non-intrusive toast feedback (*"Tautan tersalin!"*).

---

## 4. Codebase & Directory Structure

```text
hotdamn.my.id/
├── archetypes/
│   └── default.md              # Template for new articles
├── assets/
│   └── css/
│       └── style.css           # Master stylesheet (inlined directly into <head>)
├── content/
│   ├── tentang.md              # About publication page
│   └── posts/                  # Flat Markdown database
│       ├── kedaulatan-ai-indonesia-antara-jargon-politik-dan-realitas-server.md
│       ├── drama-koalisi-digital-siapa-sebenarnya-menguasai-data-pemilih.md
│       └── rekalibrasi-startup-jakarta-ketika-valuasi-halusinasi-terbentur-realita.md
├── layouts/
│   ├── _default/
│   │   ├── baseof.html         # Base HTML shell
│   │   ├── list.html           # Category & tag archives (2-column layout)
│   │   └── single.html         # Single article view (2-column editorial layout)
│   ├── partials/
│   │   ├── head.html           # SEO, GEO, Google Fonts, and Inlined CSS
│   │   ├── header.html         # 1140px header with Playwrite BE WAL cursive logo
│   │   └── footer.html         # Minimal publication footer
│   ├── index.html              # Homepage (2-column layout)
│   └── index.newssitemap.xml   # Google News XML sitemap template
├── static/
│   ├── admin/
│   │   ├── index.html          # Sveltia CMS web interface
│   │   └── config.yml          # CMS collection and field schema
│   └── robots.txt              # Crawler permissions & sitemap declarations
├── hugo.toml                   # Hugo site configuration (Go SSG)
├── vercel.json                 # Vercel security headers and caching policies
├── plan.md                     # This master production blueprint
└── design.md                   # Visual specification reference
```

---

## 5. Deployment & Production Setup (Step-by-Step)

### Step 1: Connect Git Repository to GitHub
```bash
git remote add origin https://github.com/<your-username>/hotdamn.my.id.git
git push -u origin main
```

### Step 2: Deploy to Vercel (Free)
1. Go to [vercel.com](https://vercel.com) and log in.
2. Click **"Add New Project"** $\rightarrow$ select the `hotdamn.my.id` repository.
3. Vercel automatically detects **Hugo** as the framework preset.
4. Click **Deploy**. Your site will build and be live globally in under 20 seconds.

### Step 3: Configure Cloudflare DNS & Custom Domain
1. In Vercel Project Settings $\rightarrow$ **Domains**, add `hotdamn.my.id` and `www.hotdamn.my.id`.
2. In your Cloudflare dashboard for `hotdamn.my.id`:
   - Add **CNAME** record: `hotdamn.my.id` $\rightarrow$ `cname.vercel-dns.com` (Proxy status: **Proxied**).
   - Add **CNAME** record: `www` $\rightarrow$ `cname.vercel-dns.com` (Proxy status: **Proxied**).
3. Set SSL/TLS encryption mode to **Full (strict)** in Cloudflare.
4. Enable **Auto Minify** and **HTTP/3** in Cloudflare for maximum Indonesian mobile speed.

---

## 6. Daily Editorial Workflow (Publishing Stories)

### Option A: Via the Web Admin Panel (`/admin`)
1. Visit `https://hotdamn.my.id/admin/` on any laptop or phone.
2. Log in with your GitHub account.
3. Click **"New Artikel & Liputan"**:
   - Write title, subtitle summary, select category (`Tech & AI`, `Politik`, `Konflik`).
   - Write or paste your article in rich text / markdown.
   - Click **Save** $\rightarrow$ **Publish**.
4. Sveltia CMS commits the file directly to your GitHub repository, and Vercel automatically redeploys your site in ~15 seconds.

### Option B: Via Terminal / Markdown
```bash
hugo new posts/judul-artikel-baru.md
# Edit the file in your favorite text editor
git add . && git commit -m "feat: publish new story" && git push
```
