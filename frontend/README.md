# VimanOne Frontend

**Live at:** https://viman1.com

The VimanOne website frontend: the DGCA pilot pathway, checklist, step guides, timeline, and professional guidance. Design system: [DESIGN.md](./DESIGN.md).

## Development

```bash
npm install
npm run dev
```

Then open `http://localhost:3000`.

## Build & Deploy

```bash
npm run build
```

Cloudflare Workers automatically deploys on every `git push` to `main`.

### Scripts

| Script | Purpose |
|---|---|
| `npm run dev` | Dev server |
| `npm run build` | Production build |
| `npm start` | Serve the production build |
| `npm run typecheck` | `tsc --noEmit` |

## Pages

| Route | What it is |
|---|---|
| `/` | Home: hero with 3D Airbus A320, the 8-step Checklist, prerequisites, timeline & investment, cadet vs traditional routes |
| `/steps/<step>` | One guide page per checklist step, generated from `stepGuides` in `src/lib/site.ts` |
| `/privacy-policy`, `/terms-and-conditions`, `/cookie-policy`, `/disclaimer` | Legal pages |

## Where things live

| I want to change… | Edit |
|---|---|
| Any website text, including the step pages | `src/lib/site.ts` |
| Legal page text | `src/app/<page>/page.tsx` and `src/lib/legal.ts` |
| Colours, fonts, themes, CSS animations | `src/app/globals.css` |
| A home page section | `src/components/home/` |
| Boarding pass, "Did you complete this step?", turbulence animation | `src/components/steps/` |
| Navbar, footer, logo, loading screen | `src/components/layout/` |
| What the aeroplane does as you scroll | `src/lib/storyboard.ts` |
| The 3D aeroplane and airfield | `src/components/three/` |
| Saved checklist progress | `src/lib/progress.ts` |

## Content

Content comes from the VIMAN pathway document and official DGCA portals. Every link is live and verified. All aviation facts are from official sources.

## Stack

Next.js 15 (App Router) · React 19 · TypeScript · Tailwind CSS v4 · GSAP +
ScrollTrigger · Motion · React Three Fiber + Drei + postprocessing · Lenis ·
Radix Slot · Lucide.

The aeroplane is a real Airbus A320 model (`public/models/a320.glb`); the
airfield, clouds and sky are generated in code. `assets/A320.glb` is an
identical source copy that the site does not serve.

## Performance & accessibility

- WebGL is client-only and lazy-loaded; the document indexes without it.
- A capability probe selects a quality tier; the render loop suspends entirely
  when the 3D stage leaves the viewport.
- `prefers-reduced-motion` disables smooth scroll, the preloader, magnetic
  hovers and the animation loop.
- Skip link, semantic landmarks, visible focus rings, native cursor preserved.

