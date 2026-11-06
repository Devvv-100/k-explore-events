# Eventora – Responsive Event Management Website

Eventora is a responsive event management website built with **HTML5, CSS3 and vanilla JavaScript**. Users can explore upcoming events, search and filter them, view details and register with a validated form.

- **Live website:** `PASTE_YOUR_DEPLOYED_LINK_HERE`
- **GitHub repository:** `PASTE_YOUR_REPO_LINK_HERE`

## Features
| Requirement | How it is done |
|---|---|
| Hero section | Gradient hero with headline, call-to-action buttons, live stats and a countdown to the next event |
| Event cards | Name, date badge, venue, illustrated image, category and short description |
| Search | Real-time text search across name, venue, description and category |
| Category filter | Filter chips generated from the event data |
| Event details | A `<dialog>` modal with date, time, venue, seats, description and countdown |
| Registration form | Name, email, phone and event selection |
| Validation | JavaScript checks with inline error messages (see below) |
| Confirmation | Success screen after registering |
| Responsive design | CSS Grid, Flexbox, `clamp()` font sizes and media queries; hamburger menu on mobile |

**Bonus features:** dark/light mode (saved and follows system preference), countdown timers, animations, Local Storage registration management ("My tickets" with cancel).

## Tech stack
HTML5 (semantic elements, `<dialog>`), CSS3 (custom properties, Grid, Flexbox, animations), JavaScript (ES6+, no frameworks), Local Storage, Git and GitHub.

## Project structure
```
eventora/
├── index.html   # Page structure, semantic sections, modal markup
├── style.css    # Theme variables (light/dark), layout, components, responsive rules
├── script.js    # Event data, rendering, filtering, validation, countdown, storage
└── README.md
```

## Implementation notes
**Data-driven rendering.** All events live in the `EVENTS` array in `script.js`. Cards, category chips, hero stats and the form's event dropdown are generated from it, so adding an event only needs a new object.

**Search and filter.** `renderEvents()` filters the array by the active category and the search text, then rebuilds the card grid. An empty-state message shows when nothing matches.

**Registration validation.** Each field has a rule in the `rules` object and is checked on blur and on submit:
- Name: 3–50 letters, spaces, `.`, `'`, `-`
- Email: standard `name@domain.tld` pattern
- Phone: 10-digit Indian mobile number starting with 6–9
- Event: must be selected
- The same email cannot register twice for the same event

Invalid fields get a red border and a message below the field. On success, the registration is saved and the confirmation screen appears.

**Local Storage.** Registrations are saved under the key `regs` and the theme under `theme`. The "My tickets" section reads from storage and lets users cancel.

**Countdown.** A single `setInterval` updates the hero and modal countdowns every second from the event date.

**Theming.** Colours are CSS variables on `:root`; `[data-theme="dark"]` overrides them. The toggle switches the attribute and saves the choice.

**Responsive and accessible.** Mobile-first grid with `auto-fill`/`minmax`, a collapsible nav below 820px, a skip link, ARIA labels, visible focus styles and `prefers-reduced-motion` support.

## Run locally
Keep all files in the same folder and open `index.html`, or use the VS Code Live Server extension.

## Deployment
Deployed on **GitHub Pages / Netlify / Vercel** (static site, no build step).

## Possible improvements
Real event photos, a backend for storing registrations, email confirmations, and a React version.
