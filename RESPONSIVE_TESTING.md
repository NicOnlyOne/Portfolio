# Bootstrap 5 Responsive Testing Guide

This document outlines the comprehensive testing strategy for verifying responsive behavior after the Bootstrap 5 migration.

## Key Bootstrap 3 → Bootstrap 5 Grid Changes

### Breakpoint Changes
| Bootstrap 3 | Bootstrap 5 | Width |
|------------|------------|-------|
| xs (default) | (default) | <576px |
| sm | sm | ≥576px |
| md | md | ≥768px |
| lg | lg | ≥992px |
| - | xl | ≥1200px |
| - | xxl | ≥1400px |

### Class Changes in Your Portfolio

#### Utility Classes
- ✅ `.pull-right` → `.float-end`
- ✅ `.pull-left` → `.float-start`
- ✅ `.img-circle` → `.rounded-circle`
- ✅ `.text-right` → `.text-end`
- ✅ `.text-left` → `.text-start`
- ⚠️ `.hidden-xs`, `.visible-xs` → Bootstrap 5 uses display utilities (`.d-none`, `.d-sm-block`, etc.)

## Testing Checklist

### 1. Layout Testing by Breakpoint

#### Mobile (< 576px)
- [ ] Home section displays correctly
  - [ ] Avatar image is visible and properly sized
  - [ ] Name and title are readable
  - [ ] "Check my Portfolio" button is accessible
  - [ ] Certification badges stack properly
- [ ] Portfolio grid
  - [ ] Items stack in single column
  - [ ] Images maintain aspect ratio
  - [ ] Item overlays work on tap
- [ ] Resume section
  - [ ] Skills bars display full width
  - [ ] Progress bars animate correctly
  - [ ] Circular charts (language skills) render properly
  - [ ] Icon boxes in hobbies section stack vertically
- [ ] Contact form
  - [ ] All form fields are full width
  - [ ] Submit button is accessible
  - [ ] Map overlay is readable

#### Tablet Portrait (576px - 767px)
- [ ] Navigation switches to mobile menu
- [ ] Portfolio items display in 2 columns where appropriate
- [ ] Resume columns begin to show side-by-side
- [ ] Contact form fields start to align horizontally

#### Tablet Landscape (768px - 991px)
- [ ] Main navigation becomes visible
- [ ] Portfolio grid shows optimal item arrangement
- [ ] Resume section displays 2-column layout
- [ ] Skills section shows proper spacing
- [ ] Contact content and map split properly

#### Desktop Small (992px - 1199px)
- [ ] Full navigation is visible
- [ ] Portfolio masonry layout works correctly
- [ ] Three-column resume layout displays properly
- [ ] All content sections have proper margins

#### Desktop Large (≥1200px)
- [ ] Maximum content width is maintained
- [ ] All spacing is optimal
- [ ] No horizontal scroll appears

#### Desktop Extra Large (≥1400px)
- [ ] Layout doesn't become too wide
- [ ] Content remains centered
- [ ] Design tokens maintain proper scaling

### 2. Component-Specific Testing

#### Grid System
- [ ] `.container` maintains proper max-width at all breakpoints
- [ ] `.row` gutters work correctly (Bootstrap 5 uses CSS Grid internally)
- [ ] Column classes (`.col-md-6`, `.col-sm-4`, etc.) behave as expected
- [ ] Nested grids maintain proper spacing

#### Portfolio Grid
```html
<!-- Key classes to test: -->
<div class="portfolio-item">         <!-- Regular item -->
<div class="portfolio-item item-wide"> <!-- Wide item -->
```
- [ ] Regular items (1x1 grid cells)
- [ ] Wide items (2x1 grid cells - `.item-wide`)
- [ ] Image aspect ratios are maintained
- [ ] Overlays appear on hover/touch

#### Resume Section
```html
<!-- Key structure: -->
<div class="resume-grid padded">
  <div class="row">
    <div class="resume-col">...</div>
    <div class="resume-col">...</div>
    <div class="resume-col">...</div>
  </div>
</div>
```
- [ ] Three-column layout on desktop
- [ ] Two-column layout on tablet
- [ ] Single-column layout on mobile
- [ ] Skill bars render at correct widths (95%, 90%, 85%, 80%)
- [ ] Progress bar animations trigger on scroll
- [ ] Circular charts (EasyPieChart) initialize correctly

#### Forms
```html
<!-- Contact form structure: -->
<div class="row">
  <div class="col-md-6 form-group">...</div>
  <div class="col-md-6 form-group">...</div>
  <div class="col-md-12 form-group">...</div>
</div>
```
- [ ] Two-column layout for name/email on desktop
- [ ] Single-column layout on mobile
- [ ] Form validation works
- [ ] Submit button positioning (`.float-end`)

#### Navigation
```html
<!-- Main nav structure: -->
<nav id="main-nav" class="visible-on-start">
```
- [ ] Desktop navigation is visible on large screens
- [ ] Mobile toggle appears on small screens
- [ ] Menu toggle functionality works
- [ ] Swipe/scroll navigation between sections

### 3. Utility Classes Testing

#### Float Classes
- [ ] `.float-start` (left float) works correctly
- [ ] `.float-end` (right float) works correctly
- [ ] Floats clear properly in parent containers

#### Text Alignment
- [ ] `.text-center` centers text
- [ ] `.text-start` / `.text-end` align text properly
- [ ] Responsive text alignment works (`.text-md-start`, etc.)

