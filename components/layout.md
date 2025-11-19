# Cyberpunk Slide Deck Layout

## Main Container Structure

```html
<div class="cyberpunk-slide-container">
  <header class="slide-header">
    <div class="terminal-prompt">
      > ADVANCED MCP PRESENTATION
    </div>
    <div class="slide-counter">
      SLIDE <span id="current-slide">01</span>/16
    </div>
  </header>

  <main class="slide-content">
    <!-- Slide content goes here -->
  </main>

  <footer class="slide-navigation">
    <div class="nav-controls">
      <button class="nav-btn prev-btn" id="prev-slide">
        <span class="btn-glow">◀ PREV</span>
      </button>

      <div class="progress-container">
        <div class="ascii-progress">
          [<span id="progress-bar">████████░░░░░░░░</span>]
          <span id="progress-percent">50%</span>
        </div>
      </div>

      <button class="nav-btn next-btn" id="next-slide">
        <span class="btn-glow">NEXT ▶</span>
      </button>
    </div>
  </footer>

  <!-- Cyberpunk effects overlay -->
  <div class="scanlines"></div>
  <div class="grid-overlay"></div>
</div>
```

## Navigation Behavior

- Forward/backward buttons with neon glow effects
- Slide counter updates dynamically
- ASCII progress bar shows completion percentage
- Keyboard navigation support (arrow keys, space, etc.)
- Smooth transitions with cyberpunk effects

## Layout Sections

### Header
- Terminal-style prompt showing presentation title
- Slide counter in the format "SLIDE XX/16"
- Neon cyan accent color

### Main Content Area
- Full-height content area for slide content
- Dark background with subtle texture
- Responsive layout for different screen sizes

### Footer Navigation
- Left: Previous slide button
- Center: ASCII-style progress indicator
- Right: Next slide button
- All buttons have neon glow hover effects

## Responsive Design

- Mobile-friendly navigation
- Scalable typography
- Touch-friendly button sizes
- Maintains cyberpunk aesthetic across devices

## Interactive Elements

```javascript
// Navigation functionality
function navigateSlide(direction) {
  // Update slide counter
  // Update progress bar
  // Apply transition effects
  // Update URL if applicable
}

// Keyboard shortcuts
document.addEventListener('keydown', function(e) {
  switch(e.key) {
    case 'ArrowRight':
    case ' ':
      navigateSlide('next');
      break;
    case 'ArrowLeft':
      navigateSlide('prev');
      break;
  }
});
```

## Visual Effects

### Scanlines
- Subtle horizontal scanlines across the entire slide
- CSS animation for continuous movement
- Low opacity to not interfere with content

### Grid Overlay
- Subtle grid pattern in the background
- Matrix-inspired visual element
- Very low opacity accent

### Button Glow
- Neon glow effect on hover
- Pulsing animation for active states
- Color transitions matching cyberpunk theme