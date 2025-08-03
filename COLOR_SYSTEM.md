# Pop Art Portfolio - Centralized Color System

This document explains how to use the centralized color system for the pop art portfolio website.

## Overview

All colors, gradients, shadows, and animations are centralized in `src/assets/colors.css` using CSS custom properties (CSS variables). This ensures consistency across all components and makes it easy to maintain and update the design.

## File Structure

```
src/assets/
├── colors.css          # Centralized color system
├── main.css           # Main styles (imports colors.css)
└── base.css           # Base styles
```

## Color Variables

### Primary Pop Art Colors

```css
--pop-red: #ff0000;
--pop-cyan: #00ffff;
--pop-yellow: #ffff00;
--pop-magenta: #ff00ff;
--pop-green: #00ff00;
--pop-dark-blue: #023047;
```

### Neutral Colors

```css
--pop-black: #000000;
--pop-white: #ffffff;
--pop-gray: #666666;
--pop-dark-gray: #333333;
```

### Background Colors

```css
--bg-primary: rgba(0, 0, 0, 0.95);
--bg-secondary: rgba(0, 0, 0, 0.8);
--bg-card: rgba(255, 255, 255, 0.1);
--bg-overlay: rgba(0, 0, 0, 0.9);
```

### Text Colors

```css
--text-primary: #ffffff;
--text-secondary: #cccccc;
--text-accent: #ffff00;
```

## Predefined Gradients (Now Solid Colors)

```css
--gradient-primary: var(--pop-dark-blue);
--gradient-secondary: var(--pop-dark-blue);
--gradient-accent: var(--pop-dark-blue);
```

## Text Shadows

```css
--text-shadow-primary: 2px 2px 0 var(--pop-black);
--text-shadow-accent: 4px 4px 0 var(--pop-red), 8px 8px 0 var(--pop-cyan);
--text-shadow-glow: 3px 3px 0 var(--pop-red), 6px 6px 0 var(--pop-cyan), 0 0 20px var(--pop-yellow);
```

## Box Shadows

```css
--box-shadow-primary: 4px 4px 0 var(--pop-yellow), 8px 8px 0 var(--pop-magenta);
--box-shadow-secondary: 6px 6px 0 var(--pop-yellow), 12px 12px 0 var(--pop-magenta);
--box-shadow-hover: 8px 8px 0 var(--pop-yellow), 16px 16px 0 var(--pop-magenta);
```

## Border Presets

```css
--border-thin: 2px solid var(--pop-black);
--border-medium: 3px solid var(--pop-black);
--border-thick: 4px solid var(--pop-black);
--border-extra-thick: 6px solid var(--pop-black);
```

## Animation Durations

```css
--animation-fast: 0.3s;
--animation-medium: 0.5s;
--animation-slow: 1s;
```

## Usage Examples

### In CSS

```css
.my-component {
  background: var(--gradient-primary);
  border: var(--border-thick);
  color: var(--text-primary);
  text-shadow: var(--text-shadow-accent);
  box-shadow: var(--box-shadow-primary);
  transition: all var(--animation-fast) ease;
}

.my-component:hover {
  background: var(--gradient-secondary);
  box-shadow: var(--box-shadow-hover);
}
```

### Utility Classes

The color system also provides utility classes for quick styling:

```html
<!-- Color utilities -->
<div class="pop-red">Red text</div>
<div class="bg-pop-cyan">Cyan background</div>
<div class="border-pop-yellow">Yellow border</div>

<!-- Gradient utilities -->
<div class="gradient-primary">Primary gradient</div>
<div class="gradient-secondary">Secondary gradient</div>

<!-- Shadow utilities -->
<div class="text-shadow-accent">Accent text shadow</div>
<div class="box-shadow-primary">Primary box shadow</div>

<!-- Animation utilities -->
<div class="animate-fast">Fast animation</div>
<div class="hover-lift">Hover lift effect</div>
```

## Component Integration

### 1. Import the color system

Make sure your component's CSS imports the color system:

```css
@import '../assets/colors.css';
```

### 2. Use variables instead of hardcoded colors

Instead of:

```css
background: #ff0000;
color: #ffffff;
border: 4px solid #000000;
```

Use:

```css
background: var(--pop-red);
color: var(--text-primary);
border: var(--border-thick);
```

### 3. Use predefined gradients and shadows

Instead of:

```css
background: linear-gradient(45deg, #ff0000, #00ffff);
box-shadow:
  4px 4px 0 #ffff00,
  8px 8px 0 #ff00ff;
```

Use:

```css
background: var(--gradient-primary);
box-shadow: var(--box-shadow-primary);
```

## Benefits

1. **Consistency**: All components use the same color palette
2. **Maintainability**: Change colors in one place
3. **Theme Support**: Easy to create different themes
4. **Performance**: CSS variables are optimized by browsers
5. **Accessibility**: Easy to implement high contrast modes

## Adding New Colors

To add a new color to the system:

1. Add the color variable to `src/assets/colors.css`:

```css
:root {
  --pop-orange: #ff6600;
}
```

2. Add utility classes:

```css
.pop-orange {
  color: var(--pop-orange);
}
.bg-pop-orange {
  background-color: var(--pop-orange);
}
.border-pop-orange {
  border-color: var(--pop-orange);
}
```

3. Use the new color in your components:

```css
.my-component {
  background: var(--pop-orange);
}
```

## Best Practices

1. **Always use variables**: Never hardcode colors in components
2. **Use semantic names**: Choose descriptive variable names
3. **Group related colors**: Keep similar colors together
4. **Document changes**: Update this file when adding new colors
5. **Test accessibility**: Ensure sufficient color contrast

## Migration Guide

To migrate existing components to use the color system:

1. Replace hardcoded colors with variables
2. Replace custom gradients with predefined ones
3. Replace custom shadows with predefined ones
4. Replace hardcoded animation durations with variables
5. Test the component to ensure it looks the same

Example migration:

```css
/* Before */
.my-button {
  background: linear-gradient(45deg, #ff0000, #00ffff);
  border: 4px solid #000000;
  color: #ffffff;
  box-shadow: 4px 4px 0 #ffff00;
  transition: all 0.3s ease;
}

/* After */
.my-button {
  background: var(--gradient-primary);
  border: var(--border-thick);
  color: var(--text-primary);
  box-shadow: var(--box-shadow-primary);
  transition: all var(--animation-fast) ease;
}
```
