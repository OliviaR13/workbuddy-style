---
name: workbuddy-style
description: Apply WorkBuddy's (workbuddy.cn, 腾讯云代码助手's AI Agent 办公产品) visual design system — mint-green accent on black/white/gray, pill-shaped buttons, rounded CJK display font, letter-by-letter headline reveal, conversational product-demo panel, marquee logo wall, BEM-style pricing cards — when building a new page, mockup, or demo "in WorkBuddy's style" / "像 WorkBuddy 那样" / "workbuddy 风格". These are reverse-engineered design tokens (colors, type, shape, motion, layout skeleton) meant for restyling, not for reproducing WorkBuddy's own copy, logo, or trademark — always write original content for whatever product is actually being designed.
---

# WorkBuddy Visual Style

Design tokens reverse-engineered directly from workbuddy.cn's saved page
source (exact hex values, font-family declarations, computed radius/shadow,
and class-name vocabulary — not guessed from a screenshot). Use these as
fixed constraints; make deliberate choices for whatever they don't cover
(actual copy, imagery, section content).

## Color

| Role | Value | Usage |
|---|---|---|
| Primary accent | `#28B894` | icons, links, highlighted headline words, active states |
| Accent tint | `rgba(40,184,148,.05–.08)` | soft background behind badges/icon chips |
| Ink (primary button bg / text) | `#1A1A1A` (near-black, not pure `#000`) | main CTA background, body text |
| Border / divider | `#E1E1E1` | card borders, section dividers |
| Tinted section bg | `#F6FCFB` | alternating section backgrounds, very light mint |
| Secondary accents (illustration only) | `#0053E0` blue, `#2AB9FF` light blue, `#6C4DFF` / `#583ED3` purple | gradients and decorative graphics — not for text/buttons |

Overall feel: mostly black/white/gray with **one** mint-green functional
accent, plus blue/purple reserved for decorative gradients — not a dark
techy theme, a clean light one.

## Typography

- Display/heading (CJK): a rounded geometric font — WorkBuddy uses the
  proprietary "Alimama FangYuanTi VF". For rebuilds, substitute a freely
  licensed rounded CJK font (e.g. **ZCOOL KuaiLe** from Google Fonts) and
  say so; don't claim it's the same face.
  Fallback stack: `-apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif`
- Body/UI: system sans-serif stack, weight 400–500
- Headline weight is on the lighter/rounder side, not bold-and-tight — the
  personality comes from the letterform, not heaviness

## Shape & elevation

- Buttons: **fully pill-shaped**, `border-radius: 999px`. Primary = ink
  background + white text; secondary = outline, transparent bg
- Cards: soft rounding (`~12–16px`), thin `1px solid #E1E1E1` border, little
  to no drop shadow — flat and quiet, not the generic soft-gray-shadow
  SaaS-card look
- Small tags/labels: `border-radius: 4px` (sharper than buttons — radius
  scales with the element's role, not uniform everywhere)

## Motion signature

Two specific, named patterns — reuse these rather than generic fade-ins:

1. **Letter-by-letter headline reveal**: the hero `<h1>` is split into
   per-character `<span>`s, each fading/sliding up with a small staggered
   delay (~40–50ms per character). CSS: `opacity:0; transform:translateY(14px)`
   → animate to `opacity:1; transform:none` with `animation-delay` indexed
   by character position.
2. **Infinite logo marquee**: partner/ecosystem logos scroll continuously
   left in a duplicated flex row (`react-fast-marquee`-style: render the
   list twice back-to-back, `translateX(0)` → `translateX(-50%)` looped),
   with a horizontal fade mask at both edges.

No other scattered hover/scroll animation — motion is spent on these two
moments, not sprinkled everywhere (see restraint principle in
`frontend-design`).

## Signature component: conversational product-demo panel

Instead of a static hero screenshot, WorkBuddy's hero shows a **live-looking
task panel**: a user message bubble, a sequence of checkmarked "step" lines
(✓ done steps in ink, current step in gray with a pulsing/mint dot), and a
row of resulting file chips at the end (e.g. `.md` / `.docx` / `.pptx`
icons+filenames). This "show the agent working, not a screenshot" pattern is
the single most distinctive/reusable piece — prioritize it over a generic
product screenshot whenever the subject is any kind of AI-agent or
automation tool.

## Layout skeleton

1. Sticky top nav, blurred/translucent on scroll, pill CTA button on the right
2. Hero: small pill "eyebrow" badge → letter-reveal headline → one-sentence
   subhead → primary+secondary pill buttons → the conversational demo panel
   described above
3. Logo marquee ("已支持接入" / ecosystem row)
4. Feature grid — 4 cards in a single bordered grid (hairline dividers
   between cells, not separate shadowed cards)
5. Pricing — 3–4 tier cards, one visually distinguished as "recommended"
   (border color change + small pill tag), BEM-ish naming
   (`price-card__amount`, `price-card__features`) if writing CSS classes
6. Closing CTA band with tinted mint gradient background
7. Footer: multi-column links + download/QR block + legal line

## Applying this style to a new brief

- Treat color/type/shape/motion above as fixed; make deliberate choices for
  copy, imagery, and section content specific to the actual subject
- Always write **original copy** — never reuse WorkBuddy's actual product
  name, tagline, or logo; this is a style reference, not a template to
  relabel
- Ship as a single self-contained HTML file (inline CSS/JS, no build step)
  unless the brief asks for a framework
- If the brief's subject has nothing to do with AI agents, the
  "conversational demo panel" signature component may not fit — swap it for
  whatever hero treatment is most characteristic of the actual subject, and
  keep the color/type/motion/shape tokens instead
