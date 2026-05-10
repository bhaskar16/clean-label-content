---
name: cleanlabel-design-system
description: "Use this skill whenever building, editing, or extending any frontend component, page, template, or visual asset for the CleanLabel° newsletter website or email. Covers brand identity, color palette, typography, spacing, component library, layout rules, email template structure, motion principles, and do/don't guardrails. Trigger before writing any HTML, CSS, React, or design code for CleanLabel°. Do NOT deviate from this system to add personal flair — consistency across every touchpoint is a core brand asset."
---

# CleanLabel° Design System

## 1. Brand identity & aesthetic direction

**Name:** CleanLabel°  
**The degree symbol (°)** is part of the logotype — always include it. It signals precision and scientific exactness. Never substitute with a regular period or omit it.

**Aesthetic direction:** Organic Editorial  
Not wellness-app bubbly. Not clinical white. Think *The Guardian's food section meets a laboratory notebook*. The design should feel like it was made by a thoughtful food journalist with a science background — trustworthy, airy, and slightly serious without being cold.

**The one thing a visitor should remember:** This is a publication that has done the work so you don't have to. The design reinforces that through clarity, generous whitespace, and zero visual noise.

**Aesthetic is NOT:**
- Purple gradients on white (generic wellness)
- Dark mode with neon accents (tech supplement brand)
- Maximalist illustration-heavy (children's food blog)
- Sterile all-white with black text only (medical journal)
- Earthy brown tones only (farm-to-table restaurant)

---

## 2. Color palette

### Primary palette — use these for all UI

```css
:root {
  /* Brand greens */
  --sage:             #4a7c59;   /* Primary brand color — CTAs, links, accents */
  --sage-light:       #e8f0eb;   /* Backgrounds, tag fills, verdict boxes */
  --sage-mid:         #a8c5b0;   /* Decorative borders, dividers, muted icons */
  --sage-dark:        #2d6b42;   /* Text on sage-light backgrounds */

  /* Brand ambers */
  --amber:            #c8832a;   /* Secondary accent — watch-list tags, CTAs on dark */
  --amber-light:      #fdf0e0;   /* Backgrounds for amber-context blocks */
  --amber-dark:       #8a5a1a;   /* Text on amber-light backgrounds */

  /* Neutrals */
  --warm-black:       #1a1a18;   /* Body text, headings */
  --brown:            #7a5c3d;   /* Tertiary accent — avoid-status tags */
  --brown-light:      #f2ece4;   /* Background for avoid/brown context */
  --brown-dark:       #5a3d22;   /* Text on brown-light backgrounds */
  --cream:            #faf7f2;   /* Page background */
  --cream-mid:        #f0ebe2;   /* Alternate section backgrounds */

  /* Semantic — ingredient status only */
  --status-clean:     #4a7c59;   /* Green dot — safe ingredient */
  --status-watch:     #c8832a;   /* Amber dot — watch list ingredient */
  --status-avoid:     #c0392b;   /* Red dot — avoid ingredient */
}
```

### Color usage rules

- Sage (`#4a7c59`) is the primary brand color. Use it for primary buttons, links, active states, icon accents, and the traffic-light "clean" status.
- Amber (`#c8832a`) is the secondary accent. Use it for the second CTA in a section, "watch list" tags, and alert-level callouts. Never use amber as the primary button on a green-heavy section — they will compete.
- Cream (`#faf7f2`) is the page background, never pure white. This warmth separates CleanLabel° from clinical/medical aesthetics.
- The ingredient traffic-light system (green/amber/red dots) is a core visual signature — it must be visually consistent across the website, email, and any app surfaces.
- Never use `#000000` pure black for text. Use `--warm-black` (`#1a1a18`) — it reads as rich and editorial rather than harsh.
- Never add new colors outside this palette without explicit approval. The palette's restraint is intentional.

---

## 3. Typography

### Font stack

```css
/* Import in <head> or @import at top of stylesheet */
@import url('https://fonts.googleapis.com/css2?family=DM+Serif+Display:ital@0;1&family=DM+Sans:opsz,wght@9..40,300;9..40,400;9..40,500&display=swap');

:root {
  --font-display: 'DM Serif Display', Georgia, 'Times New Roman', serif;
  --font-body:    'DM Sans', system-ui, -apple-system, sans-serif;
}
```

### Type scale

| Role | Font | Size | Weight | Style | Line height |
|---|---|---|---|---|---|
| Hero headline | DM Serif Display | 42–52px | 400 | Italic | 1.1 |
| Article headline | DM Serif Display | 28–36px | 400 | Italic | 1.2 |
| Section headline | DM Serif Display | 22–26px | 400 | Italic | 1.25 |
| Card headline | DM Serif Display | 16–20px | 400 | Italic | 1.3 |
| Section label | DM Sans | 10–11px | 500 | Uppercase, 0.14em tracking | 1.4 |
| Nav links | DM Sans | 13px | 400 | Normal | 1.4 |
| Body copy | DM Sans | 15–16px | 400 | Normal | 1.7 |
| Caption / meta | DM Sans | 11–12px | 400 | Normal | 1.5 |
| Tags / pills | DM Sans | 10–11px | 500 | Normal or uppercase | 1.0 |

### Typography rules

- **DM Serif Display in italic is the visual signature.** Every headline must be set italic. Upright Serif Display looks wrong for this brand — always use `font-style: italic`.
- Section labels (pillar names, "Issue 01", category names) are always `DM Sans`, uppercase, tracked at `0.14em`, sage color. They act as a navigational layer below the italic headlines.
- Body copy is `DM Sans` at 15–16px, `line-height: 1.7`. This generous leading is what gives the publication its airy, readable feel. Never reduce line-height below 1.6 for body text.
- Never use `font-weight: 600`, `700`, or `800` for DM Sans in body or UI. Weights are `300` (light captions only), `400` (body), and `500` (labels, emphasis). Heavier weights look wrong at this scale.
- Never use Arial, Inter, Roboto, or system-ui as a display font. DM Sans is the body workhorse — it handles everything non-headline.

---

## 4. Spacing system

Base unit: **8px**. All spacing values are multiples of 8.

```css
:root {
  --space-4:   4px;    /* Icon gaps, tight internal padding */
  --space-8:   8px;    /* Component internal gaps */
  --space-12:  12px;   /* Card internal padding (compact) */
  --space-16:  16px;   /* Standard component padding */
  --space-24:  24px;   /* Section internal spacing, column gutters */
  --space-32:  32px;   /* Between sections on mobile */
  --space-48:  48px;   /* Between major sections on desktop */
  --space-64:  64px;   /* Hero padding, page-level breathing room */
  --space-96:  96px;   /* Maximum vertical breathing room */
}
```

### Layout grid

```css
:root {
  --max-width-content: 680px;   /* Article text, email, max readable width */
  --max-width-wide:    1100px;  /* Full page max width including sidebars */
  --gutter:            24px;    /* Column gutter */
  --page-padding:      24px;    /* Horizontal page padding on mobile */
}
```

- Content (articles, email) max width: **680px**. This matches the email template width, so the reading experience is identical in browser and inbox — a deliberate design decision.
- Wide layouts (homepage, archive): max **1100px**, using a 3-column article grid on desktop.
- Article grid: 3 columns on desktop → 2 on tablet → 1 on mobile. Use `repeat(auto-fit, minmax(200px, 1fr))`.

---

## 5. Border radius

```css
:root {
  --radius-sm:   6px;    /* Tags, pills, status dots — small elements */
  --radius-md:   8px;    /* Buttons, inputs, inline components */
  --radius-lg:   12px;   /* Cards, modal sheets, panels */
  --radius-xl:   16px;   /* Feature cards, hero blocks */
  --radius-pill: 100px;  /* Buttons (CTA style), tag pills */
}
```

- Pill radius (`100px`) is used for all primary and secondary CTA buttons, and all tag/status pills. This is the most distinctive shape in the system.
- Card radius is `12px`. Never use `4px` for cards — it looks too corporate.
- Status dots (ingredient traffic light) are always perfect circles: `border-radius: 50%`, fixed width and height at `8px` (inline) or `10px` (standalone).

---

## 6. Component library

### 6.1 Buttons

```css
/* Primary CTA — sage filled, pill shape */
.btn-primary {
  background: var(--sage);
  color: #ffffff;
  border: none;
  padding: 10px 22px;
  border-radius: var(--radius-pill);
  font-family: var(--font-body);
  font-size: 13px;
  font-weight: 500;
  cursor: pointer;
  transition: opacity 0.15s ease;
}
.btn-primary:hover { opacity: 0.88; }

/* Secondary CTA — outlined sage, pill shape */
.btn-secondary {
  background: transparent;
  color: var(--sage);
  border: 1px solid var(--sage);
  padding: 10px 22px;
  border-radius: var(--radius-pill);
  font-family: var(--font-body);
  font-size: 13px;
  font-weight: 500;
  cursor: pointer;
  transition: background 0.15s ease;
}
.btn-secondary:hover { background: var(--sage-light); }
```

**Button rules:**
- Primary buttons are always sage green — never amber unless on a sage-heavy dark section.
- Never use `border-radius: 4px` for buttons. Pill shape is the system standard.
- Button text is always sentence case. Never ALL CAPS on buttons.
- Arrow suffix on directional CTAs: "Subscribe free →", "Read the archive →". Use the actual → character, not `>` or `»`.

### 6.2 Tags and status pills

Three tag types for ingredient status — these are non-negotiable brand signatures:

```css
.tag { display: inline-block; padding: 3px 11px; border-radius: var(--radius-pill); font-family: var(--font-body); font-size: 11px; font-weight: 500; }

.tag-clean  { background: var(--sage-light);   color: var(--sage-dark); }   /* Safe ingredient */
.tag-watch  { background: var(--amber-light);  color: var(--amber-dark); }  /* Watch list */
.tag-avoid  { background: #fcebeb;             color: #791f1f; }             /* Avoid */

/* Category / pillar tags — nav and article headers */
.tag-category { background: var(--sage-light); color: var(--sage); letter-spacing: 0.08em; text-transform: uppercase; font-size: 10px; }
```

### 6.3 Cards

```css
.card {
  background: #ffffff;
  border: 0.5px solid rgba(74, 124, 89, 0.15);   /* sage at 15% opacity */
  border-radius: var(--radius-lg);
  padding: var(--space-16) var(--space-24);
  transition: border-color 0.15s ease;
}
.card:hover { border-color: rgba(74, 124, 89, 0.35); }

/* Article card with colour-band accent */
.card-article { overflow: hidden; }
.card-article .band { height: 4px; margin: calc(-1 * var(--space-16)) calc(-1 * var(--space-24)) var(--space-16); }
/* Band colors by pillar: see Section 9 */
```

**Card rules:**
- Card border is always 0.5px — never 1px. The hairline border at low opacity gives the card definition without heaviness.
- Article cards have a 4px top color band indicating their content pillar (see Section 9 for pillar colors).
- Never use `box-shadow` on cards. The brand aesthetic relies on flat surfaces and hairline borders, not shadows.
- Never use a colored background on a card. Cards are always `#ffffff` against the cream page background.

### 6.4 Inputs and subscribe forms

```css
.input-email {
  border: 0.5px solid rgba(74, 124, 89, 0.3);
  border-radius: var(--radius-pill);
  padding: 10px 18px;
  font-size: 13px;
  font-family: var(--font-body);
  color: var(--warm-black);
  background: #ffffff;
  outline: none;
  width: 220px;
  transition: border-color 0.15s ease;
}
.input-email:focus { border-color: var(--sage); }
.input-email::placeholder { color: #a8b8ae; }
```

The subscribe form is always inline: `[email input] [Subscribe free →]` side by side, never stacked, on desktop. Stack vertically only on mobile (< 480px).

### 6.5 Verdict box

The verdict box is a recurring component that appears near the top of every article — it delivers the CleanLabel° ruling on an ingredient or product before the evidence.

```css
.verdict-box {
  border-left: 3px solid var(--sage);
  border-radius: 0;                          /* flat left border — no radius */
  background: var(--sage-light);
  padding: 14px 18px;
  margin: var(--space-24) 0;
}
.verdict-label {
  font-family: var(--font-body);
  font-size: 10px;
  font-weight: 500;
  text-transform: uppercase;
  letter-spacing: 0.12em;
  color: var(--sage);
  margin-bottom: 5px;
}
.verdict-text {
  font-family: var(--font-body);
  font-size: 13px;
  color: var(--sage-dark);
  line-height: 1.6;
}
```

**Verdict box rules:**
- The `border-left` accent is always `3px solid var(--sage)`. Never use `border-radius` on the box when using a single-side border — it must be `border-radius: 0`.
- For watch-list verdicts, swap to `border-left: 3px solid var(--amber)` and `background: var(--amber-light)`.
- For avoid verdicts, swap to `border-left: 3px solid #c0392b` and `background: #fcebeb`.

### 6.6 Ingredient traffic-light table

This is the most distinctive recurring visual element. Every ingredient decoder article includes one.

```css
.ingredient-row {
  display: flex;
  align-items: center;
  gap: 12px;
  padding: 10px 0;
  border-bottom: 0.5px solid rgba(74, 124, 89, 0.12);
}
.status-dot {
  width: 9px;
  height: 9px;
  border-radius: 50%;
  flex-shrink: 0;
}
.dot-clean { background: var(--status-clean); }
.dot-watch { background: var(--status-watch); }
.dot-avoid { background: var(--status-avoid); }

.ingredient-name { font-size: 13px; font-weight: 500; color: var(--warm-black); flex: 1; min-width: 140px; }
.ingredient-desc { font-size: 12px; color: #6b7a72; line-height: 1.5; flex: 2; }
```

### 6.7 Macro snapshot grid

Used in every ingredient/product article to show nutrition at a glance. Always 4 cells: Calories, Protein, Carbs, Fat.

```css
.macro-grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 8px;
  margin: var(--space-24) 0;
}
.macro-cell {
  background: var(--cream-mid);
  border-radius: var(--radius-md);
  padding: 12px 8px;
  text-align: center;
}
.macro-value {
  font-family: var(--font-display);
  font-size: 22px;
  font-style: italic;
  color: var(--warm-black);
}
.macro-label {
  font-size: 10px;
  font-weight: 500;
  color: #8a9a8e;
  margin-top: 3px;
  text-transform: uppercase;
  letter-spacing: 0.08em;
}
```

---

## 7. Navigation

### Desktop nav structure
`[Logo: CleanLabel°]` — left — `[Issues] [Ingredients] [Brands] [About]` — center — `[Subscribe →]` button — right

```css
.nav {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: var(--space-16) var(--space-32);
  border-bottom: 0.5px solid rgba(74, 124, 89, 0.15);
  background: var(--cream);
  position: sticky;
  top: 0;
  z-index: 100;
}
.nav-logo {
  font-family: var(--font-display);
  font-size: 20px;
  font-style: italic;
  color: var(--sage);
  text-decoration: none;
  letter-spacing: -0.01em;
}
.nav-links { display: flex; gap: var(--space-24); list-style: none; }
.nav-link { font-size: 13px; color: #6b7a72; text-decoration: none; }
.nav-link:hover { color: var(--sage); }
.nav-link.active { color: var(--warm-black); font-weight: 500; }
```

### Mobile nav
Hamburger at right. On open: full-width overlay with cream background, logo top-left, close button top-right, nav items stacked vertically at 20px, centered.

---

## 8. Page layout templates

### 8.1 Homepage

Structure (top to bottom):
1. **Nav** — sticky, cream background
2. **Hero** — centered, max-width 640px, sage category badge → italic headline → subheadline → inline subscribe form
3. **Latest issue preview** — full-width card with color band, excerpt, read link
4. **Article grid** — 3-column on desktop, alternating pillar color bands
5. **Why CleanLabel°** — 3-column value props, icon + short text each
6. **Subscribe CTA strip** — cream-mid background, centered, large italic headline + form
7. **Footer** — logo left, links center, subscriber count right, 0.5px top border

### 8.2 Article page

Structure:
1. **Nav**
2. **Article header** — category tag, italic headline (36px), deck (16px), meta row (reading time, issue number, date)
3. **Verdict box** — immediately below header
4. **Article body** — max-width 680px, centered, `line-height: 1.7`
5. **Ingredient table** — where applicable
6. **Macro grid** — where applicable
7. **Subscribe CTA** — inline at article end
8. **Related issues** — 3-card grid, same pillar

### 8.3 Archive / issues list

Simple 3-column grid of article cards. Each card: 4px color band, category tag, italic headline, deck (2 lines max), issue number + date. Filter bar at top: All / Label Literacy / Ingredient Decoder / Macro Science / Brand Audit / Ultra-Processed / Regulatory Watch.

---

## 9. Content pillar color coding

Every article belongs to one pillar. The pillar determines the card band color, the category tag color, and the article header accent. Apply consistently across the website and email.

| Pillar | Band color | Tag background | Tag text |
|---|---|---|---|
| Label Literacy | `#4a7c59` (sage) | `#e8f0eb` | `#2d6b42` |
| Ingredient Decoder | `#c8832a` (amber) | `#fdf0e0` | `#8a5a1a` |
| Macro Science | `#7a5c3d` (brown) | `#f2ece4` | `#5a3d22` |
| Ultra-Processed | `#3b6d8a` (slate blue) | `#e6f1fb` | `#0c447c` |
| Brand Audit | `#9b4a7a` (plum) | `#fbeaf0` | `#72243e` |
| Regulatory Watch | `#5a5a5a` (charcoal) | `#f1efe8` | `#3a3a38` |

---

## 10. Email template structure

The email template follows the same design language as the website. Maximum width: **600px**. All colors, fonts, and components must match the website system.

### Email sections (top to bottom)

```
[Header bar — sage green #4a7c59, full width]
  Logo left (italic, white) | Issue number right (small, white 70% opacity)

[Hero section — white background]
  Issue badge pill (sage-light bg, sage text, uppercase)
  Italic headline (DM Serif Display, 26px italic)
  Deck (DM Sans, 14px, muted)
  Meta row: reading time · reader count · cadence

[Verdict box — sage-light, 3px left border sage]

[Body — white, padding 24px 32px]
  Section headlines: DM Serif Display 16px italic
  Body: DM Sans 14px, line-height 1.7
  Ingredient table: status dots + name + description
  Macro grid: 4 cells, cream-mid background

[Coming next week — hairline divider, 3 items with leaf/microscope icons]

[CTA block — amber-light background, rounded 10px]
  Text left | Amber button right

[Footer — cream-mid background]
  Logo left | Navigation links right | Unsubscribe small text
```

### Email-specific rules

- Use inline CSS only — no `<style>` blocks. Gmail strips `<head>` styles.
- All fonts must have a web-safe fallback: `'DM Serif Display', Georgia, serif` and `'DM Sans', Arial, sans-serif`.
- Use `role="presentation"` on layout tables if using table-based layout for Outlook compatibility.
- Maximum image width: 560px (600px container minus 20px each side padding).
- All images must have `alt` text — screen readers and image-blocked email clients both depend on it.
- CTA buttons must be HTML text buttons, never images. Use `background-color`, `padding`, `border-radius`, and `display: inline-block` directly on an `<a>` tag.
- Never use `position: absolute` or `position: fixed` in email — these are ignored by most clients.
- Test in Gmail (web + Android), Apple Mail (iOS + Mac), and Outlook (Windows) before sending.

---

## 11. Motion and interaction principles

### Philosophy
One well-executed entrance animation creates more brand impression than twenty micro-interactions. CleanLabel° uses motion sparingly and purposefully — every animation should feel like breathing, not bouncing.

### Approved animations

```css
/* Page load — staggered fade-up for hero content */
@keyframes fadeUp {
  from { opacity: 0; transform: translateY(16px); }
  to   { opacity: 1; transform: translateY(0); }
}
.animate-in { animation: fadeUp 0.5s ease forwards; }
.animate-in:nth-child(2) { animation-delay: 0.1s; }
.animate-in:nth-child(3) { animation-delay: 0.2s; }

/* Card hover — subtle border reveal */
.card { transition: border-color 0.15s ease; }
.card:hover { border-color: rgba(74, 124, 89, 0.35); }

/* Button hover — slight opacity shift */
.btn-primary { transition: opacity 0.15s ease; }
.btn-primary:hover { opacity: 0.88; }

/* Nav link hover */
.nav-link { transition: color 0.12s ease; }
```

### Forbidden motion
- No bounce or elastic easing — feels playful, inconsistent with editorial tone
- No parallax effects — causes accessibility issues and layout shift
- No auto-playing animations on article content — the article is for reading
- No animation durations over 500ms — anything longer feels sluggish at this aesthetic register
- No animation on the ingredient traffic-light dots — they are status indicators, not decorations

---

## 12. Iconography

Use **Tabler Icons** (outline variant only) for all UI icons. Load via CDN:

```html
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/@tabler/icons-webfont@latest/tabler-icons.min.css" />
```

Usage: `<i class="ti ti-leaf" aria-hidden="true"></i>`

### Approved icon set for CleanLabel°

| Icon | Tabler name | Use |
|---|---|---|
| Leaf | `ti-leaf` | Clean/natural ingredient, logo accent |
| Microscope | `ti-microscope` | Science articles, research |
| Package | `ti-package` | Product / brand audit |
| Scan | `ti-scan` | Ingredient scanner, app cross-promo |
| Chart bar | `ti-chart-bar` | Macro / data content |
| Flame | `ti-flame` | Calories |
| Alert triangle | `ti-alert-triangle` | Watch-list ingredient |
| Circle check | `ti-circle-check` | Clean verdict |
| Clock | `ti-clock` | Reading time |
| Mail | `ti-mail` | Subscribe, email |
| World | `ti-world` | Global angle tag |
| Building bank | `ti-building-bank` | Regulatory body |
| Shield check | `ti-shield-check` | Watchdog source |
| Database | `ti-database` | Research tool |
| Star | `ti-star` | High shareability flag |

### Icon sizing rules
- Navigation: 18px
- Inline (next to text): 14–16px, `vertical-align: -2px`
- Standalone decorative: 24px maximum
- Never size icons above 24px — they become illustrations at that scale, which requires custom design

---

## 13. Accessibility requirements

- Color contrast: all text must meet WCAG AA (4.5:1 for body, 3:1 for large text). Sage (`#4a7c59`) on cream (`#faf7f2`) passes at 4.7:1. Always verify new color combinations.
- All icons that convey meaning must have `aria-label`. Decorative icons use `aria-hidden="true"`.
- All images must have descriptive `alt` text. Never use `alt=""` on content images.
- Focus states: never remove outline on focused elements. Style with `outline: 2px solid var(--sage); outline-offset: 2px;`
- Ingredient status dots cannot rely on color alone — always pair the dot with a text label ("Clean", "Watch", "Avoid") for screen readers.
- Subscribe form must have a visible `<label>` for the email input (can be visually hidden with `sr-only` class but must exist in DOM).

```css
.sr-only {
  position: absolute; width: 1px; height: 1px;
  padding: 0; margin: -1px; overflow: hidden;
  clip: rect(0,0,0,0); border: 0;
}
```

---

## 14. What this design system does NOT cover

- Editorial content, article writing, or research standards → see `SKILL.md` (writing & research skill)
- Ghost CMS theme configuration or template files
- SEO meta tags or structured data
- App design for the CleanLabel° ingredient scanner (separate design system)
- Social media asset templates
- Print or PDF versions of articles
