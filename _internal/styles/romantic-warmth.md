# Romantic Warmth Design Style

A warm, emotional design approach for romance novel platforms. Blends passion, intimacy, and cozy reading experiences through warm colors, soft shapes, elegant typography, and romantic micro-interactions.

## Core Principles

### 1. Warm Color Palette
- **Primary Red**: `#dc2626` (passion, love)
- **Primary Light**: `#ef4444` (softer red)
- **Primary Dark**: `#b91c1c` (deep romance)
- **Secondary Orange**: `#ea580c` (warmth, sunset)
- **Accent**: `#f97316` (vibrant energy)
- **Background**: `#FAF5E9` (warm cream, cozy)
- **Dark Text**: `#1f2937` (readable comfort)

**Color Variations:**
- Deep Rose: `#be123c`
- Coral: `#f43f5e`
- Blush: `#fce7f3`
- Warm Peach: `#fed7aa`
- Soft Pink: `#fbcfe8`

### 2. Soft, Organic Shapes
- **Corner Radius**: Generous rounding (16px-24px) on all elements
- **Blob Shapes**: Organic, heart-inspired forms
- **Curved Lines**: Flowing dividers instead of straight edges
- **Floating Elements**: Hearts, petals, soft circles as decorative accents
- **Layered Depth**: Cards and elements at different elevations

### 3. Romantic Typography
- **Header Font (H1-H2)**: Elegant serif for emotional impact
  - Playfair Display, Cormorant, or Merriweather
- **Body Font (P, H3-H6)**: Clean, highly readable sans-serif
  - Inter, Lato, or Source Sans Pro
- **Accent Font**: Decorative script for special moments
  - Great Vibes, Dancing Script, or Alex Brush
- **Font Weights**: 300-400 for body, 600-700 for headers
- **Letter Spacing**: -1% for headers (warmth), default for body

### 4. Cozy Spacing & Layout
- **Generous Whitespace**: Breathing room for comfortable reading
- **Section Spacing**: 96px-128px between sections
- **Element Spacing**: 24px-32px within components
- **Content Width**: 65-75 characters per line (optimal reading)
- **Padding**: 16px (mobile), 24px (tablet), 32px (desktop)

## Implementation Rules

### Color System
```css
:root {
  /* Primary - Passion */
  --romance-red: #dc2626;
  --romance-red-light: #ef4444;
  --romance-red-dark: #b91c1c;

  /* Secondary - Warmth */
  --romance-orange: #ea580c;
  --romance-orange-light: #f97316;
  --romance-orange-dark: #c2410c;

  /* Accent - Blush */
  --romance-blush: #fce7f3;
  --romance-coral: #f43f5e;
  --romance-rose: #be123c;

  /* Background */
  --romance-cream: #FAF5E9;
  --romance-cream-dark: #f3f4f6;

  /* Text */
  --romance-dark: #1f2937;
  --romance-gray: #4b5563;
  --romance-light: #9ca3af;

  /* Gradients */
  --gradient-romance: linear-gradient(135deg, var(--romance-red), var(--romance-orange));
  --gradient-blush: linear-gradient(135deg, var(--romance-blush), var(--romance-coral));
  --gradient-sunset: linear-gradient(135deg, var(--romance-orange), var(--romance-coral));
}
```

### Typography Scale
```css
/* Font families */
.romantic-header {
  font-family: 'Playfair Display', 'Cormorant', serif;
  font-weight: 600;
  letter-spacing: -0.01em;
  line-height: 1.2;
}

.romantic-body {
  font-family: 'Inter', 'Lato', sans-serif;
  font-weight: 400;
  letter-spacing: 0;
  line-height: 1.6;
}

.romantic-accent {
  font-family: 'Great Vibes', 'Dancing Script', cursive;
  font-weight: 400;
}

/* Type scale (following design rules 1.25 ratio) */
h1 { font-size: 64px; }  /* 2.5rem */
h2 { font-size: 50px; }  /* 2rem */
h3 { font-size: 40px; }  /* 1.5rem */
h4 { font-size: 32px; }  /* 1.25rem */
h5 { font-size: 25px; }  /* 1rem */
h6 { font-size: 20px; }  /* 0.8rem */
p  { font-size: 16px; }  /* base */
```

### Component Styles

