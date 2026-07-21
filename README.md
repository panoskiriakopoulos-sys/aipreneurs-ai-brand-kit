# Aipreneurs AI Brand Kit

**14,000+ curated image prompts + branding template generator. Model-agnostic.**
Works with DALL-E, Midjourney, Flux, Stable Diffusion, GPT Image, Nano Banana, Seedream, and more.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Prompts: 14K+](https://img.shields.io/badge/Prompts-14%2C855-blue)](references/manifest.json)

---

## What Is This?

An AI agent skill with two modes:

**Search Mode** -- search a curated library of 14,000+ model-agnostic image generation prompts with sample images. Organized into 11 categories: social media posts, product marketing, profile portraits, posters, infographics, e-commerce, game assets, comics, YouTube thumbnails, app/web design, and more.

**Branding Mode** -- generate custom prompts from templates for logos (5 styles), color palettes, brand boards, hero images, business cards, social media assets, mockups, and full brand identity kits.

---

## Installation

### OpenClaw
```bash
openclaw skills install git:https://github.com/panoskiriakopoulos-sys/aipreneurs-ai-brand-kit
```

### Claude Code
```bash
npx skills i panoskiriakopoulos-sys/aipreneurs-ai-brand-kit
```

### Other AI Assistants
```bash
npx skills i panoskiriakopoulos-sys/aipreneurs-ai-brand-kit
```

---

## How to Use

### Search the Prompt Library

Describe what you need:

```
"I need a cyberpunk portrait avatar"
"Find me social media post prompts for a restaurant"
"Looking for product marketing visuals for a tech product"
"Help me find a YouTube thumbnail for a podcast episode"
```

The AI searches 14,000+ prompts, returns the top 3 matches with sample images, and can remix any prompt for your specific needs.

### Generate Brand Assets

```
"I need a logo for a beach taverna called To Kyma"
"Color palette for a luxury villa brand"
"Full brand kit for a web agency in Thessaloniki"
"Business card for a freelance photographer"
```

The AI generates ready-to-use prompts you can paste into any image generation model.

---

## Prompt Categories

| Category | Count |
|----------|-------|
| Social Media Post | 9,279 |
| Product Marketing | 5,438 |
| Profile / Avatar | 1,866 |
| Poster / Flyer | 908 |
| Infographic / Edu Visual | 586 |
| E-commerce Main Image | 552 |
| Game Asset | 673 |
| Comic / Storyboard | 616 |
| YouTube Thumbnail | 215 |
| App / Web Design | 224 |
| Uncategorized | 1,081 |

Prompts are community-sourced and auto-updated from GitHub. No credentials needed.

---

## Updates

Reference files auto-update on each use. To force a manual update:

```bash
cd <skill_dir>
node scripts/setup.js --force
```

---

## License

MIT
