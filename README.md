# ACE: Into the Spider-Verse

Editable source for the ACE Club event website.

The former Spider-Man/Gwen hands cinematic, ACE morph, and “ACE PRESENTS” opening have been removed. The site now opens directly on the interactive main experience.

## Tech stack

- Next.js-compatible React app powered by Vinext
- TypeScript
- Three.js for the dimensional city background
- GSAP + ScrollTrigger for cinematic scroll motion
- Plain CSS for the full visual system

## Requirements

- Node.js 22.13 or newer
- npm

## Run locally

```bash
npm install
npm run dev
```

Open the local URL printed in the terminal, normally `http://localhost:5173`.

## Production build

```bash
npm run build
npm run start
```

## Main files to edit

- `app/page.tsx` — page structure, event text, interactions, character selector, modal, registration behavior
- `app/globals.css` — layout, colours, typography, responsive styling, animation styling
- `app/layout.tsx` — title, description, favicon, and page metadata
- `public/assets/` — city and Spider-person artwork

## Add the Google Form

In `app/page.tsx`, find the registration button inside the section with `id="register"`.

Replace its current `onClick={() => setPortalOpen(true)}` with:

```tsx
onClick={() => window.open("YOUR_GOOGLE_FORM_URL", "_blank", "noopener,noreferrer")}
```

After doing that, the placeholder registration modal and its related `portalOpen` state can be removed if they are no longer needed.

## Update event details

Search `app/page.tsx` for:

- `DATE CLASSIFIED`
- `PORTAL UNLOCKING`
- `BUILD YOUR CREW`
- `Registration coordinates are being synchronized.`

Replace those placeholders with the confirmed date, time, venue, team size, rules, and registration status.

## Replace images

Keep replacement filenames the same for the quickest swap:

- `public/assets/spider-leap.png`
- `public/assets/spider-swing.png`
- `public/assets/spider-fall.png`
- `public/assets/spider-flip.png`
- `public/assets/falling-city.jpg`

Or change their paths in `app/page.tsx` and `app/globals.css`.

Use optimized WebP/PNG images with transparent backgrounds for characters. Avoid committing large videos unless the team intentionally adds a video sequence.

## Deploy quickly

### Vercel

1. Push this folder to a GitHub repository.
2. Import the repository at Vercel.
3. Keep the detected framework/build settings.
4. Deploy.

### Cloudflare/Sites-compatible build

Run `npm run build`. The generated deployment output is placed in `dist/` and follows `.openai/hosting.json`.

## Before publishing

- Add the final Google Form link.
- Replace classified event placeholders.
- Test desktop and mobile layouts.
- Confirm all artwork and audio are cleared for public use.
- Run `npm run build` and fix any reported errors.

## Notes

- Audio begins only after user interaction because browsers block autoplay.
- Reduced-motion and non-WebGL fallbacks are already included.
- The custom cursor is desktop-only by design.
- The current code intentionally uses no database or backend because registration redirects externally.
