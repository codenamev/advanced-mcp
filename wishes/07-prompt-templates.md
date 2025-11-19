# Slide 7: Prompt Templates

<div class="slide-header">
  <h1 class="slide-title">
    > PROMPT TEMPLATES <span class="subtitle-accent">[REUSABLE CONVERSATIONS]</span>
  </h1>
</div>

<div class="prompts-overview">

## ▶ STRUCTURED CONVERSATION PATTERNS

<div class="concept-highlight">
  <strong>Reusable structured conversations that separate prompt content from tool logic</strong>
</div>

```json
{
  "name": "resource_prompt",
  "description": "Analyze resource content with dynamic arguments",
  "arguments": [
    {
      "name": "resource_uri",
      "description": "URI of the resource to analyze",
      "required": true
    }
  ]
}
```

## ▶ DYNAMIC ARGUMENT SYSTEM

<div class="pattern-grid">

### 🔗 RESOURCE INTEGRATION
Load resources dynamically into prompts

### 🎯 PARAMETERIZED TEMPLATES
Customize prompts with runtime arguments

### 💾 EXTERNAL STORAGE
Store in config files or external systems

</div>

## ▶ PROMPT TEMPLATE ARCHITECTURE

```ascii
┌──────────────────────────────────────────────────────────────┐
│                   PROMPT TEMPLATE SYSTEM                    │
├──────────────────────────────────────────────────────────────┤
│                                                              │
│  ┌─────────────┐    Arguments    ┌─────────────┐            │
│  │  TEMPLATE   │◄───────────────►│ DYNAMIC     │            │
│  │ resource_   │                 │ RESOURCE    │            │
│  │ prompt      │                 │ LOADER      │            │
│  └─────────────┘                 └─────────────┘            │
│         │                               │                   │
│         ▼                               ▼                   │
│  ┌─────────────┐                ┌─────────────┐            │
│  │ RENDERED    │◄───────────────┤ RESOURCE    │            │
│  │ CONVERSATION│                │ CONTENT     │            │
│  └─────────────┘                └─────────────┘            │
│                                                              │
│  Final prompt sent to model with injected resource data     │
└──────────────────────────────────────────────────────────────┘
```

</div>

<div class="demo-section">

## 🎮 LIVE DEMO: RESOURCE_PROMPT TEMPLATE

<div class="demo-note">
  <strong>DEMONSTRATION:</strong> `resource_prompt` uses dynamic argument to load a resource
</div>

```terminal
$ mcp-inspector
> Navigate to Prompts tab
> Select "resource_prompt" template
> Set resource_uri: "test://static/resource/42"

[TEMPLATE] Loading resource_prompt template
[ARGUMENT] resource_uri = "test://static/resource/42"
[LOADING] Fetching resource content...
[INJECTED] Resource data merged into prompt template

Generated Conversation:
┌─────────────────────────────────────────────┐
│ System: Analyze the following resource data │
│                                             │
│ Resource URI: test://static/resource/42     │
│ Content: {"id": 42, "timestamp": "...", ... │
│                                             │
│ User: Please summarize the key information  │
│ and identify any patterns or anomalies.     │
└─────────────────────────────────────────────┘
```

### Key Observations:
- **Dynamic content injection** - resource loaded at runtime
- **Template reusability** - same template, different resources
- **Argument validation** - required parameters enforced
- **Content flexibility** - works with any resource type

</div>

<div class="template-benefits">

## ▶ SEPARATION OF CONCERNS

```
├── PROMPT LOGIC     │ Template structure and flow
├── CONTENT SOURCE   │ Dynamic resource loading
├── PARAMETERIZATION │ Runtime argument injection
└── REUSABILITY      │ Multiple contexts, same template
```

## ▶ STORAGE OPTIONS

<div class="storage-grid">

### 📁 CONFIG FILES
JSON/YAML template definitions

### 🗃️ EXTERNAL SYSTEMS
Database or CMS-managed templates

### 🔄 VERSION CONTROL
Git-tracked template evolution

</div>

</div>

<div class="slide-footer">
  <span class="demo-ready">🎮 DYNAMIC PROMPT DEMO READY</span>
  <span class="next-indicator">▶ NEXT: Sampling - Server-Asks-Model</span>
</div>

<div class="cyberpunk-navigation">
  <header class="slide-header">
    <div class="terminal-prompt">
      > ADVANCED MCP PRESENTATION
    </div>
    <div class="slide-counter">
      SLIDE 07/16
    </div>
  </header>

  <footer class="slide-navigation">
    <div class="nav-controls">
      <button class="nav-btn prev-btn" onclick="window.location.href='06-resources-context'">
        <span class="btn-glow">◀ PREV</span>
      </button>

      <div class="progress-container">
        <div class="ascii-progress">
          [<span class="progress-bar">███████░░░░░░░░░</span>]
          <span class="progress-percent">44%</span>
        </div>
      </div>

      <button class="nav-btn next-btn" onclick="window.location.href='08-sampling-model'">
        <span class="btn-glow">NEXT ▶</span>
      </button>
    </div>
  </footer>
</div>