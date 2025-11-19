# Slide 6: Resources - Read-Only Context for Models

<div class="slide-header">
  <h1 class="slide-title">
    > RESOURCES: READ-ONLY CONTEXT <span class="subtitle-accent">[DYNAMIC DATA]</span>
  </h1>
</div>

<div class="resources-overview">

## ▶ URI-BASED STRUCTURED CONTENT

<div class="concept-highlight">
  <strong>Provide structured content on demand - great for large data and real-time updates</strong>
</div>

```json
{
  "uri": "test://static/resource/42",
  "name": "Static Test Resource",
  "description": "A test resource that updates every 5 seconds",
  "mimeType": "application/json"
}
```

## ▶ RESOURCE PATTERNS

<div class="pattern-grid">

### 📊 LARGE DATA SETS
File contents, search results, database queries

### 🔄 AUTO-UPDATING
Real-time data feeds, monitoring dashboards

### 🔗 SUBSCRIPTIONS
Push notifications when resources change

</div>

## ▶ AUTO-UPDATE ARCHITECTURE

```ascii
┌────────────────────────────────────────────────────────────────┐
│              AUTO-UPDATING RESOURCE SYSTEM                    │
├────────────────────────────────────────────────────────────────┤
│                                                                │
│  ┌─────────────┐    5s Timer    ┌─────────────┐               │
│  │  RESOURCE   │◄──────────────►│   UPDATE    │               │
│  │ test://42   │                │  GENERATOR  │               │
│  └─────────────┘                └─────────────┘               │
│         │                               │                     │
│         ▼                               ▼                     │
│  ┌─────────────┐                ┌─────────────┐               │
│  │ SUBSCRIBERS │                │  NEW DATA   │               │
│  │   NOTIFIED  │◄───────────────┤  TIMESTAMP  │               │
│  └─────────────┘                └─────────────┘               │
│                                                                │
│  Inspector, Claude, and other clients get live updates        │
└────────────────────────────────────────────────────────────────┘
```

</div>

<div class="demo-section">

## 🎮 LIVE DEMO: AUTO-UPDATING RESOURCES

<div class="demo-note">
  <strong>DEMONSTRATION:</strong> `test://static/resource/42` in Everything Server - auto-updates every 5 seconds
</div>

```terminal
$ mcp-inspector
> Navigate to Resources tab
> Subscribe to test://static/resource/42

[T+00s] {"id": 42, "timestamp": "2025-11-19T10:00:00Z", "value": 1}
[T+05s] {"id": 42, "timestamp": "2025-11-19T10:00:05Z", "value": 2}
[T+10s] {"id": 42, "timestamp": "2025-11-19T10:00:10Z", "value": 3}
[T+15s] {"id": 42, "timestamp": "2025-11-19T10:00:15Z", "value": 4}

[NOTIFICATION] Resource updated - new data available
[SUBSCRIPTION] Real-time updates flowing to all subscribers
```

### Key Observations:
- **Automatic updates** - no polling required
- **Subscription model** - efficient resource management
- **Version tracking** - timestamp-based change detection
- **Multiple consumers** - Inspector + Claude both receive updates

</div>

<div class="use-cases">

## ▶ COMMON USE CASES

```
├── File System Contents    │ Directory listings, file metadata
├── Database Query Results  │ Live data feeds, cached queries
├── API Response Caching    │ External service data
├── Search Indexes         │ Document collections, embeddings
└── Monitoring Dashboards   │ System metrics, health checks
```

</div>

<div class="slide-footer">
  <span class="demo-ready">🎮 LIVE UPDATE DEMO READY</span>
  <span class="next-indicator">▶ NEXT: Prompt Templates</span>
</div>

<div class="cyberpunk-navigation">
  <header class="slide-header">
    <div class="terminal-prompt">
      > ADVANCED MCP PRESENTATION
    </div>
    <div class="slide-counter">
      SLIDE 06/16
    </div>
  </header>

  <footer class="slide-navigation">
    <div class="nav-controls">
      <button class="nav-btn prev-btn" onclick="window.location.href='05-tools-heart'">
        <span class="btn-glow">◀ PREV</span>
      </button>

      <div class="progress-container">
        <div class="ascii-progress">
          [<span class="progress-bar">██████░░░░░░░░░░</span>]
          <span class="progress-percent">37%</span>
        </div>
      </div>

      <button class="nav-btn next-btn" onclick="window.location.href='07-prompt-templates'">
        <span class="btn-glow">NEXT ▶</span>
      </button>
    </div>
  </footer>
</div>