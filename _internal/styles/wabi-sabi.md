# Wabi-Sabi Design Style

Embracing the beauty of imperfection, impermanence, and incompleteness. This design philosophy finds value in the natural, the aged, and the authentic - creating websites that feel human, organic, and comfortably imperfect.

## Core Principles

### 1. Embracing Imperfection
- **Hand-Drawn Elements**: Sketched arrows, circles, boxes with slight wobble
- **Natural Asymmetry**: Intentionally off-center layouts
- **Organic Shapes**: Imperfect circles, wavy lines, free-form blobs
- **Visible "Mistakes"**: Slight overlaps, misalignments (2-5px)
- **Human Touch**: Elements that look crafted by hand

### 2. Texture and Materiality
- **Paper Textures**: Subtle paper grain, watercolor paper texture
- **Natural Materials**: Wood grain, stone texture, fabric weaves
- **Worn Surfaces**: Faded edges, distressed patterns
- **Layered Textures**: Multiple texture overlays for depth
- **Tactile Feel**: Design that invites touch/interaction

### 3. Organic Color Palette
- **Earth Tones**: Browns, tans, creams, grays from nature
- **Muted Colors**: Desaturated versions of bright colors
- **Natural Dyes**: Colors found in plants, clay, minerals
- **Faded Hues**: Slightly washed-out, aged appearance
- **Subtle Gradients**: Imperfect, hand-painted color transitions

### 4. Time and Aging
- **Vintage Photography**: Unpolished, film-like images with grain
- **Aged Effects**: Yellowing paper, faded ink, worn edges
- **Patinina**: Showing the passage of time
- **Weathered Typography**: Distressed fonts, ink bleed
- **Natural Processes**: Rust, decay, growth patterns

## Implementation Rules

### Color System
```css
:root {
  --cream: #F5F2E8;
  --warm-brown: #8B7355;
  --slate-gray: #708090;
  --terracotta: #E2725B;
  --moss-green: #8A9A5B;
  --charcoal: #36454F;
  --aged-white: #FAF8F3;
}

/* Textured overlays */
.paper-texture {
  background-image:
    url("data:image/svg+xml,%3Csvg width='100' height='100' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence baseFrequency='0.9' /%3E%3C/filter%3E%3Crect width='100' height='100' filter='url(%23noise)' opacity='0.04'/%3E%3C/svg%3E"),
    var(--cream);
}
```

### Typography
```css
/* Main text with slight imperfection */
.wabi-sabi-text {
  font-family: 'Georgia', serif;
  letter-spacing: 0.01em; /* Slightly irregular */
  line-height: 1.7; /* Relaxed, breathing room */
}

/* Handwritten accent styles */
.handwritten {
  font-family: 'Caveat', cursive;
  transform: rotate(-1deg); /* Natural tilt */
}

/* Messy underline effect */
.messy-underline {
  position: relative;
  display: inline-block;
}

.messy-underline::after {
  content: '';
  position: absolute;
  bottom: -2px;
  left: -5%;
  width: 110%;
  height: 8px;
  background: url("data:image/svg+xml,%3Csvg width='100' height='8' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath d='M0,4 Q25,0 50,4 T100,4' stroke='%23E2725B' stroke-width='2' fill='none'/%3E%3C/svg%3E") repeat-x;
  background-size: 100px 8px;
}
```

### Hand-Drawn Elements
```css
/* Imperfect circle */
.hand-drawn-circle {
  border: 3px solid var(--warm-brown);
  border-radius: 50% 49% 51% 50% / 50% 49% 51% 50%;
  transform: rotate(1deg);
}

/* Wavy underline */
.wavy-underline {
  text-decoration: none;
  position: relative;
}

.wavy-underline::before {
  content: '';
  position: absolute;
  bottom: 0;
  left: 0;
  width: 100%;
  height: 4px;
  background: url("data:image/svg+xml,%3Csvg width='60' height='4' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath d='M0,2 Q15,6 30,2 T60,2' stroke='%238B7355' fill='none'/%3E%3C/svg%3E") repeat-x;
}

/* Sketched arrow */
.sketched-arrow::after {
  content: '';
  position: absolute;
  width: 40px;
  height: 2px;
  background: var(--charcoal);
  transform: rotate(30deg);
  box-shadow: 20px -10px 0 var(--charcoal);
}
```

### Layout Patterns
- **Asymmetric Grids**: Off-center column alignment
- **Uneven Spacing**: Vary margins and padding (not strict grid)
- **Overlapping Elements**: Slight intentional overlaps
- **Organic Flow**: Content following natural curves
- **White Space**: Generous but irregular spacing

