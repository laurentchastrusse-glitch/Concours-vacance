# ekino Design System

A design system for **ekino** — an international digital agency, part of the Havas group, specialising in the design and development of digital products (websites, mobile apps, platforms). This system codifies ekino's visual identity for use across slide decks, client pitches, internal presentations, and prototyped product surfaces.

> **Scope of this system.** It is primarily a **slide / presentation** design system, derived from the official ekino Slidev theme ([`@ekino/slidev-theme-ekino`](https://github.com/ekino/slidev-theme-ekino)), the brand's Powerpoint template made web-native. It also includes the lower-level visual foundations (color, type, spacing, components) so it can be reused for any ekino-branded surface.

---

## Sources used

| Source | What it gave us |
| ------ | --------------- |
| [`github.com/ekino/slidev-theme-ekino`](https://github.com/ekino/slidev-theme-ekino) | Layout names, components (`SpeakerCard`, `Feedback`), slot conventions (`::logo::`, `::speaker::`), the README's layout list. We could only read the GitHub web README (no GitHub connector access at build time) — the Vue source for exact pixel parity wasn't available. **Reader: connect GitHub to refine against the Vue source.** |
| `meetup-ai-and-em/` (codebase) | A real ekino Slidev presentation in production — `slides.md` (10+ live slides), `slides-overview.md`, `pitch.md`, `package.json`. Used as ground truth for how the theme is used in practice: copy tone, slide flow, layout choices, image conventions. |
| `uploads/ekino_logo.jpeg` | Yellow square logomark with "ekino." wordmark + "A Havas Company" lockup. |
| `uploads/Graphik-Regular.otf` | Brand typeface (Regular weight only — see Caveats). |

---

## Index

| Path | What |
| ---- | ---- |
| `colors_and_type.css` | All color & typography tokens. Import this in any consumer. |
| `fonts/` | Graphik-Regular.otf (Regular only). |
| `assets/` | Logos (yellow lockup, black/white wordmarks). |
| `preview/` | Design-System tab cards — type, color, spacing, components, brand. |
| `slides/` | Slide template kit — `index.html` deck + per-layout JSX files mirroring the Slidev theme's `cover`, `title`, `two-cols`, `image-right`, `center`, `thank-you` layouts. |
| `ui_kits/slidev-theme-ekino/` | UI kit — recreation of the Slidev theme's components (`SpeakerCard`, `Feedback`, layouts) as static, click-through HTML/JSX. |
| `SKILL.md` | Cross-compatible Agent Skill definition. Drop into Claude Code to invoke `/ekino-design`. |

---

## CONTENT FUNDAMENTALS

ekino's voice is **French, professional, and refreshingly informal in conversational moments**. The brand is fluent in tech without being stiff. Drawn from the real meetup deck and `pitch.md`:

### Language
- **Primary language: French.** All public-facing slide copy is in French. English appears only in technical names (Astro, FFmpeg, OKR, Lead, hands-on).
- Sentences are short. Bullets are short. The brand respects the reader's attention.

### Tone
- **First person, plural-when-collective.** Authors speak as themselves ("Je m'appelle…", "j'ai pu créer le site en moins d'une semaine") and use *on* / *nous* for collective claims. They do not write *vous*-driven marketing copy; they write the way an engineer talks to engineers.
- **Confident but not boastful.** Achievements are framed as enabling ("Grâce à l'IA j'ai pu aller au bout de mon idée…") rather than self-congratulating.
- **A dash of warmth and humour.** Inside jokes ("Réunions avec plein de ssssss", "P-A Virenque", "dont 80% de revue de code 😁") show through on bullets and captions. Not on titles.

### Casing
- **Slide titles: sentence case.** `Contexte : l'IA omniprésente mais risquée` — never Title Case, never ALL CAPS.
- **Eyebrows / kickers in the system: ALL CAPS** with wide tracking (`.t-eyebrow` token). These are a UI device, not editorial copy.
- **Acronyms stay capitalised in body** (IA, RGPD, OKR, CI/CD).

### Punctuation
- French typography: **espace insécable before `:` `;` `!` `?`** (`Définition du rôle de EM`, `Contexte : l'IA…`).
- French quotation marks « … » preferred over straight quotes in body, but inline code keeps straight quotes.
- Em-dashes used for pauses, never as section separators.

### Emoji
- **Used, sparingly, and always inline.** Functional, not decorative — a 🛡️ next to "RGPD", a 📬 next to an email address, a 🚀 next to a stack name. Never used to break up paragraphs.
- Never used in titles. Reserved for bullet bodies and contact lines.

### Specific copy examples (verbatim from real deck)
- **Title:** `L'IA dans la vie d'un Engineering Manager`
- **Subtitle:** `Usages concrets et apprentissages`
- **Bullet:** `L'IA fait désormais partie du quotidien : ChatGPT, Claude, Gemini, Mistral, Perplexity ...`
- **Caption / aside:** `_Réunions avec plein de ssssss_` (italic, knowingly informal)
- **Quote attribution:** `> _"Il ne faut pas se définir uniquement par son travail"_  — Antoine Brette`
- **Thank-you:** `Merci pour votre attention` (always French — never "Thank you")

### Vibe
Professional French agency. Confident, useful, slightly self-deprecating. The deck is a colleague talking to colleagues, not a brand talking at customers.

---

## VISUAL FOUNDATIONS

ekino's visual identity is **stark, confident, and built on three colours**. The system rewards restraint.

### Colour
- **Three-colour palette: black (`#0A0A0A`), white (`#FFFFFF`), ekino yellow (`#FFD900`).** Yellow is the only accent; it is used as ink (text on black), as fill (full-bleed yellow slides for emphasis), and as a hairline (4px left border on quotes, underline accent on links). It is *not* used as gradient backgrounds, not as call-out boxes with rounded corners, not stacked with other accent colours.
- **Off-black not pure black.** `#0A0A0A` reads as black but is less harsh on screen.
- **Neutrals are warm-cool balanced greys** (`--neutral-50` through `--neutral-950`) for hierarchy. They never replace the yellow accent.
- **Semantic colours** (info/success/danger) exist but are reserved for product UI — never used in slide chrome.

### Type
- **Single family: Graphik.** A modern geometric sans, neutral and slightly humanist. Used for both display and body. No serif companion.
- **Weight contrast does the work.** Display = `900` (black), titles = `700` (bold), body = `400` (regular). The system deliberately skips a serif/sans pairing — hierarchy comes from weight + size, not face changes.
- **Tight tracking on display, normal on body.** Display copy uses `letter-spacing: -0.02em`.

### Spacing
- 4pt grid (`--space-0` → `--space-10`).
- **Slides are aired.** 80px padding minimum on slide edges, generous whitespace around titles. Density is deliberately low — the deck breathes.

### Backgrounds
- **Default: pure white.** This is the dominant surface.
- **Inverse: full-bleed black** for section dividers and dramatic statements.
- **Accent: full-bleed yellow** for the `title` layout — used for the slides that need to land hardest.
- **No gradients. No patterns. No textures.** Backgrounds are flat colour, full bleed.
- **Imagery is full-bleed when used as background, otherwise floats free** on white with no frame/border.

### Animation
- **Slidev's `view-transition`** between slides (default declared in `slides.md`).
- **`v-clicks` on bullets** — staged reveal of bullet points within a slide. This is the default interaction; the audience reads with the speaker, not ahead.
- **No bounces, no springs, no parallax.** Motion is brisk and minimal: short fades, view-transitions.
- Easing: `cubic-bezier(0.22, 1, 0.36, 1)` (`--ease-out`) for entrances, ~220ms.

### Hover / press states
- **Hover:** swap underline accent colour (yellow → black) for links. For buttons, invert (`bg-black` → `bg-yellow`, or `bg-yellow` → `bg-yellow-deep`).
- **Press:** darker shade (`--ekino-yellow-deep` `#F5C800`) + 1px nudge. No scale-shrink.

### Borders
- **1px solid borders, `--ekino-black`.** Used on cards, inputs, dividers.
- **4px solid yellow** used as quote indicator (left rail) and as a kicker/eyebrow underline.
- **Hairline borders use `--neutral-200`** in product UI.

### Shadows
- **Used sparingly.** The brand prefers borders + yellow over shadow.
- `--shadow-1` and `--shadow-2` exist for product cards.
- `--shadow-yellow` (a yellow-tinted ambient) exists for hero CTA emphasis but is rare.
- **No inner shadows.** No layered drop shadows.

### Transparency & blur
- Not part of the system. Surfaces are opaque.

### Corner radii
- **Default is `0` — sharp corners.** Cards use `--radius-3` (8px) at most; chips use `--radius-2` (4px); pills (`--radius-pill`) only for tag/badge clusters. The visual character is angular, not rounded.

### Imagery
- **Mostly black-and-white or full-colour photography** (real subjects, real settings — no stock illustration).
- Quirky personal illustrations occasionally used as cover/profile images, but on neutral backgrounds with **rounded-full** treatment only for portraits.
- Tone: warm, real. Not over-edited. No grain filters.

### Cards
- **White background, 1px black border, no shadow, sharp corners** is the default.
- Yellow-highlight cards (`bg: ekino-yellow-soft`, `border: 2px solid ekino-yellow-deep`) appear in slides for callouts.

### Layout rules
- The **logo sits top-left or top-right** of the cover slide, around 100×100px, on the yellow surface.
- Slide titles **left-aligned, top of slide**, never centered (except for `layout: title` which centers an enormous title on a yellow background).
- The **`title` layout** is unusual: full-bleed yellow + huge centered text — the system's only "stop and read" device.

### Iconography
See the dedicated section below.

---

## ICONOGRAPHY

The Slidev theme **does not ship a custom icon font**. The theme inherits Slidev's stock icon mechanism (Iconify, `<carbon-…>` / `<mdi-…>` Vue components on demand). The real `meetup-ai-and-em` deck makes a deliberate choice: **emoji over icons**.

### What's actually used in production decks
- **Inline emoji as iconography.** `🚀`, `🤖`, `🎨`, `💻`, `📬`, `📞`, `🛡️`, `📈`, `🐳`, `📦`, `🔍`, `🔤`, `✅`, `📹`, `🎯`, `🙊`, `📝`. These act as visual anchors in bullet lists.
- **No SVG icon set** is bundled into the theme repo.
- **Logos as raster (`.png` / `.jpg`)** for tooling references (Astro, FFmpeg, Whisper, etc.).
- **QR codes** generated on the fly via the `<Feedback>` component (uses `qrcode` package under the hood).

### This system's stance
1. **Default to emoji** for inline list anchors. Match the production deck's vibe.
2. **For UI / product surfaces** (not slides), use **Lucide** via CDN — clean, geometric, matches Graphik's tone. Stroke width 1.75. Sized in multiples of 4 (16, 20, 24).
   - CDN: `https://unpkg.com/lucide@latest/dist/umd/lucide.js`
3. **Never** invent custom SVG glyphs for things that should be emoji (people, food, weather, gestures, tools).
4. **Never** mix icon families on the same slide.

> **Substitution flagged:** Lucide is *not* official ekino. It's a reasonable analog because the actual repo doesn't define one. If ekino has an internal icon library, drop SVGs into `assets/icons/` and update this section.

---

## CAVEATS / SUBSTITUTIONS

- **Graphik weights missing.** Only `Graphik-Regular.otf` was provided. The system falls back to synthetic bold for Medium/Semibold/Bold/Black. **Please upload `Graphik-Medium.otf`, `Graphik-Semibold.otf`, `Graphik-Bold.otf`, `Graphik-Black.otf`** if available — `colors_and_type.css` has the `@font-face` blocks ready to uncomment.
- **GitHub connector unavailable at build time.** I built against the Slidev theme's public README + a real consumer codebase (`meetup-ai-and-em`). I did not read the Vue source of the layout files. Connect GitHub and re-run for pixel-exact parity with the upstream theme.
- **Iconography is a system-level guess** (Lucide) — see ICONOGRAPHY above.
- **Logos are reconstructed.** The yellow lockup is a JPEG; the SVG wordmark versions in `assets/` were created by recomposing the wordmark in Graphik. If you have official SVG masters, drop them in `assets/` to replace.
