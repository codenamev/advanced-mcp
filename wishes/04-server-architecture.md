# Slide 4: Core Server Architecture

<div class="slide-header">
  <h1 class="slide-title">
    > CORE SERVER ARCHITECTURE <span class="subtitle-accent">[FOUNDATION]</span>
  </h1>
</div>

<div class="architecture-overview">

## ▶ MCP SDK FOUNDATION

<div class="concept-highlight">
  <strong>Use MCP SDKs (Python, Go, Java) to expose tools with minimal boilerplate</strong>
</div>

```python
# Everything Server Example
from mcp import Server
from mcp.server import stdio_server

server = Server("everything-server")

@server.tool()
async def echo(message: str) -> str:
    """Echo back the input message."""
    return f"Echo: {message}"
```

## ▶ DESIGN PRINCIPLES

<div class="design-grid">

### 🎯 MODULAR DESIGN
One domain per server - focused, composable toolboxes

### 🔄 STATELESS FUNCTIONS
Idempotent tool functions - predictable, reliable operations

### 🚀 TRANSPORT OPTIONS
stdio vs HTTP/SSE - choose based on deployment needs

</div>

## ▶ EVERYTHING SERVER ARCHITECTURE

```ascii
┌─────────────────────────────────────────────────────────────┐
│                  EVERYTHING MCP SERVER                      │
├─────────────────────────────────────────────────────────────┤
│  TOOLS          │  RESOURCES      │  PROMPTS      │ SAMPLING│
│  ├─ echo        │  ├─ static/42   │  ├─ simple    │ ├─ llm  │
│  ├─ add         │  ├─ dynamic     │  ├─ resource  │ └─ comp │
│  ├─ longOp      │  └─ subscribe   │  └─ complex   │         │
│  └─ annotated   │                 │               │         │
├─────────────────────────────────────────────────────────────┤
│         MCP Protocol Layer (stdio/HTTP transport)          │
└─────────────────────────────────────────────────────────────┘
```

</div>

<div class="demo-section">

## 🎮 LIVE DEMO SETUP

<div class="demo-note">
  <strong>DEMONSTRATION:</strong> Everything Server's add & echo tools - minimal schema, fast feedback
</div>

```terminal
$ npx -y @modelcontextprotocol/server-everything
[DEMO] Launch Everything Server
[INSPECT] Examine tool definitions and schemas
[TEST] Call echo and add tools directly
[OBSERVE] Response structure and metadata
```

### Key Observations:
- **Fast feedback loop** - immediate tool response
- **Minimal schema** - clear, focused tool definitions
- **Error handling** - graceful failure modes
- **Metadata structure** - consistent response format

</div>

<div class="slide-footer">
  <span class="demo-ready">🎮 DEMO READY</span>
  <span class="next-indicator">▶ NEXT: Tools - The Heart of MCP</span>
</div>

<div class="cyberpunk-navigation">
  <header class="slide-header">
    <div class="terminal-prompt">
      > ADVANCED MCP PRESENTATION
    </div>
    <div class="slide-counter">
      SLIDE 04/16
    </div>
  </header>

  <footer class="slide-navigation">
    <div class="nav-controls">
      <button class="nav-btn prev-btn" onclick="window.location.href='03-advanced-focus'">
        <span class="btn-glow">◀ PREV</span>
      </button>

      <div class="progress-container">
        <div class="ascii-progress">
          [<span class="progress-bar">████░░░░░░░░░░░░</span>]
          <span class="progress-percent">25%</span>
        </div>
      </div>

      <button class="nav-btn next-btn" onclick="window.location.href='05-tools-heart'">
        <span class="btn-glow">NEXT ▶</span>
      </button>
    </div>
  </footer>
</div>