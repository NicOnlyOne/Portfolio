# Design Tokens Documentation

This portfolio uses a **design token system** to maintain consistent styling across the entire site. Design tokens are the single source of truth for design decisions like colors, spacing, typography, and more.

## What Are Design Tokens?

Design tokens are named variables that store visual design attributes. Instead of hardcoding values like `#428bca` or `16px` throughout your CSS, you use semantic names like `--ds-color-primary` or `--ds-space-3`.

### Benefits:
- **Consistency**: All design decisions in one place
- **Maintainability**: Change a color once, update everywhere
- **Scalability**: Easy to extend and theme
- **Framework Independence**: Tokens work with any CSS framework or vanilla CSS

## File Structure

The token system consists of two files:

```
css/
├── tokens.css           # Core design tokens (framework-independent)
└── bootstrap-bridge.css # Maps tokens to Bootstrap 5 variables
```

### Load Order

In your HTML, always load stylesheets in this order:

```html
<!-- 1. Framework (Bootstrap 5) -->
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css">

<!-- 2. Design Tokens -->
<link rel="stylesheet" href="css/tokens.css">

<!-- 3. Bootstrap Bridge -->
<link rel="stylesheet" href="css/bootstrap-bridge.css">

<!-- 4. Custom Styles -->
<link rel="stylesheet" href="css/style.css">
<link rel="stylesheet" href="css/blue.css">
```

## Token Categories

### Colors

#### Brand Colors
```css
var(--ds-color-primary)        /* Main brand color: #428bca */
var(--ds-color-primary-hover)  /* Hover state */
var(--ds-color-primary-active) /* Active/pressed state */
var(--ds-color-secondary)      /* Secondary brand color */
```

#### Semantic Colors
```css
var(--ds-color-success)  /* Green for success states */
var(--ds-color-info)     /* Blue for informational messages */
var(--ds-color-warning)  /* Yellow/orange for warnings */
var(--ds-color-danger)   /* Red for errors/destructive actions */
```

#### Neutral Colors
```css
var(--ds-color-light)  /* Light gray background */
var(--ds-color-dark)   /* Dark gray/black */
var(--ds-color-white)
var(--ds-color-black)
```

#### Text Colors
```css
var(--ds-color-text-primary)   /* Main text color: #333 */
var(--ds-color-text-secondary) /* Secondary text: #666 */
var(--ds-color-text-muted)     /* Muted/subtle text: #999 */
```

### Spacing

Use a consistent spacing scale (based on 4px/0.25rem):

```css
var(--ds-space-0)  /* 0 */
var(--ds-space-1)  /* 4px */
var(--ds-space-2)  /* 8px */
var(--ds-space-3)  /* 16px - base unit */
var(--ds-space-4)  /* 24px */
var(--ds-space-5)  /* 32px */
var(--ds-space-6)  /* 48px */
var(--ds-space-7)  /* 64px */
var(--ds-space-8)  /* 96px */
```

### Typography

#### Font Families
```css
var(--ds-font-family-base)      /* Open Sans for body text */
var(--ds-font-family-heading)   /* Raleway for headings */
var(--ds-font-family-monospace) /* Monaco for code */
```

#### Font Sizes
```css
var(--ds-font-size-xs)   /* 12px */
var(--ds-font-size-sm)   /* 14px */
var(--ds-font-size-base) /* 16px - base size */
var(--ds-font-size-lg)   /* 18px */
var(--ds-font-size-xl)   /* 20px */
var(--ds-font-size-2xl)  /* 24px */
var(--ds-font-size-3xl)  /* 30px */
var(--ds-font-size-4xl)  /* 36px */
var(--ds-font-size-5xl)  /* 48px */
```

#### Font Weights
```css
var(--ds-font-weight-light)    /* 300 */
var(--ds-font-weight-normal)   /* 400 */
var(--ds-font-weight-medium)   /* 500 */
var(--ds-font-weight-semibold) /* 600 */
var(--ds-font-weight-bold)     /* 700 */
```

### Border Radius

```css
var(--ds-radius-none)  /* 0 - sharp corners */
var(--ds-radius-sm)    /* 4px */
var(--ds-radius-md)    /* 6px - default */
var(--ds-radius-lg)    /* 8px */
var(--ds-radius-xl)    /* 12px */
var(--ds-radius-2xl)   /* 16px */
var(--ds-radius-full)  /* 9999px - fully rounded (pills, circles) */
```

### Shadows

```css
var(--ds-shadow-xs)  /* Subtle shadow */
var(--ds-shadow-sm)  /* Small shadow */
var(--ds-shadow-md)  /* Medium shadow - default */
var(--ds-shadow-lg)  /* Large shadow */
var(--ds-shadow-xl)  /* Extra large shadow */
```

