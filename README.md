# VimanOne — Zero to Cockpit

**Live:** https://viman1.com

The VimanOne website: your step-by-step guide to becoming a commercial pilot in India. From prerequisites through the DGCA pathway, checklist, timeline, cadet vs. traditional routes, and professional guidance.

## Repository

| Folder | What's in it |
|---|---|
| `frontend/` | The website (Next.js 15, React 19, TypeScript, Tailwind CSS). Everything deployed at viman1.com. |
| `backend/` | Reserved for server code. Empty for now. |

## Build & Deploy

From `frontend/`:

```bash
npm install
npm run build
```

Cloudflare automatically deploys on every push to `main`. See `wrangler.jsonc` for hosting configuration.

## Where things live in `frontend/`

| Path | What it is |
|---|---|
| `src/lib/site.ts` | **All the website text**, including every step page. Edit this to change copy. |
| `src/app/` | Pages: the home page (`page.tsx`), step pages (`steps/[slug]`), legal pages |
| `src/app/globals.css` | Colours, fonts and the light/dark themes |
| `src/components/home/` | Home page sections — hero, checklist, timeline, cadet vs traditional |
| `src/components/steps/` | Step page parts — boarding pass, "Did you complete this step?", turbulence animation |
| `src/components/layout/` | Navbar, footer, logo, loading screen |
| `src/components/three/` | The 3D aeroplane and airfield |
| `src/components/ui/` | Shared buttons, cards and headings |
| `src/components/motion/`, `providers/` | Scroll and reveal animations |
| `src/lib/` (other files) | Legal text, the flight animation timeline, saved checklist progress |
| `public/` | Files served as they are (the 3D aeroplane model) |
| `assets/` | Source files the site does not serve |
| `README.md`, `DESIGN.md` | The detailed frontend guide and design notes |
