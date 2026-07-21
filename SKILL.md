---
name: aipreneurs-ai-brand-kit
version: 1.0.0
description: |
  Brand kit prompt generator + 14,000+ curated image prompts.
  Works with ANY AI image model -- DALL-E, Midjourney, Flux, Stable Diffusion, GPT Image, Nano Banana, and more.

  Use this skill when users want to:
  - Find proven image generation prompts (portraits, products, social posts, avatars, posters)
  - Create a professional logo for a business or client
  - Generate brand color palettes, hero images, business cards, and social assets
  - Build a complete brand identity kit
platforms:
  - openclaw
  - claude-code
  - claude
  - cursor
  - gemini-cli
tags: [branding, logo, prompts, image-generation, brand-identity, design, visual-identity, prompt-library, brand-kit]
author: Aipreneurs Academy
license: MIT
---

> 🎨 14,000+ model-agnostic prompts · Branding templates for logos, colors, and social assets · [GitHub →](https://github.com/panoskiriakopoulos-sys/aipreneurs-ai-brand-kit)

# Aipreneurs AI Brand Kit

You generate image generation prompts. Two modes:

- **Search Mode** -- search a curated library of 14,000+ prompts with sample images, recommend the best matches, and remix for the user's content. Model-agnostic.
- **Branding Mode** -- generate custom prompts from templates for logos, color palettes, hero images, business cards, social assets, and full brand kits.

All prompts work with any text-to-image model -- DALL-E, Midjourney, Flux, Stable Diffusion, GPT Image, Nano Banana, Seedream, etc.

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

## Setup

Reference files auto-update on each use. To manually sync:

```bash
cd <skill_dir>
node scripts/setup.js --check   # Check freshness (>24h stale triggers auto-update)
node scripts/setup.js --force   # Force update
```

No credentials needed. References are pulled from GitHub.

---

## Mode Detection

| User Request | Mode |
|-------------|------|
| "logo / brand mark / award" | **Branding** -- Logo template |
| "colors / palette / brand colors" | **Branding** -- Color assets |
| "hero image / header / banner" | **Branding** -- Hero template |
| "business card / a" | **Branding** -- Business card template |
| "full brand / complete kit / brand identity" | **Branding** -- Full brand kit workflow |
| "social kit / profile / covers / highlights" | **Branding** -- Social assets |
| "mockup / " | **Branding** -- Mockup template |
| ANY general image request | **Search** -- 14K+ prompt library |
| Vague / unclear | Ask: "Brand assets (logo, colors, kit) or general image (portrait, social post)?" |

---

# SEARCH MODE -- Curated Prompt Library

## Prompt Data Structure

Each reference file contains an array of prompt objects:

```json
{
  "id": 12345,
  "content": "Image generation prompt text in English",
  "title": "Prompt title",
  "description": "What this prompt creates",
  "sourceMedia": ["sample_image_url_1", "sample_image_url_2"],
  "needReferenceImages": false
}
```

## Reference Files

<!-- REFERENCES_START -->

### Use Case Category Files

| File | Category | Count |
|------|----------|-------|
| `profile-avatar.json` | Profile / Avatar | 1,866 |
| `social-media-post.json` | Social Media Post | 9,279 |
| `infographic-edu-visual.json` | Infographic / Edu Visual | 586 |
| `youtube-thumbnail.json` | YouTube Thumbnail | 215 |
| `comic-storyboard.json` | Comic / Storyboard | 616 |
| `product-marketing.json` | Product Marketing | 5,438 |
| `ecommerce-main-image.json` | E-commerce Main Image | 552 |
| `game-asset.json` | Game Asset | 673 |
| `poster-flyer.json` | Poster / Flyer | 908 |
| `app-web-design.json` | App / Web Design | 224 |
| `others.json` | Uncategorized | 1,081 |

<!-- REFERENCES_END -->

## Category Matching

Match user intent to category by scanning the manifest `categories[].title` field:

- "avatar / profile / headshot / portrait" → Profile / Avatar
- "social / instagram / twitter / linkedin / post" → Social Media Post
- "product / ad / marketing / promo" → Product Marketing
- "poster / flyer / event / banner" → Poster / Flyer
- "infographic / diagram / chart / data" → Infographic / Edu Visual
- "ecommerce / product photo / listing" → E-commerce Main Image
- "game / sprite / character / asset" → Game Asset
- "comic / manga / storyboard" → Comic / Storyboard
- "youtube / thumbnail / video cover" → YouTube Thumbnail
- "app / ui / web / interface / mockup" → App / Web Design
- No clear match → search `others.json`

## Search Workflow

### Step 0: Refresh

Run `node <skill_dir>/scripts/setup.js --check` before searching. Auto-updates if >24h stale.

### Step 1: Clarify

Ask ONE question at a time. Minimum info: image type + topic. If too vague:

| Vague | Ask |
|-------|-----|
| "I need a portrait" | What style? Realistic, artistic, anime? Person, pet, or character? |
| "Help with infographic" | What type? Data comparison, process flow, timeline? What topic? |
| "Product photo" | What product? White background or lifestyle? Purpose? |
| "Social post image" | What topic? Platform? Vibe? |

### Step 2: Search

1. Identify target category from matching table
2. Search with grep (NEVER load the full JSON file):
```bash
grep -i "keyword" <skill_dir>/references/category-file.json
```
3. No match in primary category → search `others.json`
4. Still no match → say so, offer to switch to Branding Mode or generate a custom prompt

### Step 3: Present Results

Present up to 3 results. For each:

- **Title** (in user's language)
- **Description** (in user's language)
- **Sample image** -- use `sourceMedia[0]` URL. Never skip this -- images are essential.
- **Full prompt** in a code block

Ask: "Which one? Reply 1, 2, or 3. I can remix it for your specific needs."

### Step 4: Remix

When user selects a prompt:

1. **Collect details** -- ask relevant questions (what to change, specific content to incorporate)
2. **Output** the customized prompt with a note on what was changed

---

# BRANDING MODE -- Templates

## Prompt Anatomy

Branding prompts are built with 8 layers. Vague inputs → weak output.

| # | Layer | Example |
|---|-------|---------|
| 1 | Style | "premium modern minimalist vector logo" |
| 2 | Brand + Context | "Melmare, a luxury villa in Crete" |
| 3 | Icon Concept | ONE idea: "minimal wave" |
| 4 | Typography | "elegant geometric, clean spacing" |
| 5 | Colors | "electric blue and dark navy with white" |
| 6 | Background | "transparent background ONLY" |
| 7 | Negative Constraints | "no mockup, no 3D, no shadows, no borders" |
| 8 | Use Cases | "scalable for web, print, social media" |

## Industry-to-Template Matching

| Industry | Logo | Hero | Colors |
|----------|------|------|--------|
| Hotel / Villa / Resort | A (Premium) | 3-set | Earthy, coastal, warm neutrals |
| Agency / SaaS / Tech | B (Modern) | Single (abstract) | Blue, navy, electric accents |
| Restaurant / Taverna / Cafe | C (Traditional) | Single (interior) | Warm earth, terracotta, cream |
| Photography / Art / Beauty | D (Creative) | 3-set | Monochrome or bold accent |
| Real Estate / Legal / Medical | A (Premium) | Single (scene) | Navy, gold, white |
| Fitness / Ecommerce | B (Modern) | Single (action) | Bold, high contrast |
| Unknown | E (Budget) | Single | Ask preference |

## Logo Templates

### Template A -- Premium / Luxury

```text
Create a premium modern minimalist vector logo for "[BRAND NAME]", a
[INDUSTRY] in [LOCATION].
Transparent background (alpha channel) ONLY -- no white, black, colored,
textured, gradient, or shadow background. The output must be an isolated
logo in PNG format with full transparency.

Use elegant geometric typography with clean, balanced spacing. Integrate
a subtle [REGIONAL/CONTEXTUAL] inspired icon: [ONE SIMPLE CONCEPT].

Flat vector design, no mockup, no business card, no wall sign, no 3D
effects, no embossing, no lighting, no reflections, no drop shadows, no
border, no frame, no watermark, no extra text besides "[BRAND NAME]".
Centered composition with crisp edges and professional luxury branding
suitable for print and digital use.
```

### Template B -- Modern / Tech

```text
Create a professional logo for a [BUSINESS TYPE] named "[BRAND NAME]".
Style: modern minimalist.

Design a sleek "[LETTER]" integrated with [CONCEPT 1] and subtle
[CONCEPT 2] to represent [CORE VALUE].

Use clean geometric lines, flat vector design, rounded corners, premium
tech aesthetic, bold sans-serif typography for "[BRAND NAME]",
[COLOR 1] and [COLOR 2] color palette with [ACCENT] accents.
Transparent background, highly scalable, suitable for website, app icon,
business cards, and social media branding.
```

### Template C -- Local / Traditional

```text
Create a warm, inviting logo for "[BRAND NAME]", a [BUSINESS TYPE]
in [LOCATION]. Style: handcrafted / vintage / rustic.

Design an icon featuring [ONE SIMPLE CONCEPT], hand-drawn feel,
slightly imperfect lines for authenticity.

Use [serif / handwritten] typography for "[BRAND NAME]", warm earth
tones -- [COLORS]. Transparent background, no mockup, no 3D effects,
no drop shadows, no extra text. Suitable for menus, signage, social
media, and website favicon.
```

### Template D -- Creative / Artistic

```text
Create a bold, artistic logo for "[BRAND NAME]", a [BUSINESS TYPE].
Style: contemporary / avant-garde with clean execution.

Design an icon that represents [THEIR MEDIUM]. Minimalist aesthetic
with strong visual impact.

Use modern [sans-serif / display] typography, [COLOR SCHEME], transparent
background, scalable, no mockups, no extra elements. Suitable for
[USE CASES].
```

### Template E -- Budget / Quick

```text
Create a simple, clean logo for "[BRAND NAME]", a [INDUSTRY].
Keep it minimal. Use [2 COLORS]. Transparent background.
Brand name only -- no icon, or one very simple icon.
No mockup. No tagline. No 3D. No borders.
```

## Color Assets

### Color Palette

```text
Generate a professional brand color palette for [BUSINESS TYPE].
Include: Primary, Secondary, Accent, Neutral/dark, Background/light.
All with hex codes.

Requirements: [VIBE DESCRIPTION].
Colors must work for both digital and print.
Explain why each color was chosen.
```

### Color Usage Guide (run after palette)

```text
Create a brand color usage guide for [BRAND NAME] using these
colors: [INSERT HEX CODES].

For each color, specify best use, what NOT to pair it with, and a real
example from a website or business card. One paragraph per color.
No design jargon.
```

### Brand Board

```text
Create a visual brand board concept for "[BRAND NAME]".
Color swatches: [PRIMARY] dominant, [SECONDARY] and [ACCENT] supporting.
Add minimalist geometric shapes in [STYLE]. Clean white/cream background.

Text: "[BRAND NAME]" in [TYPOGRAPHY], tagline "[TAGLINE]".
Professional presentation slide. No mockups, no phone screens.
```

## Hero Images

### Single Hero

```text
Ultra-photorealistic 8K image of [DETAILED SCENE] in [SETTING].
16:9 horizontal. Editorial photography style. Natural [golden hour /
soft daylight] lighting. Shallow depth of field. [WARM/COOL] tones.
No text. No logos. No watermarks. Mood: [MOOD].

Negative: CGI, 3D render, digital art, illustration, overprocessed,
plastic textures, fake sky, wide-angle distortion, fisheye.
```

### 3-Image Hero Set

```text
Generate 3 professional website hero images for "[BRAND NAME]", a
[BUSINESS TYPE] in [LOCATION].

Style: ultra-photorealistic, editorial, 16:9. Shot on medium format,
warm natural lighting, shallow depth of field.

Image 1 -- [ESTABLISHMENT]: Wide shot of [the space/product]. Warm
ambient light. No people. Sky with clouds or sunset tones.

Image 2 -- [DETAIL]: Close-up of [key feature]. Soft focus, shallow
depth, bokeh background. Editorial composition.

Image 3 -- [EXPERIENCE]: Lifestyle shot showing [a person enjoying the
space/product]. Candid, natural, not staged. Warm atmosphere.

All three: No text. No watermarks. No logos. Realistic, not "AI perfect."
Natural imperfections in skin, lighting, texture.

Negative for all: CGI, 3D render, digital art, overprocessed, plastic
textures, fake sky, unnatural colors, no text, no logos.
```

## Business Card

```text
Create a [modern / premium / minimalist] business card for "[BRAND NAME]",
a [BUSINESS TYPE].

Front: Brand name prominent, [NAME] - [ROLE], contact info in clean
layout. [COLOR 1] dominant, [COLOR 2] accent, on [COLOR 3] background.

Back: [ICON / PATTERN] with tagline or service listing. 85x55mm.
Flat mockup. No 3D, no perspective, no extra text.
```

## Social Assets

### Social Profile Kit (4 assets)

```text
Create a cohesive social media branding package for "[BRAND NAME]".

4 assets in one image grid:
1. Profile picture (circular, 1:1) - brand mark on [COLOR] background
2. Facebook cover (820x312px) - brand name, tagline, subtle pattern
3. LinkedIn banner (1584x396px) - professional layout, service icons
4. Instagram story background (1080x1920px) - clean template

Brand colors: [HEXES]. Clean, professional, no stock photos.
```

### Social Post Template

```text
Clean social media post template for "[BRAND NAME]".
Square 1080x1080px. Brand colors: [HEXES].

Layout: Clean [COLOR] background. Logo small at top center. Large empty
center for text. Bottom: [URL] + [CTA BUTTON] in [ACCENT COLOR].
Minimalist, professional, no stock photos.
```

### Instagram Highlight Covers

```text
Design 6 Instagram Story Highlight icons for "[BRAND NAME]".
[STYLE] line-art on [COLOR] background, 1:1 square.

Icons: 1. Home/About  2. Services/Products  3. Reviews/Testimonials
4. Contact  5. Gallery/Portfolio  6. Offers/News

Simple symbols, consistent stroke width. [COLOR 1] on [COLOR 2].
No text. Clean, professional.
```

## Mockups

### Phone Mockup

```text
Realistic phone mockup with a mobile website for "[BRAND NAME]".
Screen shows a [STYLE] landing page with [KEY VISUAL]. Hand holding
phone naturally, soft indoor lighting, [DESK/BACKGROUND] surface.
Photorealistic, clean. No readable text on screen.
```

### Branded Merch Mockup

```text
Flat-lay mockup of branded merchandise for "[BRAND NAME]":
[ITEM 1] and [ITEM 2] with logo in [BRAND COLOR].
Arranged on [SURFACE]. Soft natural lighting from upper left.
[PLANT / PEN / COFFEE CUP] for scale. Aesthetic flat lay.
```

---

## Full Brand Kit Workflow

When user wants a complete brand identity, run in order:

1. Logo → 2. Color Palette → 3. Usage Guide → 4. Business Card → 5. Social Kit → 6. Hero Image

After each: "Want adjustments or move to the next asset?"

---

## Known Fixes

### Background Issues

If the generated image has a white/colored background instead of transparent: tell the model "Remove the background. I need a transparent PNG with alpha channel only."

### Text Rendering

Image models often misspell brand names or distort text. Workaround: generate the icon mark only ("no text in the icon"), add typography in Canva. Describe font style, not font name.

### Unwanted Mockups

If the model adds phones, cards, or wall signs: add these to the prompt: "no mockup, no business card, no wall sign, no phone screen, no 3D effects, no borders, no extra text."

### Plastic / AI Look

Remove "perfect, flawless, ideal, immaculate" from prompts. Add "natural texture, organic, realistic imperfections, editorial photography, candid expression."

### Chaotic Icons

Keep icon concept to ONE idea. "A wave" works. "A wave with mountain + sun + boat" produces chaos.

---

## Pro Tips

**For hero images, realism keywords:**
```
ultra-photorealistic 8K, editorial photography, 85mm f/1.4,
shallow depth of field, natural skin texture, warm tones

AVOID: perfect, flawless, 3D render, digital art, Unreal Engine
```

**For logos, typography:**
Describe the style, not the font name. "Bold condensed sans-serif" works better than "Helvetica Neue Bold" because models understand style descriptions better than specific font names.

**Language:** Respond in user's language. Always output the image generation prompt in English (best results across models).

**Quick start (bypass Q&A):**
- "Logo for [BRAND], [INDUSTRY]. [COLORS]. Transparent bg."
- "Color palette for [BUSINESS]. [VIBE]."
- "Hero image of [SCENE]. [LIGHTING]. 16:9. No text."
