# Slide 5: Tools - The Heart of an MCP Server

<div class="slide-header">
  <h1 class="slide-title">
    > TOOLS: THE HEART OF MCP <span class="subtitle-accent">[CORE PRIMITIVE]</span>
  </h1>
</div>

<div class="tools-overview">

## ▶ TOOL DEFINITION STRUCTURE

<div class="concept-highlight">
  <strong>Define name, title, description, and JSON schema for intelligent LLM selection</strong>
</div>

```json
{
  "name": "longRunningOperation",
  "title": "Long Running Operation Demo",
  "description": "Demonstrates async streaming with progress notifications",
  "inputSchema": {
    "type": "object",
    "properties": {
      "duration": {"type": "number", "description": "Operation duration in seconds"},
      "steps": {"type": "number", "description": "Number of progress steps"}
    },
    "required": ["duration"]
  }
}
```

## ▶ DESIGN PATTERNS

<div class="pattern-grid">

### 🎯 FINE-GRAINED OVER MONOLITHS
Prefer focused, single-purpose tools

### 📝 DESCRIPTIVE METADATA
Help LLMs choose tools intelligently

### ⚡ ASYNC CAPABILITIES
Stream progress, handle long operations

</div>

## ▶ ASYNC STREAMING ARCHITECTURE

```ascii
┌──────────────────────────────────────────────────────────────┐
│                LONGRUNNINGOPERATION TOOL                     │
├──────────────────────────────────────────────────────────────┤
│  REQUEST          STREAM UPDATES           COMPLETION        │
│     │                    │                      │            │
│     ▼                    ▼                      ▼            │
│  ┌─────┐            ┌─────────┐            ┌─────────┐       │
│  │START│────────────►│PROGRESS │────────────►│ RESULT  │       │
│  └─────┘            │NOTIFS   │            └─────────┘       │
│                     └─────────┘                              │
│                          │                                   │
│                     Real-time updates                        │
│                     to client/inspector                      │
└──────────────────────────────────────────────────────────────┘
```

</div>

<div class="demo-section">

## 🎮 LIVE DEMO: LONGRUNNINGOPERATION

<div class="demo-note">
  <strong>DEMONSTRATION:</strong> Everything Server's `longRunningOperation` tool - async streaming + notifications
</div>

```terminal
$ mcp-inspector
> Call longRunningOperation(duration: 10, steps: 5)

[STREAM] Starting operation...
[PROGRESS] Step 1/5 (20%) - Processing data chunk 1
[PROGRESS] Step 2/5 (40%) - Processing data chunk 2
[PROGRESS] Step 3/5 (60%) - Processing data chunk 3
[PROGRESS] Step 4/5 (80%) - Processing data chunk 4
[PROGRESS] Step 5/5 (100%) - Operation complete
[RESULT] Final result with full metadata
```

### Key Observations:
- **Real-time progress** - streaming notifications
- **Cancellation support** - can interrupt long operations
- **Error recovery** - graceful handling of failures
- **Resource management** - proper cleanup on completion

</div>

<div class="tool-benefits">

## ▶ INTELLIGENT TOOL SELECTION

```
LLM Decision Process:
├── Read tool descriptions
├── Match to user intent
├── Validate required parameters
└── Execute with confidence
```

</div>

<div class="slide-footer">
  <span class="demo-ready">🎮 ASYNC DEMO READY</span>
  <span class="next-indicator">▶ NEXT: Resources - Read-Only Context</span>
</div>

<div class="cyberpunk-navigation">
  <header class="slide-header">
    <div class="terminal-prompt">
      > ADVANCED MCP PRESENTATION
    </div>
    <div class="slide-counter">
      SLIDE 05/16
    </div>
  </header>

  <footer class="slide-navigation">
    <div class="nav-controls">
      <button class="nav-btn prev-btn" onclick="window.location.href='04-server-architecture'">
        <span class="btn-glow">◀ PREV</span>
      </button>

      <div class="progress-container">
        <div class="ascii-progress">
          [<span class="progress-bar">█████░░░░░░░░░░░</span>]
          <span class="progress-percent">31%</span>
        </div>
      </div>

      <button class="nav-btn next-btn" onclick="window.location.href='06-resources-context'">
        <span class="btn-glow">NEXT ▶</span>
      </button>
    </div>
  </footer>
</div>