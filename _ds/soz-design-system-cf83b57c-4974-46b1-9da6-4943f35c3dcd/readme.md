# SOZ Design System

SOZ is a web studio based in Bishkek, Kyrgyzstan — full-cycle website development for businesses and startups: design, development and launch, plus redesigns, admin panels/business-specific functionality, post-launch support, and AI integrations (a 24/7 client-response agent). Their differentiator: an in-house AI engineer runs 40 hand-trained AI agents (~10 dedicated to style/visual work) — trained manually over 500+ hours, not a "ChatGPT wrapper." Positioning is explicitly anti-template: *"Каждый сайт — под ваш бизнес, а не тема из каталога"* ("Every site is built for your business, not a catalog theme"). Process: **Бриф и цели → Дизайн → Разработка → Запуск** (Brief & goals → Design → Development → Launch). Contact: WhatsApp +996 501 656 526 · Instagram [@soz.sites](https://instagram.com/soz.sites) · Bishkek.

## Sources

- `uploads/Catalis Website Page Template for Webflow.jpeg` — a screenshot of **Aeline**, a real published Webflow template ([aeline.webflow.io](https://aeline.webflow.io/), by Temlis/temlis.com) for an AI-consulting agency. Used as a **layout/structural reference only** (hero, about, stat cards, services, pricing, testimonials, footer rhythm) — its colors, fonts and copy are *not* SOZ's; they belong to that template.
- `uploads/logo-1788892138526-m8wc.jpeg` ("soz logo.jpeg") — SOZ's real logo. Source of truth for brand color. Extracted to `assets/logo-transparent.png`.
- `uploads/more_screens-1788892096133-avft.pdf` ("SOZ_Brief_dlya_video.pdf") — SOZ's own creative brief (Russian), written for a promo-video shoot: company description, voice/tone rules with real Instagram examples, exact brand hex codes + typeface, 8 named portfolio projects, contact details. This is the primary source for everything in this file.
- No codebase, Figma file, or existing design system for SOZ was attached or accessible. (A paid Figma/code export exists for the Aeline template at temlis.com but sits behind a $149/yr paywall and was not purchased or accessed.) Because no component inventory source existed for SOZ itself, the components in this system are a standard set sized to a web agency's needs — see "Intentional additions" below.

## Content fundamentals

**Language.** SOZ's real audience and voice are Russian-language (Bishkek/Kyrgyzstan market, @soz.sites on Instagram). This design system's UI kit and component demo copy are written in English for general usability, but follow the exact voice rules below. Production copy for SOZ itself should be Russian, following these rules directly — the Russian examples are quoted verbatim, not translated over.

**Address & tone.** Informal "ty" (ты), never the formal "vy" — direct and personal, like talking to a friend. Short, punchy sentences. No corporate jargon or bureaucratic tone ("канцелярит", corporate pathos). A little boldness and self-irony is welcome — jokes and exaggeration are fine.

**Structure.** Open with a rhetorical question-hook: *"Кто такие SOZ?"* ("Who is SOZ?"), *"Хотите сайт, который ПРОДАЁТ?"* ("Want a site that SELLS?").

**Emphasis.** CAPS on key words for emphasis — not for shouting. No emoji appear anywhere in the brief's own example copy; this system does not use emoji.

**Real example phrases** (verbatim from @soz.sites, with gloss):
- «Твой сайт ОТНИМАЕТ у тебя ДЕНЬГИ. И ты даже не догадываешься…» — *"Your site is TAKING your MONEY. And you don't even realize it…"*
- «Сайт будет готов БЫСТРЕЕ, чем ты дочитаешь этот пост.» — *"Your site will be ready FASTER than you finish reading this post."*
- «Ваш бренд. Наша стратегия.» — *"Your brand. Our strategy."*
- «Дизайн — не украшение. Это стратегия.» — *"Design isn't decoration. It's strategy."*

**Copy filter.** Per the brief's own design principle: every element either sells, explains, or drives to action — cut anything that does none of the three. Their process is explicitly "без воды" (no fluff/filler).

## Visual foundations

**Color.** Two colors are locked by the logo and brief: dark navy `#0A0E17` (primary surface) and electric cyan `#00E5FF` (accent — headlines, glow, CTAs), with white text on dark. Everything else (a full navy neutral ramp, a light neutral ramp for body content, semantic success/warning/danger) was extrapolated in OKLCH to stay harmonious with those two anchors. See `tokens/colors.css`.

**Typography.** Manrope — SOZ's real brand font, confirmed in the brief ("already used on our site"). ExtraBold/Black for headlines and accents, Regular/Medium for body text. Self-hosted in `fonts/fonts.css` (latin + Cyrillic subsets, since SOZ's market reads Cyrillic). The brief's Golos Text/Inter fallback is a note for video-editing software without Manrope installed — irrelevant on the web, where the real font is always self-hosted.

**Spacing.** A rem-based scale from `--space-3xs` (4px) to `--space-4xl` (128px). Naming is inspired by the Aeline reference's own Client-First `spacer-tiny…xhuge` convention, mapped to SOZ's own values.

**Backgrounds.** Brand "moments" — hero, footer, CTA bands — sit on the dark navy canvas with cyan glow. Body/content sections use light neutral surfaces with navy ink text. That alternation (dark bookends, light body) is the site's rhythm, rather than all-dark or all-light. No real photography was supplied anywhere in the source material — every photo/image spot in the UI kit is an explicit placeholder. A subtle diagonal grain texture is used sparingly on dark hero surfaces for depth; no decorative gradients, no repeating geometric wallpaper patterns.

**Animation.** Snappy, confident easing (`--ease-out`, 120–200ms) — matches the brand's "без воды" (no fluff), fast, direct voice. Nothing bouncy or playful.

**Hover state.** On dark surfaces: lift (`translateY(-2px)`) plus an increased cyan glow-shadow. On light surfaces: a subtle background tint plus a darkened border.

**Press/active state.** Scale down slightly (0.97) and drop the glow — a tactile "pressed" feel.

**Borders.** None by default — dark cards separate from the canvas via glow/shadow, not a hairline border (elevation is conveyed by shadow, matching the brief's "cyan glow" direction for the logo reveal). On light surfaces, a 1px `--border-on-light` appears only where two same-color surfaces need a seam (input fields, table rows).

**Shadows.** Two families: neutral `--shadow-sm/md/lg` for light-surface elevation, and `--glow-cyan-sm/md/lg` — a glow, not a drop shadow — for dark-surface elevation, hover and focus.

**Corner radii.** Generously rounded: `--radius-md/lg` for cards, `--radius-full` (pill) for buttons and badges — echoing the fully-rounded letterforms and the circular "O" dot in the logo.

**Layout.** Centered container, 1200px max (1440px full-bleed for hero/footer bands). No fixed decorative elements beyond a slim sticky header.

**Transparency & blur.** Used only for the sticky header (translucent navy + backdrop-blur) and modal/dialog overlays — never decoratively elsewhere.

**Imagery.** No real photography was supplied. Placeholders throughout use `image-slot`-style drop zones; where a treatment is needed, a navy/cyan duotone tint keeps future real photography on-brand.

## Iconography

No icon font, sprite sheet, or SVG set was found in SOZ's source material. **Substituted [Lucide](https://lucide.dev) via CDN** — clean geometric outline icons (1.5–2px stroke, no fill) — chosen to pair with Manrope's geometric letterforms and the logo's circular motif. *Flagging this substitution*: if SOZ has a preferred icon library, swap the CDN link in one place (see any component using `<script src=".../lucide">`). No emoji or unicode-character icons are used anywhere in this system, matching the brief's own copy.

## Intentional additions

No codebase or Figma file defined SOZ's own component inventory, so this system authors a standard primitive set sized to a web agency's marketing site: `forms/`, `feedback/`, `overlay/`, `navigation/` groups, plus a `marketing/` group (SectionHeading, StatCard, PricingCard, TestimonialCard, PortfolioCard) — composing marketing pages is this agency's actual product, so those compositions are worth first-class components rather than one-off UI-kit markup.

## Index

## Index

- `styles.css` — import-only entry point; pulls in `fonts/fonts.css` (self-hosted Manrope, latin+cyrillic) and `tokens/*.css` (`colors.css`, `typography.css`, `spacing.css`, `effects.css`, `base.css`).
- `assets/` — `logo-transparent.png` (white+cyan, for dark surfaces), `logo-transparent-dark.png` (navy, for light surfaces), `logo-on-navy.jpg` (original upload).
- `guidelines/` — 19 foundation specimen cards (Colors, Type, Spacing, Effects, Brand) — see the Design System tab.
- `components/` (22 total, see below) — every directory has its own `@dsCard` demo.
- `ui_kits/marketing-website/` — the click-through site: `index.html` (Home, tagged for the Design System tab), `services.html`, `portfolio.html`, `contact.html` (working form).
- `SKILL.md` — Claude Code / Agent-Skills-compatible version of this system.

**Components** (`components/<group>/`):
- `forms/` — Button, IconButton, Input, Textarea, Select, Checkbox, Radio, Switch
- `feedback/` — Badge, Tag, Tooltip, Toast
- `overlay/` — Dialog
- `navigation/` — Tabs, Accordion, Header, Footer
- `marketing/` — SectionHeading, StatCard, PricingCard, TestimonialCard, PortfolioCard

See the Design System tab for the live, authoritative component/card list.
