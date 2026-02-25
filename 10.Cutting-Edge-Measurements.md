```markdown
# 🚀 Advanced CSS - Phase 5 Cutting-Edge Features

## 1. 🎥 `aspect-ratio` - Perfect Video Embeds

**`aspect-ratio`** = Maintain perfect proportions automatically!

### Common Ratios
```
16/9  → Video/YouTube (most common)
4/3   → Old TVs  
1/1   → Square (Instagram)
3/2   → Photos
9/16  → Stories/TikTok (portrait)
```

### Basic Usage
```css
.video-container {
  aspect-ratio: 16 / 9;
  width: 100%;
  background: #000;
}

.video-container iframe,
.video-container video {
  width: 100%;
  height: 100%;
}
```

### Responsive Magic
```css
.card-media {
  aspect-ratio: clamp(3/4, 1/1, 16/9);  /* Portrait → Square → Landscape */
  width: 100%;
  object-fit: cover;
}
```

**HTML:**
```html
<div class="video-container">
  <iframe src="https://youtube.com/embed/VIDEO_ID"></iframe>
</div>
```

**Before `aspect-ratio` (UGLY):**
```html
<!-- Padding hack -->
<div style="padding-bottom: 56.25%;"></div>  ❌
```

**After:** `aspect-ratio: 16/9` ✅

---

## 2. 🧱 Masonry Layout - Pinterest Style

**CSS Masonry** = Auto-arrange cards like Pinterest (unequal heights)!

### Native Masonry (Firefox/Chrome Canary)
```css
.masonry {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
  grid-auto-flow: column;  /* Key! */
  gap: 1.5rem;
  masonry: pack;  /* Firefox only currently */
}
```

### Universal Fallback - CSS Columns
```css
.masonry {
  columns: 12;       /* ~300px columns */
  column-gap: 1.5rem;
  column-fill: auto;
}

.masonry .card {
  break-inside: avoid;
  margin-bottom: 1.5rem;
  background: white;
  border-radius: 12px;
  box-shadow: 0 4px 12px rgba(0,0,0,0.1);
}
```

**Complete Fallback Demo:**
```css
.pinterest {
  /* Modern browsers */
  display: grid !important;
  grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
  gap: 1.5rem;
}

/* Fallback for others */
@supports not (display: grid) {
  .pinterest {
    columns: 250px;
    column-gap: 1.5rem;
  }
  
  .pinterest .card {
    break-inside: avoid;
    margin-bottom: 1.5rem;
  }
}
```

---

## 3. 🥞 `@layer` - Cascade Layers (CSS Priority Control)

**Problem:** CSS specificity wars → `!important` hell  
**Solution:** `@layer` = Organize priority explicitly

### Basic Layers
```css
@layer reset, components, utilities, theme;

@layer reset {
  * { margin: 0; padding: 0; box-sizing: border-box; }
}

@layer components {
  .btn { padding: 12px 24px; }
}

@layer utilities {
  .text-center { text-align: center; }
}