#### Display Utilities
- [ ] Elements show/hide at correct breakpoints
- [ ] No unexpected visibility issues
- [ ] Mobile-specific elements display correctly

#### Spacing
Design tokens are used for spacing. Test that:
- [ ] `var(--ds-space-2)` through `var(--ds-space-10)` render correctly
- [ ] Padding and margins maintain visual hierarchy
- [ ] Spacing scales appropriately at different breakpoints

### 4. JavaScript Interactions

#### Swiper.js (Section Navigation)
- [ ] Horizontal swiping between sections works
- [ ] Navigation buttons function properly
- [ ] Section indicators show active state
- [ ] Mobile swipe gestures work

#### Owl Carousel
- [ ] Client logos carousel auto-plays
- [ ] Testimonials carousel transitions smoothly
- [ ] Carousel controls work on touch devices

#### Plugins
- [ ] EasyPieChart circles animate
- [ ] jQuery plugins initialize correctly
- [ ] No console errors related to Bootstrap

### 5. Cross-Browser Testing

#### Required Browsers
- [ ] Chrome (latest)
- [ ] Firefox (latest)
- [ ] Safari (latest - macOS/iOS)
- [ ] Edge (latest)
- [ ] Samsung Internet (mobile)

#### Known Issues to Check
- [ ] Flexbox behavior is consistent
- [ ] CSS Grid fallbacks work (if needed)
- [ ] CSS custom properties (design tokens) are supported
- [ ] Video autoplay works (home background)

### 6. Performance Testing

#### Load Times
- [ ] Bootstrap 5 CDN loads quickly
- [ ] No blocking resources on mobile
- [ ] Images are optimized

#### Rendering
- [ ] No layout shift during page load
- [ ] Smooth scrolling between sections
- [ ] Animations don't cause jank on mobile

### 7. Accessibility Testing

#### Keyboard Navigation
- [ ] Tab order is logical
- [ ] Focus indicators are visible
- [ ] Menu can be operated via keyboard

#### Screen Readers
- [ ] Alt text on images
- [ ] Form labels are associated correctly
- [ ] ARIA attributes are appropriate

#### Touch Targets
- [ ] Buttons are minimum 44x44px on mobile
- [ ] Adequate spacing between interactive elements
- [ ] No accidental taps

## Testing Tools

### Browser DevTools
1. **Chrome DevTools**
   - Device toolbar (Toggle device toolbar: Cmd/Ctrl + Shift + M)
   - Test at each breakpoint: 375px, 576px, 768px, 992px, 1200px, 1400px
   - Responsive mode with throttling

2. **Firefox Responsive Design Mode**
   - Cmd/Ctrl + Shift + M
   - Test specific devices (iPhone, iPad, Galaxy, etc.)

### Online Tools
- [ ] [BrowserStack](https://www.browserstack.com/) - Real device testing
- [ ] [Responsively App](https://responsively.app/) - Multi-device preview
- [ ] [LambdaTest](https://www.lambdatest.com/) - Cross-browser testing

### Manual Testing
- [ ] Test on actual devices:
  - iPhone (Safari)
  - Android phone (Chrome)
  - iPad (Safari)
  - Android tablet (Chrome)

## Common Issues & Solutions

### Issue 1: Portfolio Grid Layout Breaks
**Symptoms:** Items don't align properly, gaps appear
**Check:**
- Grid CSS in `style.css`
- `.portfolio-item` and `.item-wide` classes
- Flexbox/Grid properties

### Issue 2: Mobile Menu Doesn't Toggle
**Symptoms:** Menu button doesn't open menu
**Check:**
- Bootstrap 5 JS is loaded
- jQuery is loaded (for custom scripts)
- `.menu-toggle` event handlers

### Issue 3: Skill Bars Don't Animate
**Symptoms:** Progress bars stay at 0%
**Check:**
- JavaScript initialization
- Viewport detection
- CSS transitions are applied

### Issue 4: Responsive Classes Not Working
**Symptoms:** Elements show/hide at wrong breakpoints
**Check:**
- Updated to Bootstrap 5 breakpoint values
- Display utility classes syntax
- Custom CSS overrides

### Issue 5: Design Tokens Not Applied
**Symptoms:** Colors, spacing, or typography look wrong
**Check:**
- `tokens.css` loads after Bootstrap
- CSS custom property browser support
- Specificity issues with Bootstrap defaults

## Test Automation (Optional)

### Visual Regression Testing
```bash
# Using BackstopJS
npm install -g backstopjs
backstop init
# Configure scenarios for each breakpoint
backstop test
```

### Lighthouse Audits
```bash
# Test performance and accessibility
lighthouse https://your-portfolio-url.com --view
```

## Sign-Off Checklist

Before merging the PR:
- [ ] All breakpoints tested
- [ ] All major browsers tested
- [ ] No console errors
- [ ] No layout issues
- [ ] Performance is acceptable
- [ ] Accessibility checks pass
- [ ] Design tokens work correctly
- [ ] All interactive elements function
- [ ] Forms work and validate
- [ ] Navigation works on all devices

## Notes

- Bootstrap 5 uses `rem` units more consistently than Bootstrap 3
- Grid system now uses CSS Grid under the hood (with Flexbox fallback)
- Design tokens provide consistency across all breakpoints
- Always test with network throttling to simulate real-world conditions

---

**Last Updated:** March 5, 2026  
**Bootstrap Version:** 5.3.3  
**Branch:** `chore/bootstrap5-design-tokens`