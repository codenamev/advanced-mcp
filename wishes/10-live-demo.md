# Slide 10: Live Demo - Everything MCP Server + MCP Inspector

<div class="slide-header">
  <h1 class="slide-title">
    > LIVE DEMO: INSPECTOR + SERVER <span class="subtitle-accent">[HANDS-ON]</span>
  </h1>
</div>

<div class="demo-setup">

## ▶ ZERO-SETUP EXPLORATION PLATFORM

<div class="concept-highlight">
  <strong>Launch with npx, inspect in real-time, safe for live exploration</strong>
</div>

```terminal
$ npx -y @modelcontextprotocol/server-everything
[STARTING] Everything MCP Server v1.0.0
[LOADED] 8 tools, 4 resources, 3 prompts, 2 sampling endpoints
[TRANSPORT] stdio ready for connections
[SAFE] No destructive operations - perfect for demos
```

</div>

<div class="inspector-interface">

## 🎮 MCP INSPECTOR WALKTHROUGH

```ascii
┌──────────────────────────────────────────────────────────────────┐
│                      MCP INSPECTOR INTERFACE                     │
├──────────────────────────────────────────────────────────────────┤
│                                                                  │
│  TABS: [Tools] [Resources] [Prompts] [Sampling] [Connection]     │
│                                                                  │
│  ┌─────────────────────────────────────────────────────────────┐ │
│  │ TOOLS TAB                                                   │ │
│  │ ├── echo               │ Simple echo demonstration          │ │
│  │ ├── add                │ Add two numbers together           │ │
│  │ ├── longRunningOp      │ Async streaming demo               │ │
│  │ ├── annotatedMessage   │ Structured metadata example       │ │
│  │ ├── getTinyImage       │ Generate small images              │ │
│  │ ├── sampleLLM          │ Server-asks-model demonstration    │ │
│  │ ├── printEnv           │ Environment variable display       │ │
│  │ └── complex_tool       │ Multi-parameter advanced tool      │ │
│  └─────────────────────────────────────────────────────────────┘ │
│                                                                  │
│  [EXECUTE] [VIEW SCHEMA] [TEST PARAMETERS] [MONITOR]             │
└──────────────────────────────────────────────────────────────────┘
```

</div>

<div class="demo-checklist">

## ✅ INTERACTIVE DEMONSTRATION CHECKLIST

<div class="demo-section">

### 🔧 TOOLS EXPLORATION
```terminal
[ ] Call `echo` → verify basic functionality
[ ] Call `add(5, 3)` → test parameter validation
[ ] Execute `longRunningOperation(10, 5)` → watch streaming
[ ] Try `annotatedMessage` → examine structured metadata
```

### 📚 RESOURCES INSPECTION
```terminal
[ ] Browse `test://static/resource/42` → observe auto-updates
[ ] Subscribe to resource → watch real-time changes
[ ] Check resource metadata → understand structure
[ ] View resource history → track update timeline
```

### 💬 PROMPTS TESTING
```terminal
[ ] Load `simple_prompt` → basic template example
[ ] Execute `resource_prompt` → dynamic argument injection
[ ] Try `complex_prompt` → multi-modal demonstration
[ ] Modify arguments → see template flexibility
```

### 🤖 SAMPLING DEMOS
```terminal
[ ] Call `sampleLLM` → server-asks-model pattern
[ ] Watch bidirectional AI workflow
[ ] Observe response validation
[ ] Test different prompts → see AI integration
```

</div>

</div>

<div class="live-benefits">

## ▶ REAL-TIME EXPLORATION BENEFITS

<div class="benefits-grid">

### 👁️ VISUAL INSPECTION
See tool schemas, resource structures, prompt templates

### ⚡ IMMEDIATE FEEDBACK
Execute tools and see results instantly

### 🔍 DEBUG CAPABILITIES
Monitor requests, responses, and errors

### 📊 PERFORMANCE MONITORING
Track response times and resource usage

</div>

## ▶ SAFE EXPLORATION

```
✅ No destructive operations
✅ Isolated test environment
✅ Easy reset and restart
✅ Perfect for learning and demos
```

</div>

<div class="demo-notes">

## 📝 KEY DEMONSTRATION POINTS

<div class="demo-note">
**Interactive Elements:**
- Real-time tool execution and results
- Resource subscription and auto-updates
- Template argument modification
- Bidirectional AI sampling workflows
- Error handling and validation
- Performance and monitoring insights
</div>

</div>

<div class="slide-footer">
  <span class="live-indicator">● LIVE DEMO ACTIVE</span>
  <span class="next-indicator">▶ NEXT: Tool Design Patterns</span>
</div>

<div class="cyberpunk-navigation">
  <header class="slide-header">
    <div class="terminal-prompt">
      > ADVANCED MCP PRESENTATION
    </div>
    <div class="slide-counter">
      SLIDE 10/16
    </div>
  </header>

  <footer class="slide-navigation">
    <div class="nav-controls">
      <button class="nav-btn prev-btn" onclick="window.location.href='09-multi-server'">
        <span class="btn-glow">◀ PREV</span>
      </button>

      <div class="progress-container">
        <div class="ascii-progress">
          [<span class="progress-bar">██████████░░░░░░</span>]
          <span class="progress-percent">62%</span>
        </div>
      </div>

      <button class="nav-btn next-btn" onclick="window.location.href='11-tool-patterns'">
        <span class="btn-glow">NEXT ▶</span>
      </button>
    </div>
  </footer>
</div>