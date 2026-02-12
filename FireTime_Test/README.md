# FireTime_Test - Design System Tokens

Auto-generated token export from DesignPush.

## Architecture: 3-Layer Token System

```
Layer 1: Primitive  ─┐
Layer 2: Semantic    ─┴─► tokens-core.json
Layer 3a: Patterns   ─┐
Layer 3b: Component  ─┴─► tokens-components.json
```

### File Structure

```
design-system/
├── tokens-core.json          # Source: Primitive + Semantic definitions
├── tokens-components.json    # Source: Patterns + Component definitions
├── tokens-extended.json      # Your customizations (never overwritten)
│
└── build/                    # Compiled outputs (do not edit)
    ├── core/                 # Primitive + Semantic tokens
    │   ├── variables.css
    │   ├── tokens.ts
    │   └── tokens.js
    │
    ├── components/           # Pattern + Component tokens
    │   ├── variables.css
    │   ├── tokens.ts
    │   └── tokens.js
    │
    ├── react/                # React components (coming soon)
    ├── tailwind/             # Tailwind preset (coming soon)
    └── shadcn/               # shadcn config (coming soon)
```

## Usage

### CSS
```html
<!-- Load both CSS files (core first, then components) -->
<link rel="stylesheet" href="design-system/build/core/variables.css">
<link rel="stylesheet" href="design-system/build/components/variables.css">
```

### TypeScript
```typescript
import { tokens as coreTokens } from './design-system/build/core/tokens';
import { tokens as componentTokens } from './design-system/build/components/tokens';

// Use semantic tokens for styling
const primaryBg = coreTokens.semantic['color-interactive-primary-default-light'];
```

### JavaScript
```javascript
const { tokens: coreTokens } = require('./design-system/build/core/tokens');
const { tokens: componentTokens } = require('./design-system/build/components/tokens');
```

### Dark Mode
```html
<html data-theme="dark">
```

## Token Usage Rules

When building UI that consumes these tokens:

1. **Always use semantic tokens first** (`--semantic-*`)
2. **Use primitive tokens only** if no relevant semantic token exists (`--primitive-*`)
3. **Hard-code values only** as a last resort

```css
/* Wrong - skips semantic layer */
.button {
  font-size: var(--primitive-typography-size-sm);
}

/* Right - uses semantic layer */
.button {
  font-size: var(--semantic-typography-label-sm-font-size);
}
```

## AI Workflow

### Reading Token Definitions
1. Read `tokens-core.json` for primitive + semantic definitions
2. Read `tokens-components.json` for pattern + component definitions
3. Use `tokens-extended.json` to add custom tokens

### Using Compiled Outputs
1. Import `build/core/variables.css` for primitive + semantic CSS variables
2. Import `build/components/variables.css` for pattern + component CSS variables
3. Both CSS files must be loaded (core first, then components)

### Adding Custom Tokens
```json
{
  "my-new-token": {
    "$value": "{primitive.color.brand.primary.500}",
    "$type": "color",
    "$metadata": {
      "createdBy": "claude",
      "createdAt": "2024-01-15T10:30:00Z",
      "reason": "Added for feature X"
    }
  }
}
```

## Important: What You Can Edit

Treat this design system like a **dependency** (similar to `node_modules/`). Don't edit files in `build/` - they will be replaced on updates.

| Path | Editable? | On Re-download |
|------|-----------|----------------|
| `tokens-core.json` | **No** | Replaced |
| `tokens-components.json` | **No** | Replaced |
| `tokens-extended.json` | **Yes** | Preserved |
| `build/*` | **No** | Replaced |
| `../src/*` (your app code) | **Yes** | Not touched |

## How to Customize

### 1. Add New Tokens → `tokens-extended.json`

```json
{
  "my-brand-gradient": {
    "$value": "linear-gradient(135deg, {primitive.color.brand.primary.500}, {primitive.color.brand.secondary.500})",
    "$type": "color",
    "$metadata": {
      "createdBy": "claude",
      "reason": "Brand gradient for hero sections"
    }
  }
}
```

### 2. Override CSS → Create overrides in your app

```css
/* src/styles/overrides.css */
@import '../design-system/build/core/variables.css';
@import '../design-system/build/components/variables.css';

/* Override specific component tokens */
:root {
  --component-button-primary-background: var(--semantic-color-brand-accent);
  --component-button-primary-border-radius: 9999px; /* pill buttons */
}
```

### 3. Create New Components → Use semantic tokens

```css
/* src/components/Alert.css */
.alert {
  padding: var(--semantic-spacing-inset-md);
  border-radius: var(--primitive-radius-md);
  border: 1px solid var(--semantic-color-border-neutral-default);
}

.alert-info {
  background: var(--semantic-color-surface-info-subtle);
  color: var(--semantic-color-text-neutral-default);
}
```

## Theme Support

CSS files include light and dark theme tokens:
- `:root` - Light theme (default)
- `[data-theme="dark"]` - Dark theme

Set `data-theme` attribute on `<html>` or `<body>` to switch themes.
