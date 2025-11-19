# Slide 2: What is MCP? (Quick Recap)

<div class="slide-header">
  <h1 class="slide-title">
    > WHAT IS MCP? <span class="subtitle-accent">[QUICK RECAP]</span>
  </h1>
</div>

<div class="concept-grid">

## ▶ OPEN PROTOCOL FOR AI INTEGRATION

<div class="concept-highlight">
  <strong>Open protocol for connecting LLMs to external tools, data, and prompts</strong>
</div>

## ▶ SOLVES THE M + N PROBLEM

```ascii
WITHOUT MCP:           WITH MCP:
┌─────────────┐       ┌─────────────┐
│   LLM A     │◄─────►│   LLM A     │◄──┐
├─────────────┤       ├─────────────┤   │
│   LLM B     │◄──┐   │   LLM B     │◄──┤  MCP
├─────────────┤   │   ├─────────────┤   │ PROTOCOL
│   LLM C     │◄──┼──►│   LLM C     │◄──┤
└─────────────┘   │   └─────────────┘   │
     ▲ ▲ ▲        │                     │
     │ │ │        │   ┌─────────────┐   │
     │ │ └────────┼──►│  TOOL A     │◄──┘
     │ └──────────┼──►│  TOOL B     │◄──┘
     └────────────┴──►│  TOOL C     │◄──┘
                      └─────────────┘

  M×N connections      M+N connections
```

## ▶ SERVER = "TOOLBOX" FOR THE MODEL

<div class="demo-note">
  <strong>DEMO CONCEPT:</strong> Each MCP server acts as a specialized toolbox that models can pick up and use
</div>

</div>

<div class="key-benefits">

### ENABLES MODULAR, SCALABLE INTEGRATION

```terminal
$ mcp-connect --server filesystem --server git --server database
[CONNECTED] 3 servers, 24 tools, 8 resources available
[READY] Claude can now access files, git, and data
```

</div>

<div class="slide-footer">
  <span class="next-indicator">▶ NEXT: Advanced Focus Areas</span>
</div>

<div class="cyberpunk-navigation">
  <header class="slide-header">
    <div class="terminal-prompt">
      > ADVANCED MCP PRESENTATION
    </div>
    <div class="slide-counter">
      SLIDE 02/16
    </div>
  </header>

  <footer class="slide-navigation">
    <div class="nav-controls">
      <button class="nav-btn prev-btn" onclick="window.location.href='01-title'">
        <span class="btn-glow">◀ PREV</span>
      </button>

      <div class="progress-container">
        <div class="ascii-progress">
          [<span class="progress-bar">██░░░░░░░░░░░░░░</span>]
          <span class="progress-percent">12%</span>
        </div>
      </div>

      <button class="nav-btn next-btn" onclick="window.location.href='03-advanced-focus'">
        <span class="btn-glow">NEXT ▶</span>
      </button>
    </div>
  </footer>
</div>