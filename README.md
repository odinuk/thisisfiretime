# FireTime Website

Marketing landing page for FireTime — the interval timer app for iPhone.

**Last Updated:** February 12, 2026

## Tech Stack

- **HTML5** — Single page, no framework
- **Tailwind CSS** (CDN) — Utility-first styling
- **Design System** — Custom CSS variables from `FireTime_Test/build/`
- **Lucide Icons** — Clean, consistent iconography
- **Vanilla JS** — Scroll reveals, tab switching

## File Structure

```
Website/
├── index.html              # Main landing page
├── README.md               # This file
├── firetime_images/        # Screenshots and assets
│   ├── apple-fitness.png
│   ├── quick-build.png
│   ├── workout-builder.png
│   ├── workout-complete.png
│   ├── watch-timer.png
│   ├── watch-live-activity.png
│   └── Simulator Screenshot - iPhone 17 - *.png
└── FireTime_Test/
    └── build/
        └── core/variables.css      # Design tokens
        └── components/variables.css
```

## Page Sections

| Section | Description |
|---------|-------------|
| Hero | App intro with 3 phone mockups (fan layout) |
| Quick Build | Feature highlight — workout generation |
| Active Timer | Timer UI showcase (2 phones, subtle rotation) |
| Workout Builder | Custom interval editing |
| Why FireTime? | 6 benefit cards with Lucide icons |
| Apple Watch | Watch companion showcase |
| Apple Fitness | Health integration with floating stat cards |
| Privacy | "Your data stays yours" — 0/0/0/100% stats |
| Exercise Library | Tabbed exercise browser (150+ exercises) |
| Testimonials | 3 user quotes |
| CTA | Final download prompt |
| Footer | Links to Privacy Policy, Terms, Contact |

## Design Tokens

All colors, radii, shadows, and durations use CSS variables from the design system:

```css
/* Colors */
--primitive-color-brand-primary-500    /* Main purple */
--primitive-color-brand-primary-950    /* Dark purple bg */
--semantic-color-surface-neutral-default
--semantic-color-text-neutral-bold

/* Radii */
--primitive-radius-md / lg / xl / 2xl

/* Transitions */
--primitive-duration-fast / base / slow
```

## Key Components

### Phone Mockup
```css
.phone-mockup {
  border-radius: 2.875rem;  /* 46px - iPhone corners */
  padding: 0.4rem;
  background: var(--primitive-color-neutral-gray-950);
}
```

### Watch Mockup
```css
.watch-mockup {
  border-radius: 2.875rem;  /* Apple Watch corners */
  padding: 6px;
}
```

### Benefit Cards
```css
.benefit-card {
  /* Hover: purple border + tinted background */
}
```

### Tab Buttons (Exercise Library)
- **Inactive:** Dark gray bg, muted text
- **Hover:** Lighter gray bg, border
- **Active:** Purple border, purple text, purple-tinted bg

### Exercise Pills
- **Default:** Gray-800 bg, bold white text
- **Hover:** Subtle purple border

## Animations

### Scroll Reveal
Elements with `.reveal` class fade in and slide up when scrolled into view.

### Floating Stat Cards (Apple Fitness)
```css
@keyframes floatCard {
  0%, 100% { transform: translateY(0); }
  50% { transform: translateY(-8px); }
}
```

### Timer Ring
```css
@keyframes ringProgress {
  from { stroke-dashoffset: 440; }
  to { stroke-dashoffset: 132; }
}
```

## Images

Screenshots should be placed in `firetime_images/`. The phone/watch mockups add bezels via CSS — just provide the raw screen content.

**Required images:**
- `quick-build.png` — Quick Build sheet
- `workout-builder.png` — Workout builder screen
- `workout-complete.png` — Completion screen
- `apple-fitness.png` — Apple Fitness showing FireTime workout
- `watch-timer.png` — Watch timer view
- `watch-live-activity.png` — Watch data view
- Timer screenshots (Simulator Screenshot files)

## Brand Colors

| Color | Hex | Usage |
|-------|-----|-------|
| Primary Purple | #AD68FF | Accents, CTAs, highlights |
| Primary Dark | ~#1a0d2e | Backgrounds, hover states |
| Success Green | #30D158 | Apple Fitness duration |
| Warning Orange | #FF9F0A | Apple Fitness calories |
| Error Red | #FF375F | Apple Fitness heart rate |

## Development

No build step required. Just open `index.html` in a browser.

For local development with live reload:
```bash
# Using Python
python -m http.server 8000

# Using Node
npx serve .
```

## Notes

- Download buttons currently show "Coming Soon!" alert
- Privacy Policy and Terms link to Notion pages
- Contact email: firetime.app@gmail.com
- All DEBUG/test code is in the app, not the website