#### Romantic Buttons
```css
.romance-btn {
  padding: 14px 28px;
  border-radius: 50px;
  font-weight: 600;
  font-size: 1rem;
  border: none;
  cursor: pointer;
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
  position: relative;
  overflow: hidden;
}

.romance-btn-primary {
  background: var(--gradient-romance);
  color: white;
  box-shadow: 0 4px 15px rgba(220, 38, 38, 0.3);
}

.romance-btn-primary:hover {
  transform: translateY(-2px);
  box-shadow: 0 8px 25px rgba(220, 38, 38, 0.4);
}

.romance-btn-secondary {
  background: var(--romance-blush);
  color: var(--romance-red);
  border: 2px solid var(--romance-red);
}

.romance-btn-ghost {
  background: transparent;
  color: var(--romance-red);
  border: 2px solid var(--romance-red);
}

.romance-btn-ghost:hover {
  background: var(--romance-red);
  color: white;
}
```

#### Soft Cards
```css
.romance-card {
  background: white;
  border-radius: 20px;
  padding: 24px;
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.08);
  border: 1px solid rgba(220, 38, 38, 0.1);
  transition: all 0.3s ease;
  position: relative;
  overflow: hidden;
}

.romance-card::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  height: 4px;
  background: var(--gradient-romance);
  opacity: 0;
  transition: opacity 0.3s ease;
}

.romance-card:hover {
  transform: translateY(-4px);
  box-shadow: 0 12px 40px rgba(0, 0, 0, 0.12);
}

.romance-card:hover::before {
  opacity: 1;
}
```

#### Heart & Floating Elements
```css
/* Floating hearts animation */
.floating-heart {
  position: absolute;
  font-size: 24px;
  color: var(--romance-red);
  opacity: 0;
  animation: float-heart 15s ease-in-out infinite;
  pointer-events: none;
}

@keyframes float-heart {
  0% {
    transform: translateY(100vh) rotate(0deg);
    opacity: 0;
  }
  10% {
    opacity: 0.3;
  }
  90% {
    opacity: 0.3;
  }
  100% {
    transform: translateY(-100vh) rotate(360deg);
    opacity: 0;
  }
}

/* Soft blob shape */
.romance-blob {
  border-radius: 60% 40% 30% 70% / 60% 30% 70% 40%;
  background: var(--gradient-blush);
  animation: blob-morph 8s ease-in-out infinite;
}

@keyframes blob-morph {
  0%, 100% {
    border-radius: 60% 40% 30% 70% / 60% 30% 70% 40%;
  }
  50% {
    border-radius: 30% 60% 70% 40% / 50% 60% 30% 60%;
  }
}
```

#### Curved Dividers
```css
.romance-curve {
  height: 80px;
  background: var(--romance-blush);
  position: relative;
}

.romance-curve::after {
  content: '';
  position: absolute;
  bottom: -40px;
  left: 0;
  width: 100%;
  height: 80px;
  background: inherit;
  border-radius: 50% 50% 0 0;
}
```

### Background Patterns
```css
/* Soft dotted pattern */
.romance-dots {
  background-image: radial-gradient(circle, var(--romance-coral) 15%, transparent 15%);
  background-size: 20px 20px;
  opacity: 0.15;
}

/* Heart pattern */
.romance-hearts {
  background-image: url("data:image/svg+xml,%3Csvg width='60' height='60' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath d='M30 50 C30 50, 10 35, 10 20 C10 10, 20 5, 30 15 C40 5, 50 10, 50 20 C50 35, 30 50, 30 50Z' fill='%23dc2626' fill-opacity='0.08'/%3E%3C/svg%3E");
  background-size: 60px 60px;
}

/* Gradient overlay */
.romance-gradient-overlay {
  background: linear-gradient(135deg,
    rgba(220, 38, 38, 0.05) 0%,
    rgba(234, 88, 12, 0.05) 100%);
}
```

### Micro-interactions
```css
/* Heart pulse on like */
.heart-pulse:active {
  animation: heart-pulse 0.6s ease-in-out;
}

@keyframes heart-pulse {
  0%, 100% { transform: scale(1); }
  25% { transform: scale(1.3); }
  50% { transform: scale(0.9); }
  75% { transform: scale(1.1); }
}

/* Smooth page transitions */
.romance-fade-in {
  animation: fadeIn 0.6s ease-out;
}

@keyframes fadeIn {
  from {
    opacity: 0;
    transform: translateY(20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

/* Reading progress indicator */
.reading-progress {
  height: 4px;
  background: var(--romance-blush);
  position: fixed;
  top: 0;
  left: 0;
  z-index: 100;
}

.reading-progress-bar {
  height: 100%;
  background: var(--gradient-romance);
  transition: width 0.1s ease;
}
```

