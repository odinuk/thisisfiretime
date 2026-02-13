# FireTime Website

Marketing landing page for FireTime — the interval timer app for iPhone.

**Last Updated:** February 13, 2026 (Evening)

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
├── support.html            # Support page with FAQ & Exercise Library
├── privacy.html            # Privacy Policy
├── terms.html              # Terms & Conditions
├── README.md               # This file
├── Videos/                 # Video assets
│   ├── FireTimeHeroVideo.webm
│   └── *.webm              # Background videos
├── firetime_images/        # Screenshots and assets
│   ├── apple-fitness.webp
│   ├── quick-build.webp
│   ├── workout-builder.webp
│   ├── CompleteWorkout.webp
│   ├── FireTimePhoneIcon.svg
│   └── Watch/
│       ├── TimerPhone.webp
│       └── FireTimeWatch.webp
└── FireTime_Test/
    └── build/
        └── core/variables.css
        └── components/variables.css
```

## Page Sections (index.html)

| Section | Description |
|---------|-------------|
| Hero | App intro with 3 phone mockups (fan layout with video center) |
| Speed | Full-width video bento with "intention to exertion" headline |
| Quick Build | Feature highlight — workout generation |
| Full Control | Custom interval editing |
| Active Timer | Timer UI showcase (watch + phone side by side) |
| Apple Fitness | Health integration with animated stat display |
| Privacy | "Your data stays yours" — 0/0/0/100% stats with video bg |
| CTA | Final download prompt |
| Footer | Links to Privacy Policy, Terms, Support |

## Support Page (support.html)

| Section | Description |
|---------|-------------|
| Exercise Library | Tabbed exercise browser (150+ exercises) with tooltips |
| FAQ | Apple-style "Questions? Answers." accordion |

## Mobile Responsiveness

The site is fully responsive with these key adaptations:

- **Hero phones**: Side phones hidden on mobile, center phone only
- **Feature sections**: Text above phone on mobile (`flex-col-reverse`)
- **Phone widths**: 92% width on mobile, fixed widths on desktop
- **Typography**: Scaled headings for mobile readability
- **Privacy section**: Portrait-style layout with taller min-height
- **Stats**: Centered on mobile, left-aligned on desktop

## Design Tokens

All colors, radii, shadows, and durations use CSS variables from the design system:

```css
/* Colors */
--primitive-color-brand-primary-500    /* Main purple #AD68FF */
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
  overflow: hidden;
}
.phone-mockup img,
.phone-mockup video {
  width: 100%;
  height: auto;
  display: block;
}
```

### Hero Video
- Center phone uses rounded corners (`rounded-[4rem]`)
- Drop shadow for depth (`filter: drop-shadow()`)

### Apple Fitness Stats
- Three-row layout with colored numbers
- Purple (duration), Yellow (calories), Red (heart rate)
- Centered on mobile, left-aligned on desktop
- Uses Nunito font for numbers

### Exercise Pills (Support Page)
- Tap-to-show tooltips on mobile
- Hover tooltips on desktop
- Staggered fade-in animation

### FAQ Accordion (Support Page)
- Apple-style "Questions? Answers." heading
- Chevron icons with rotation animation
- No card borders, clean minimal design

## Animations

### Scroll Reveal
Elements with `.reveal` class fade in and slide up when scrolled into view.

### Timer Ring
```css
@keyframes ringProgress {
  from { stroke-dashoffset: 440; }
  to { stroke-dashoffset: 132; }
}
```

## Videos

Videos are in `.webm` format. For Safari/iOS compatibility, `.mp4` versions are recommended as fallbacks.

**Current videos:**
- `FireTimeHeroVideo.webm` — Hero phone demo
- `8401254-hd_1920_1080_30fps.webm` — Speed section background
- `7676731-uhd_4096_2160_25fps.webm` — Privacy section background

## Brand Colors

| Color | Hex | Usage |
|-------|-----|-------|
| Primary Purple | #AD68FF | Accents, CTAs, highlights |
| Primary Dark | #1c1c1e | Backgrounds |
| Duration Purple | #AD68FF | Apple Fitness duration |
| Calories Yellow | #FFD60A | Apple Fitness calories |
| Heart Rate Red | #FF375F | Apple Fitness heart rate |

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
- Privacy Policy and Terms pages available
- Contact email: firetime.app@gmail.com
- Videos may not autoplay on iOS Safari (webm format limitation)
- All images use `.webp` format for better compression
