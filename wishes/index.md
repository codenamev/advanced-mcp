# Advanced MCP Presentation - Cyberpunk Style

<div class="cyberpunk-slide-container">
  <header class="slide-header">
    <div class="terminal-prompt">
      > ADVANCED MCP PRESENTATION SYSTEM
    </div>
    <div class="slide-counter">
      INITIALIZING...
    </div>
  </header>

  <main class="slide-content">

## 🚀 WELCOME TO THE ADVANCED MCP PRESENTATION

```ascii
╔══════════════════════════════════════════════════════════════════╗
║                                                                  ║
║    ██████   ██████  ██    ██  █████  ███    ██  ██████ ███████   ║
║   ██   ██  ██   ██  ██    ██ ██   ██ ████   ██ ██      ██        ║
║   ███████  ██   ██  ██    ██ ███████ ██ ██  ██ ██      █████     ║
║   ██   ██  ██   ██   ██  ██  ██   ██ ██  ██ ██ ██      ██        ║
║   ██   ██  ██████     ████   ██   ██ ██   ████  ██████ ███████   ║
║                                                                  ║
║                        ███    ███  ██████ ██████                 ║
║                        ████  ████ ██      ██   ██                ║
║                        ██ ████ ██ ██      ██████                 ║
║                        ██  ██  ██ ██      ██                     ║
║                        ██      ██  ██████ ██                     ║
║                                                                  ║
╚══════════════════════════════════════════════════════════════════╝
```

### 📋 PRESENTATION NAVIGATION

<div class="slide-grid">

**Introduction Section:**
- [Slide 1: Title Slide](01-title)
- [Slide 2: MCP Recap](02-mcp-recap)
- [Slide 3: Advanced Focus](03-advanced-focus)

**Core Architecture Section:**
- [Slide 4: Server Architecture](04-server-architecture)
- [Slide 5: Tools - The Heart](05-tools-heart)
- [Slide 6: Resources - Context](06-resources-context)
- [Slide 7: Prompt Templates](07-prompt-templates)
- [Slide 8: Sampling Model](08-sampling-model)

**Advanced Patterns Section:**
- [Slide 9: Multi-Server Architecture](09-multi-server)
- [Slide 10: Live Demo](10-live-demo)
- [Slide 11: Tool Design Patterns](11-tool-patterns)
- [Slide 12: Security Practices](12-security-practices)
- [Slide 13: Deployment & Performance](13-deployment-performance)

**Workflows & Conclusion Section:**
- [Slide 14: Advanced Workflows](14-workflow-examples)
- [Slide 15: Recap & Takeaways](15-recap-takeaways)
- [Slide 16: Resources & Questions](16-resources-questions)

</div>

### 🎮 LIVE DEMO PREPARATION

<div class="demo-setup-section">

#### Required Setup Commands:
```terminal
$ npx -y @modelcontextprotocol/server-everything
$ npx -y @modelcontextprotocol/inspector
```

#### Demo Status:
- ✅ Everything MCP Server (Ready for launch)
- ✅ MCP Inspector (Ready for real-time exploration)
- ✅ Multi-server examples (Git + FS + DB)
- ✅ Security demonstrations (printEnv analysis)
- ✅ Performance monitoring (listRoots scoping)

</div>

### 🎯 PRESENTATION FEATURES

<div class="features-grid">

#### 🎨 Cyberpunk Aesthetic
- Classic matrix-style visuals
- Neon color schemes and glow effects
- Terminal-inspired navigation
- ASCII art and retro-futuristic design

#### 🔧 Technical Content
- All 4 MCP primitives covered
- Live demonstrations throughout
- Architecture diagrams and patterns
- Production-ready security and scaling

#### ⏱️ 30-Minute Format
- Focused on demos and architecture
- Minimal text, maximum visual impact
- Interactive exploration opportunities
- Q&A preparation included

</div>

  </main>

  <footer class="slide-navigation">
    <div class="nav-controls">
      <button class="nav-btn start-btn" onclick="window.location.href='01-title'">
        <span class="btn-glow">START PRESENTATION ▶</span>
      </button>
    </div>
  </footer>

  <div class="scanlines"></div>
  <div class="grid-overlay"></div>
</div>

<style>
/* Apply cyberpunk styling directly */
body {
  background: linear-gradient(135deg, #000011 0%, #0D1117 100%);
  color: #E6E6E6;
  font-family: 'Monaco', 'Consolas', 'Courier New', monospace;
  margin: 0;
  padding: 0;
  min-height: 100vh;
}

.cyberpunk-slide-container {
  min-height: 100vh;
  position: relative;
  overflow: hidden;
}

.slide-header {
  padding: 1rem 2rem;
  border-bottom: 2px solid #00FFFF;
  display: flex;
  justify-content: space-between;
  align-items: center;
  background: rgba(0, 255, 255, 0.1);
}

.terminal-prompt {
  color: #00FFFF;
  font-weight: bold;
  text-shadow: 0 0 10px #00FFFF;
}

.slide-content {
  padding: 2rem 4rem;
  max-width: 1200px;
  margin: 0 auto;
}

.slide-content h1 {
  color: #00FFFF;
  text-shadow: 0 0 10px #00FFFF;
  font-size: 2.5rem;
  margin-bottom: 2rem;
}

.slide-content h2 {
  color: #00FF41;
  font-size: 1.5rem;
  margin: 1.5rem 0;
}

.slide-content h3, .slide-content h4 {
  color: #FFB000;
  margin: 1rem 0;
}

.slide-grid, .features-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 1rem;
  margin: 1rem 0;
}

.slide-grid a {
  color: #00FFFF;
  text-decoration: none;
  padding: 0.5rem;
  border: 1px solid #00FFFF;
  border-radius: 4px;
  display: block;
  transition: all 0.3s ease;
}

.slide-grid a:hover {
  background: rgba(0, 255, 255, 0.1);
  box-shadow: 0 0 10px #00FFFF;
}

.demo-setup-section, .features-grid div {
  border: 1px solid #00FF41;
  padding: 1rem;
  border-radius: 4px;
  background: rgba(0, 255, 65, 0.1);
  margin: 1rem 0;
}

.nav-btn {
  background: #0D1117;
  border: 2px solid #00FFFF;
  color: #00FFFF;
  padding: 1rem 2rem;
  font-family: 'Monaco', monospace;
  font-weight: bold;
  text-transform: uppercase;
  cursor: pointer;
  transition: all 0.3s ease;
  border-radius: 4px;
}

.nav-btn:hover {
  background: #00FFFF;
  color: #000011;
  box-shadow: 0 0 20px #00FFFF;
  transform: scale(1.05);
}

.slide-navigation {
  text-align: center;
  padding: 2rem;
}

.scanlines {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: linear-gradient(transparent 50%, rgba(0, 255, 255, 0.03) 50%);
  background-size: 100% 4px;
  pointer-events: none;
  animation: scanline-move 2s linear infinite;
}

@keyframes scanline-move {
  0% { transform: translateY(0); }
  100% { transform: translateY(4px); }
}

.grid-overlay {
  position: fixed;
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

code, pre {
  background: #0a0a0a;
  border: 1px solid #00FF41;
  color: #00FF41;
  padding: 0.5rem;
  border-radius: 4px;
  font-family: 'Monaco', monospace;
}

pre {
  padding: 1rem;
  overflow-x: auto;
}
</style>