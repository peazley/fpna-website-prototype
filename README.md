# FPNA Demo Site

A static prototype for the Forest Park Neighborhood Association website rebuild. Built as a demo for the May 19 board conversation. Self-contained — no build step, no dependencies, no JavaScript framework. Just HTML, CSS, and Google Fonts.

## What's here

- `index.html` — Homepage with hero, next-meeting card, recent news, address checker, CTA
- `about.html` — Mission, boundaries (with address checker), 50-year history timeline, board roster
- `meetings.html` — Next meeting, upcoming schedule, past minutes archive
- `news.html` — News post grid + newsletter signup
- `get-involved.html` — Member signup, volunteer committees, 50th anniversary RSVP, sponsor tiers
- `contact.html` — Contact form, direct emails, press kit link
- `styles.css` — Shared design system (one file)

## Design notes

- **Typography**: Fraunces (serif) for display, Inter for body — both from Google Fonts
- **Palette**: forest green accent (`#2D5A3D`), warm cream background (`#FAF7F2`), deep forest text (`#1A2B1F`)
- **Layout**: max 1100px content width, generous vertical spacing, responsive down to mobile
- **No JavaScript framework**, no build step. The address checker and forms are visual demos — they pop a placeholder alert on submit, with a note about what the production version will do.
- **Accessibility**: semantic HTML, proper landmarks, ARIA labels on nav, focus states on inputs

## Placeholders to fill in

These are clearly marked in the markup and will need real data before launch:

- Board member names and roles (currently `[Name]`)
- Meeting location for May 19 ("Location to be confirmed")
- Mailing address P.O. box
- Real boundary map (currently a decorative SVG placeholder)
- Real Forest Park photography (currently typographic + accent-color only)
- Press kit PDF link
- Email addresses (currently generic `hello@`, `board@`, etc.)
- Past meeting minutes PDFs

## Running locally

Open `index.html` in any browser. No server required for the demo.

If you want a local dev server (for live reload):

```sh
# Python (any version):
python3 -m http.server 8080

# Or Node:
npx serve .
```

## Deploying to Vercel

This site is plain HTML, so Vercel will deploy it without any configuration.

### From GitHub:

1. Push this `fpna-demo/` directory to a new GitHub repo (e.g., `fpna-website-prototype`).
2. Sign into [vercel.com](https://vercel.com) and click "Add New Project."
3. Import the GitHub repo. When asked for framework, select "Other" (it's static HTML).
4. Leave build settings empty. Output directory: leave blank, or set to `/`.
5. Deploy. Vercel will give you a URL like `fpna-website-prototype.vercel.app`.

### Or directly via CLI:

```sh
npm i -g vercel
cd fpna-demo
vercel
```

Follow prompts. Vercel will deploy the directory and give you a preview URL within seconds.

## Showing this on May 19

Best practice: pull up the Vercel URL on your phone before the meeting starts. Tell Veronica "I built a quick prototype to give us something to react to — not asking you to commit, just want to make the conversation concrete." Then scroll through the homepage with her. Specifically:

- The hero + tagline establish the tone
- The "next meeting" card shows how a board member's actual content would appear
- The news grid shows the structure for future Updates
- The boundary section / address checker is the standout feature most NAs don't have
- The 50th anniversary banner and RSVP page directly serve the August party

If she's excited, the natural next step is "let me share this with the board." Send her the URL. Don't promise the production version yet — that decision still depends on the platform conversation and who'll maintain it long-term.

## What's intentionally not here

A few things you might expect that I left out for the demo:

- **Real boundary map data** — placeholder SVG only. Production version needs Mapbox or Google Maps with FPNA's actual GeoJSON.
- **Real address checker functionality** — UI only. Production version needs a geocoder + point-in-polygon check.
- **Working forms** — they don't submit anywhere. Production version needs MailerLite/Mailchimp, Tally/Fillout, or a managed form service.
- **Photos** — none. Easy to add a Forest Park hero photo, board headshots, event photos when content is ready.
- **Resources page** — the IA references it but I didn't build a full one for the demo. Easy follow-up.

These are all 1-2 day additions when the platform decision is made.

## Conversion paths

If they want to keep this stack:
- Move to Astro for component reuse and content-as-markdown — keeps the same look, gains a real CMS layer via Decap if needed
- Deploy stays on Vercel or Cloudflare Pages, free tier

If they want WordPress instead:
- This serves as visual/IA spec for a WordPress theme build
- Plug into a block theme (GeneratePress, Kadence) and recreate sections as blocks
- Managed hosting at Kinsta/Pressable

If they want Squarespace:
- Use this as the visual brief — Squarespace can closely approximate this design with their built-in tools
- Migration would be a content lift but the platform handles everything else
