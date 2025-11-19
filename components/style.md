# Cyberpunk Style Guidelines

## Color Palette

### Primary Colors
```css
:root {
  /* Dark Backgrounds */
  --cyber-black: #000011;
  --cyber-dark: #0D1117;
  --cyber-darker: #0a0a0a;

  /* Neon Accents */
  --neon-cyan: #00FFFF;
  --neon-green: #00FF41;
  --neon-magenta: #FF00FF;
  --neon-amber: #FFB000;

  /* Text Colors */
  --text-primary: #E6E6E6;
  --text-secondary: #B3B3B3;
  --text-accent: #00FFFF;

  /* Effects */
  --glow-cyan: 0 0 10px #00FFFF, 0 0 20px #00FFFF, 0 0 30px #00FFFF;
  --glow-green: 0 0 10px #00FF41, 0 0 20px #00FF41, 0 0 30px #00FF41;
}
```

## Typography

### Font Families
- **Headers**: `'Courier New', 'Monaco', monospace`
- **Body Text**: `'Monaco', 'Consolas', 'Courier New', monospace`
- **Code Blocks**: `'Fira Code', 'Monaco', 'Consolas', monospace`

### Font Sizes & Hierarchy
```css
.slide-title {
  font-size: 3rem;
  color: var(--neon-cyan);
  text-shadow: var(--glow-cyan);
}

.slide-subtitle {
  font-size: 1.5rem;
  color: var(--neon-green);
}

.slide-content h2 {
  font-size: 2rem;
  color: var(--text-accent);
}

.slide-content p, .slide-content li {
  font-size: 1.2rem;
  color: var(--text-primary);
  line-height: 1.6;
}

.code-block {
  font-family: 'Fira Code', monospace;
  background: var(--cyber-darker);
  border-left: 3px solid var(--neon-green);
  color: var(--neon-green);
}
```

## Layout & Spacing

### Container Styles
```css
.cyberpunk-slide-container {
  background: linear-gradient(135deg, var(--cyber-black) 0%, var(--cyber-dark) 100%);
  min-height: 100vh;
  font-family: 'Monaco', monospace;
  color: var(--text-primary);
  position: relative;
  overflow: hidden;
}

.slide-content {
  padding: 2rem 4rem;
  max-width: 1200px;
  margin: 0 auto;
}
```

## ASCII Art Elements

### Section Dividers
```
╔══════════════════════════════════════════════════════════════════╗
║                        ADVANCED MCP CONCEPTS                     ║
╚══════════════════════════════════════════════════════════════════╝

└── TOOLS ──┐
├── RESOURCES ──┐
├── PROMPTS ──┐
└── SAMPLING ──┘

>>> DEMO TIME <<<

▶ NEXT CONCEPT ▶
```

### Terminal Prompts
```
> BUILDING ADVANCED MCP SERVERS
$ npm install @modelcontextprotocol/server-everything
:: Launching MCP Inspector...
[SUCCESS] Server connected
[INFO] Tools loaded: 8
[DEMO] Ready for live demonstration
```

## Button Styles

### Navigation Buttons
```css
.nav-btn {
  background: var(--cyber-dark);
  border: 2px solid var(--neon-cyan);
  color: var(--neon-cyan);
  padding: 1rem 2rem;
  font-family: 'Monaco', monospace;
  font-weight: bold;
  text-transform: uppercase;
  cursor: pointer;
  position: relative;
  overflow: hidden;
  transition: all 0.3s ease;
}

.nav-btn:hover {
  background: var(--neon-cyan);
  color: var(--cyber-black);
  box-shadow: var(--glow-cyan);
  transform: scale(1.05);
}

.nav-btn::before {
  content: '';
  position: absolute;
  top: 0;
  left: -100%;
  width: 100%;
  height: 100%;
  background: linear-gradient(90deg, transparent, rgba(0,255,255,0.4), transparent);
  transition: left 0.5s;
}

.nav-btn:hover::before {
  left: 100%;
}
```

## Visual Effects

### Scanlines
```css
.scanlines {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: linear-gradient(
    transparent 50%,
    rgba(0, 255, 255, 0.03) 50%
  );
  background-size: 100% 4px;
  pointer-events: none;
  animation: scanline-move 2s linear infinite;
}

@keyframes scanline-move {
  0% { transform: translateY(0); }
  100% { transform: translateY(4px); }
}
```

### Grid Overlay
```css
.grid-overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-image:
    linear-gradient(rgba(0,255,255,0.1) 1px, transparent 1px),
    linear-gradient(90deg, rgba(0,255,255,0.1) 1px, transparent 1px);
  background-size: 20px 20px;
  pointer-events: none;
  opacity: 0.3;
}
```

### Glitch Effect
```css
.glitch {
  position: relative;
  color: var(--text-primary);
  animation: glitch 2s infinite;
}

.glitch::before,
.glitch::after {
  content: attr(data-text);
  position: absolute;
  top: 0;
  left: 0;
}

.glitch::before {
  color: var(--neon-magenta);
  animation: glitch-1 2s infinite;
}

.glitch::after {
  color: var(--neon-cyan);
  animation: glitch-2 2s infinite;
}

@keyframes glitch {
  0%, 100% { transform: translate(0); }
  20% { transform: translate(-2px, 2px); }
  40% { transform: translate(-2px, -2px); }
  60% { transform: translate(2px, 2px); }
  80% { transform: translate(2px, -2px); }
}
```

## Content Styling

### Code Blocks
```css
.code-demo {
  background: var(--cyber-darker);
  border: 1px solid var(--neon-green);
  border-radius: 4px;
  padding: 1.5rem;
  margin: 1rem 0;
  font-family: 'Fira Code', monospace;
  color: var(--neon-green);
  position: relative;
  overflow-x: auto;
}

.code-demo::before {
  content: '> LIVE DEMO';
  position: absolute;
  top: -10px;
  left: 20px;
  background: var(--cyber-black);
  color: var(--neon-cyan);
  padding: 0 10px;
  font-size: 0.8rem;
}
```

### Highlight Boxes
```css
.concept-highlight {
  border: 2px solid var(--neon-amber);
  background: rgba(255, 176, 0, 0.1);
  padding: 1rem;
  margin: 1rem 0;
  border-radius: 4px;
}

.demo-note {
  border-left: 4px solid var(--neon-magenta);
  background: rgba(255, 0, 255, 0.1);
  padding: 1rem;
  margin: 1rem 0;
  font-style: italic;
}
```

## Animation Classes

### Fade In Effects
```css
.fade-in {
  animation: fadeIn 0.8s ease-in;
}

@keyframes fadeIn {
  from { opacity: 0; transform: translateY(20px); }
  to { opacity: 1; transform: translateY(0); }
}

.slide-enter {
  animation: slideEnter 0.6s ease-out;
}

@keyframes slideEnter {
  from { transform: translateX(100px); opacity: 0; }
  to { transform: translateX(0); opacity: 1; }
}
```

## Responsive Breakpoints

```css
/* Mobile */
@media (max-width: 768px) {
  .slide-content { padding: 1rem 2rem; }
  .slide-title { font-size: 2rem; }
  .nav-btn { padding: 0.8rem 1.5rem; }
}

/* Tablet */
@media (max-width: 1024px) {
  .slide-content { padding: 1.5rem 3rem; }
  .slide-title { font-size: 2.5rem; }
}
```