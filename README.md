# workbuddy-style

A Claude Skill that packages [WorkBuddy](https://www.workbuddy.cn/)'s
(腾讯云代码助手 AI Agent 办公产品) visual design system as reusable tokens —
so "build this in WorkBuddy's style" applies real, reverse-engineered colors,
type, shape, and motion instead of a generic AI-page look.

## What's in it

Tokens were pulled directly from a saved copy of workbuddy.cn's rendered
page source (exact hex values, `font-family` declarations, computed
`border-radius`, and CSS class-name vocabulary) — not guessed from a
screenshot:

- **Color**: mint-green `#28B894` accent on a black/white/gray base, with
  blue/purple reserved for decorative gradients only
- **Type**: rounded CJK display font (Alimama FangYuanTi VF, with a
  freely-licensed substitute noted for rebuilds)
- **Shape**: pill buttons (`999px` radius), flat thin-bordered cards, sharp
  small tags
- **Motion**: letter-by-letter headline reveal + infinite logo marquee
- **Signature component**: a conversational "agent working" demo panel in
  place of a static hero screenshot
- **Layout skeleton**: nav → hero → logo wall → feature grid → pricing →
  closing CTA → footer

## Install

Copy the `workbuddy-style/` folder into wherever your Claude setup loads
skills from (e.g. `.claude/skills/` for Claude Code, or upload the folder /
zipped `.skill` file in claude.ai / Claude Cowork's skill settings).

## Note on reuse

This captures WorkBuddy's *design system* — colors, type, shape, motion —
for style reference. It's not a template for relabeling WorkBuddy's actual
product: SKILL.md explicitly instructs writing original copy and never
reusing WorkBuddy's name, tagline, or logo.