## Usage Examples

### Using Tokens in Custom CSS

#### Example 1: Custom Button
```css
.my-custom-button {
  background-color: var(--ds-color-primary);
  color: var(--ds-color-white);
  padding: var(--ds-space-2) var(--ds-space-4);
  border-radius: var(--ds-radius-md);
  font-size: var(--ds-font-size-base);
  font-weight: var(--ds-font-weight-semibold);
  box-shadow: var(--ds-shadow-sm);
  transition: var(--ds-transition-base);
}

.my-custom-button:hover {
  background-color: var(--ds-color-primary-hover);
  box-shadow: var(--ds-shadow-md);
}
```

#### Example 2: Custom Card Component
```css
.portfolio-card {
  background-color: var(--ds-color-bg-primary);
  border: 1px solid var(--ds-color-border-light);
  border-radius: var(--ds-radius-lg);
  padding: var(--ds-space-5);
  box-shadow: var(--ds-shadow-md);
}

.portfolio-card__title {
  font-family: var(--ds-font-family-heading);
  font-size: var(--ds-font-size-2xl);
  font-weight: var(--ds-font-weight-bold);
  color: var(--ds-color-text-primary);
  margin-bottom: var(--ds-space-3);
}

.portfolio-card__description {
  font-size: var(--ds-font-size-base);
  line-height: var(--ds-line-height-relaxed);
  color: var(--ds-color-text-secondary);
}
```

#### Example 3: Spacing Utilities
```css
.section-padding {
  padding-top: var(--ds-space-7);
  padding-bottom: var(--ds-space-7);
}

.element-spacing {
  margin-bottom: var(--ds-space-4);
}
```

### Using Tokens with Bootstrap 5

Bootstrap 5 components automatically inherit token values through `bootstrap-bridge.css`:

```html
<!-- These buttons automatically use your design tokens -->
<button class="btn btn-primary">Primary Action</button>
<button class="btn btn-success">Success</button>

<!-- Forms use token border colors -->
<input type="text" class="form-control" placeholder="Name">

<!-- Typography inherits token font families and sizes -->
<h1>Heading uses Raleway</h1>
<p>Body text uses Open Sans</p>
```

## Customizing Tokens

### Changing the Primary Color

To change your brand color, edit `css/tokens.css`:

```css
:root {
  --ds-color-primary: #428bca;       /* Change this */
  --ds-color-primary-hover: #3071a9; /* And this */
  --ds-color-primary-active: #285e8e; /* And this */
}
```

All buttons, links, and components using the primary color will update automatically.

### Adding New Tokens

You can add custom tokens for specific needs:

```css
:root {
  /* Custom portfolio-specific tokens */
  --ds-color-portfolio-overlay: rgba(0, 0, 0, 0.7);
  --ds-animation-slide-duration: 600ms;
  --ds-hero-height: 100vh;
}
```

Then use them in your CSS:

```css
.portfolio-item-overlay {
  background-color: var(--ds-color-portfolio-overlay);
}

.swiper-slide {
  transition-duration: var(--ds-animation-slide-duration);
}
```

## Migration from Hardcoded Values

When updating existing CSS files (`style.css`, `blue.css`), replace hardcoded values with tokens:

### Before:
```css
.my-element {
  color: #428bca;
  padding: 16px;
  border-radius: 6px;
  font-family: 'Open Sans', sans-serif;
}
```

### After:
```css
.my-element {
  color: var(--ds-color-primary);
  padding: var(--ds-space-3);
  border-radius: var(--ds-radius-md);
  font-family: var(--ds-font-family-base);
}
```

## Bootstrap 5 Migration Notes

This portfolio has been upgraded from Bootstrap 3.3.0 to Bootstrap 5.3.3. Key changes:

### Class Name Changes
- `pull-left` → `float-start`
- `pull-right` → `float-end`
- `hidden-*` → `d-none d-{breakpoint}-block`
- Grid: `col-xs-*` → `col-*` (xs is now default)

### jQuery Compatibility
jQuery is kept for existing plugins (Owl Carousel, Swiper). Bootstrap 5 itself doesn't require jQuery.

## Browser Support

CSS custom properties (variables) are supported in:
- Chrome 49+
- Firefox 31+
- Safari 9.1+
- Edge 15+
- iOS Safari 9.3+

## Resources

- [Bootstrap 5 Documentation](https://getbootstrap.com/docs/5.3/)
- [CSS Custom Properties (MDN)](https://developer.mozilla.org/en-US/docs/Web/CSS/--*)
- [Design Tokens Community Group](https://www.w3.org/community/design-tokens/)

## Questions?

For questions about the design token system, please open an issue or contact the maintainer.