@layer theme {
  :root { --primary: #007bff; }
}
```

**Priority Order:** `reset < components < utilities < theme`

### Real Project Structure
```css
/* style.css */
@import url('reset.css') layer(reset);
@import url('components.css') layer(components);
@import url('utilities.css') layer(utilities);

@layer theme {
  :root { --brand-color: #10b981; }
}
```

**No more specificity fights!** 🎉

---

## 4. 🧮 Custom Properties Functions - Dynamic Math

**Combine CSS vars + math = Responsive everything!**

### Dynamic Spacing System
```css
:root {
  --base-spacing: 1rem;
  --space-xs: calc(var(--base-spacing) * 0.25);
  --space-sm: calc(var(--base-spacing) * 0.5);
  --space-md: var(--base-spacing);
  --space-lg: calc(var(--base-spacing) * 2);
  --space-xl: calc(var(--base-spacing) * 4);
}
```

### Modern Math Functions
```css
:root {
  --container-max: 1200px;
}

/* Responsive container */
.container {
  width: min(100vw - 2rem, var(--container-max));
  margin: 0 auto;
  padding: clamp(1rem, 5vw, 4rem);
}

/* Fluid spacing */
.section-padding {
  padding: 
    min(4rem, 10vw) 
    clamp(2rem, 5vw, 6rem);
}
```

### Dynamic Typography Scale
```css
:root {
  --text-base: clamp(1rem, 2.5vw, 1.125rem);
}

h1 { font-size: clamp(2.5rem, 7vw, 5rem); }
h2 { font-size: clamp(2rem, 5vw, 3.5rem); }
h3 { font-size: clamp(1.5rem, 4vw, 2.5rem); }
```

---

## 5. 🏛️ CSS Architecture Patterns

### A. **BEM** - Block Element Modifier
```
Block          → .card
Element        → .card__title
Modifier       → .card--featured
```

```css
.card {
  padding: 2rem;
}

.card__title {
  font-size: 1.5rem;
  margin-bottom: 1rem;
}

.card__button {
  margin-top: 1rem;
}

.card--featured {
  border-left: 5px solid var(--primary);
  background: var(--bg-secondary);
}

.card--featured .card__title {
  color: var(--primary);
}
```

### B. **ITCSS** - Inverted Triangle CSS
```
1. Settings     → Variables, @import
2. Tools        → Reset, mixins  
3. Generic      → Normalize
4. Elements     → h1, p, a (no classes)
5. Objects      → .grid, .media-object
6. Components   → .card, .btn-group
7. Utilities    → .text-center, .mt-2
```

### C. **Design System Approach**
```css
/* tokens.css */
:root {
  --color-primary-500: #3b82f6;
  --space-4: 1rem;
  --radius-md: 8px;
}

/* components.css */
@layer components {
  .btn {
    padding: var(--space-4) var(--space-6);
    border-radius: var(--radius-md);
  }
  
  .btn--primary {
    background: var(--color-primary-500);
  }
}
```

---

## 🧪 Complete Advanced Demo

```html
<!DOCTYPE html>
<html>
<head>
<style>
@layer reset, base, components, utilities;

/* 1. Reset Layer */
@layer reset {
  * { margin: 0; padding: 0; box-sizing: border-box; }
}

/* 2. Base */
@layer base {
  :root {
    --primary: #10b981;
    --space: 1rem;
  }
  
  body { 
    font-family: system-ui, sans-serif;
    line-height: 1.6;
  }
}

/* 3. Components */
@layer components {
  .masonry {
    columns: 280px;
    column-gap: 1.5rem;
    gap: 1.5rem;
  }
  
  .card {
    break-inside: avoid;
    background: white;
    border-radius: 12px;
    padding: calc(var(--space) * 1.5);
    box-shadow: 0 4px 20px rgba(0,0,0,0.08);
    margin-bottom: 1.5rem;
  }
  
  .video {
    aspect-ratio: 16/9;
    width: 100%;
    background: #000;
    border-radius: 8px;
  }
}

/* 4. Utilities */
@layer utilities {
  .container {
    width: min(100% - 3rem, 1200px);
    margin: 0 auto;
    padding: clamp(2rem, 5vw, 4rem) 0;
  }
}
</style>
</head>
<body>
  <div class="container">
    <h1 style="font-size: clamp(2rem, 6vw, 4rem); margin-bottom: 2rem;">
      Advanced CSS Demo
    </h1>
    
    <div class="masonry">
      <div class="card">
        <h2>Masonry Works!</h2>
        <p>Perfect Pinterest layout.</p>
      </div>
      <div class="card">
        <div class="video"></div>
        <h3>Perfect 16:9 Video</h3>
      </div>
      <!-- Add more cards of different heights -->
    </div>
  </div>
</body>
</html>
```

## 🚀 Pro Summary

```
✅ aspect-ratio = Perfect videos/images
✅ masonry/columns = Pinterest layouts  
✅ @layer = Priority control
✅ calc/min/max = Dynamic math
✅ BEM/ITCSS = Scalable architecture
✅ Design tokens = Consistent systems
```

**These make you a CSS pro!** 🎉

**Build what next?** Full design system or masonry gallery?
```

**Advanced CSS features complete!** Cutting-edge techniques with practical demos for your YouTube series. 🔥