### Photography Guidelines
```css
/* Vintage photo effect */
.vintage-photo {
  filter: sepia(0.3) contrast(0.9) brightness(1.1);
  position: relative;
}

.vintage-photo::before {
  content: '';
  position: absolute;
  inset: 0;
  background:
    radial-gradient(circle at 30% 30%, transparent 50%, rgba(0,0,0,0.1) 100%),
    url("data:image/svg+xml,%3Csvg width='200' height='200' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='grain'%3E%3CfeTurbulence baseFrequency='0.65' numOctaves='3' stitchTiles='stitch'/%3E%3CfeColorMatrix type='matrix' values='1 0 0 0 0 0 1 0 0 0 0 0 1 0 0 0 0 0 0.5 0'/%3E%3C/filter%3E%3Crect width='100' height='100' filter='url(%23grain)' opacity='0.15'/%3E%3C/svg%3E");
  pointer-events: none;
}

/* Taped corners effect */
.taped-corner::before,
.taped-corner::after {
  content: '';
  position: absolute;
  width: 30px;
  height: 30px;
  background: rgba(255,255,255,0.6);
  border: 1px solid rgba(0,0,0,0.1);
}

.taped-corner::before {
  top: -15px;
  left: -15px;
  transform: rotate(45deg);
}

.taped-corner::after {
  bottom: -15px;
  right: -15px;
  transform: rotate(45deg);
}
```

## Component Guidelines

### Navigation
```html
<nav class="wabi-nav">
  <div class="logo">
    <img src="hand-drawn-logo.svg" alt="Logo" class="sketchy">
  </div>
  <div class="nav-links">
    <a href="#" class="handwritten">about</a>
    <a href="#" class="handwritten">work</a>
    <a href="#" class="handwritten">contact</a>
  </div>
</nav>
```

### Hero Section
```html
<section class="hero-wabi">
  <div class="paper-texture">
    <h1 class="handwritten">
      imperfect <span class="messy-underline">beauty</span>
    </h1>
    <p>A celebration of the human touch in digital design</p>
    <div class="hand-drawn-circle cta">
      <span class="sketchy-arrow">→</span>
      explore
    </div>
  </div>
</section>
```

### Card Components
```html
<div class="wabi-card taped-corner">
  <img src="unpolished-photo.jpg" alt="" class="vintage-photo">
  <div class="card-content">
    <h3 class="wabi-sabi-text">Nature's Pattern</h3>
    <p>Finding beauty in decay and aging</p>
  </div>
</div>
```

### Button Styles
```css
.btn-wabi {
  background: var(--aged-white);
  border: 2px solid var(--warm-brown);
  padding: 12px 24px;
  position: relative;
  transition: all 0.3s ease;
}

.btn-wabi:hover {
  background: var(--warm-brown);
  color: var(--aged-white);
  transform: translateY(-2px) rotate(-1deg);
}

/* Ink bleed effect on hover */
.btn-wabi::after {
  content: '';
  position: absolute;
  inset: 0;
  background: radial-gradient(circle at center, transparent 70%, var(--warm-brown) 100%);
  opacity: 0;
  transition: opacity 0.3s ease;
}

.btn-wabi:hover::after {
  opacity: 0.1;
}
```

## When to Use Wabi-Sabi

### Perfect For:
- Artisan/craft websites
- Artists portfolios
- Organic/natural product brands
- Wellness and mindfulness apps
- Vintage/retro businesses
- Personal blogs with authentic voice
- Nonprofit organizations
- Sustainable/eco-friendly brands

### Avoid When:
- Tech/SaaS companies
- Corporate enterprises
- Financial services
- Medical/healthcare platforms
- Government websites
- High-end luxury brands (unless intentionally rustic)

## Technical Implementation

### CSS Filters for Effects
```css
/* Age/fade effect */
.age-effect {
  filter: brightness(0.95) contrast(0.9) sepia(0.1);
}

/* Watercolor effect */
.watercolor {
  filter: contrast(0.8) brightness(1.2);
  mix-blend-mode: multiply;
}

/* Paper texture overlay */
.texture-overlay {
  position: relative;
}

.texture-overlay::before {
  content: '';
  position: absolute;
  inset: 0;
  opacity: 0.05;
  pointer-events: none;
  background-image: url("paper-texture.png");
  mix-blend-mode: multiply;
}
```

### SVG Hand-Drawn Elements
```html
<!-- Hand-drawn arrow -->
<svg width="60" height="30" viewBox="0 0 60 30" class="sketchy-arrow">
  <path d="M5,15 Q30,10 45,15 M45,15 Q40,10 45,15 Q50,20 45,15"
        stroke="#8B7355"
        stroke-width="2"
        fill="none"
        stroke-linecap="round"/>
</svg>

<!-- Imperfect rectangle -->
<svg width="200" height="100" viewBox="0 0 200 100">
  <rect x="5" y="8" width="192" height="85"
        stroke="#708090"
        stroke-width="2"
        fill="none"
        stroke-dasharray="195 95"
        stroke-dashoffset="0"
        rx="2" ry="3"/>
</svg>
```

Remember: Wabi-sabi is not about being messy for messiness sake. It's about embracing the natural imperfections that make things feel human, real, and comfortable - finding beauty in the way things actually are, not in perfect artificiality.