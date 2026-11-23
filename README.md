# Moxie — Premium Habit Tracker

AI-powered habit tracker with a cinematic dark UI. Built for StackBlitz / GitHub.

**Business name:** Moxie  
**Stack:** React 19 + Vite + TypeScript

---

## Quick start (StackBlitz / local)

```bash
npm install
npm run dev
```

Open the URL Vite prints. Habits are saved in `localStorage`.

---

## Features included

- **Liquid-chrome style background** (canvas) — full-viewport, subtle motion
- **Moxie logo** with glass shine
- **Habit board** — toggle completion, streaks, 7-day dots, add new habits
- **Progress gallery** — accordion-style hover expand (AccordionGallery inspiration)
- **Crystal Ball AI** — orb + chat panel (Strands inspiration). Currently uses smart local replies; wire to any free LLM API
- **Star border CTA** — “Ask Moxie” button
- **Animated sections** on scroll
- **Crosshair cursor overlay**
- **Gradual blur** at the bottom of content

---

## Upgrade to real React Bits / ReactDrops components

Once the project is running, add the official components:

```bash
# Background
npx shadcn@latest add @react-bits/LiquidChrome-JS-CSS

# Crystal ball / AI orb
npx shadcn@latest add @react-bits/Strands-JS-CSS

# Premium animations
npx shadcn@latest add @react-bits/AnimatedContent-JS-CSS
npx shadcn@latest add @react-bits/GradualBlur-JS-CSS
npx shadcn@latest add @react-bits/Crosshair-JS-CSS
npx shadcn@latest add @react-bits/StarBorder-JS-CSS
npx shadcn@latest add @react-bits/AccordionGallery-JS-CSS

# Logo
npx shadcn@latest add https://reactdrops.dev/r/glass-slab-logo.json
```

Then replace the placeholder components in `src/components/` with the real imports. The current placeholders are deliberately styled to match the same aesthetic so the app looks finished immediately.

### Suggested LiquidChrome props (full viewport)

```tsx
<div style={{ position: 'fixed', inset: 0, zIndex: 0 }}>
  <LiquidChrome
    color="#ffffff"
    speed={0.2}
    amplitude={0.3}
    detail={4}
    thickness={1}
    interactive
    frequencyX={3}
    frequencyY={3}
    depth={1}
    roughness={0.3}
    exposure={1}
    rippleStrength={1}
    rippleSize={1}
    tilt={1}
    intro
    lightMode={false}
  />
</div>
```

### Strands as the AI orb

```tsx
<div style={{ width: 220, height: 220, position: 'relative' }}>
  <Strands
    listening={isListening}
    glass
    energy={0.65}
    colors={["#d95b56","#ba5046","#ffa24c","#ffe0b3","#93f1ff","#3569fa","#193d9b"]}
    interactive
    clickPulse
    intro
  />
</div>
```

### GlassSlabLogo for Moxie

```tsx
<GlassSlabLogo
  logo="/moxie-icon.svg"   // or your SVG
  slabs={17}
  depth={0.75}
  elevation={60}
  colors={["#a78bfa","#171717","#171717","#171717","#171717"]}
  reflectivity={1.65}
  style={{ height: 120 }}
/>
```

---

## Wiring a free LLM API

In `src/components/CrystalBall.tsx`, replace the `generateReply` call with your preferred free API (Groq, OpenRouter free models, Gemini free tier, etc.). Keep the same message state shape.

Example shape:

```ts
const res = await fetch('https://api.groq.com/...', {
  method: 'POST',
  headers: { Authorization: `Bearer ${import.meta.env.VITE_GROQ_KEY}`, ... },
  body: JSON.stringify({ messages: [...] })
})
```

Store the key in `.env` as `VITE_GROQ_KEY` (or equivalent).

---

## Project structure

```
src/
  App.tsx              # main layout + habit state
  components/
    LiquidChromeBackground.tsx
    MoxieLogo.tsx
    HabitBoard.tsx
    ProgressGallery.tsx
    CrystalBall.tsx    # AI orb + chat
    StarButton.tsx
    AnimatedSection.tsx
    CrosshairOverlay.tsx
    GradualBlurFooter.tsx
  index.css
  App.css
public/
  moxie-icon.svg
```

---

## Deploy / GitHub

1. Create a new GitHub repo
2. Push this folder
3. Open the repo on [stackblitz.com](https://stackblitz.com) → “Import from GitHub”
4. Run `npm install && npm run dev`

Enjoy building with Moxie.