## Component Guidelines

### Navigation
```html
<nav class="romance-nav">
  <div class="nav-brand">
    <span class="brand-text">NovelRomance</span>
  </div>
  <div class="nav-links">
    <a href="#" class="nav-link">Browse</a>
    <a href="#" class="nav-link">Categories</a>
    <a href="#" class="nav-link">My Library</a>
    <button class="romance-btn romance-btn-primary">Start Reading</button>
  </div>
</nav>
```

### Hero Section
```html
<section class="romance-hero">
  <div class="floating-hearts">
    <span class="floating-heart" style="left: 10%; animation-delay: 0s;">❤️</span>
    <span class="floating-heart" style="left: 30%; animation-delay: 3s;">💕</span>
    <span class="floating-heart" style="left: 70%; animation-delay: 6s;">💗</span>
  </div>
  <div class="hero-content">
    <h1 class="romantic-header">Fall in Love<br><span class="gradient-text">With Every Page</span></h1>
    <p class="romantic-body">Discover heartwarming romance novels that will sweep you off your feet</p>
    <div class="hero-cta">
      <button class="romance-btn romance-btn-primary">Explore Books</button>
      <button class="romance-btn romance-btn-ghost">Write Your Story</button>
    </div>
  </div>
</section>
```

### Book Card
```html
<div class="romance-card book-card">
  <div class="book-cover">
    <img src="cover.jpg" alt="Book Cover">
    <div class="book-overlay">
      <button class="romance-btn romance-btn-primary">Read Now</button>
    </div>
  </div>
  <div class="book-content">
    <span class="book-category">Contemporary Romance</span>
    <h3 class="book-title">When Stars Collide</h3>
    <p class="book-author">by Sarah Johnson</p>
    <div class="book-rating">
      <span class="stars">★★★★★</span>
      <span class="rating-count">(2.4k)</span>
    </div>
  </div>
</div>
```

### Reading Interface
```html
<div class="romance-reader">
  <div class="reading-progress">
    <div class="reading-progress-bar" style="width: 45%;"></div>
  </div>
  <div class="reader-content">
    <div class="chapter-header">
      <span class="chapter-number">Chapter 12</span>
      <h2 class="chapter-title romantic-header">The Promise</h2>
    </div>
    <div class="chapter-text romantic-body">
      <p>The moonlight cast silver shadows across her face as he reached for her hand...</p>
    </div>
  </div>
  <div class="reader-controls">
    <button class="romance-btn romance-btn-ghost">← Previous</button>
    <button class="romance-btn romance-btn-primary">Next →</button>
  </div>
</div>
```

## When to Use Romantic Warmth

### Perfect For:
- Romance novel platforms
- Book reading apps
- Wedding/relationship services
- Lifestyle blogs with emotional content
- Storytelling platforms
- Fan fiction communities
- Romantic fiction publishers

### Avoid When:
- Tech/SaaS products
- Corporate/B2B
- Medical/financial services
- News/informational sites
- Gaming platforms
- Industrial/manufacturing

## Technical Requirements

### Font Imports
```html
<!-- Google Fonts -->
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@600;700&family=Inter:wght@300;400;500;600&family=Great+Vibes&display=swap" rel="stylesheet">
```

### Icon Libraries
- Lucide Icons (clean, romantic-friendly)
- Heroicons (elegant line icons)
- Custom heart/romance SVG icons

### Animation Libraries
- Framer Motion (Vue: @vueuse/motion)
- GSAP (for complex story animations)
- CSS transitions for micro-interactions

### Accessibility
- Color contrast: Minimum 4.5:1 for normal text
- Touch targets: Minimum 44px × 44px
- Respect `prefers-reduced-motion`
- Alt text for all book covers and imagery

Remember: Romantic Warmth is about creating an emotional connection through design. Every element should evoke feelings of love, warmth, and comfort. The key is subtlety - romance should be felt, not shouted.

---

**Palette Reference:**
- Primary: `#dc2626` | `#ef4444` | `#b91c1c`
- Secondary: `#ea580c` | `#f97316` | `#c2410c`
- Accent: `#f43f5e` | `#fce7f3` | `#be123c`
- Background: `#FAF5E9` | `#ffffff`
- Text: `#1f2937` | `#4b5563` | `#9ca3af`
