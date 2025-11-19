# Slide 9: Multi-Server Architecture

<div class="slide-header">
  <h1 class="slide-title">
    > MULTI-SERVER ARCHITECTURE <span class="subtitle-accent">[COMPOSITION]</span>
  </h1>
</div>

<div class="multi-server-overview">

## ▶ SPECIALIZED SERVER COMPOSITION

<div class="concept-highlight">
  <strong>Compose specialized servers: Git, Filesystem, Database, etc. - Keep scopes focused</strong>
</div>

```ascii
┌──────────────────────────────────────────────────────────────────┐
│                   MULTI-SERVER ARCHITECTURE                      │
├──────────────────────────────────────────────────────────────────┤
│                                                                  │
│    ┌─────────────┐  ┌─────────────┐  ┌─────────────┐            │
│    │    GIT      │  │ FILESYSTEM  │  │  DATABASE   │            │
│    │   SERVER    │  │   SERVER    │  │   SERVER    │            │
│    ├─────────────┤  ├─────────────┤  ├─────────────┤            │
│    │• git_commit │  │• read_file  │  │• query_data │            │
│    │• git_status │  │• list_dir   │  │• insert_row │            │
│    │• git_diff   │  │• write_file │  │• update_rec │            │
│    └─────────────┘  └─────────────┘  └─────────────┘            │
│           │                │                │                    │
│           └────────────────┼────────────────┘                    │
│                           │                                      │
│                    ┌─────────────┐                               │
│                    │   CLAUDE    │                               │
│                    │    CLIENT   │                               │
│                    ├─────────────┤                               │
│                    │• Orchestrates                               │
│                    │• Combines                                   │
│                    │• Coordinates                                │
│                    └─────────────┘                               │
│                                                                  │
│  Client orchestrates multi-server workflows intelligently       │
└──────────────────────────────────────────────────────────────────┘
```

</div>

<div class="composition-patterns">

## ▶ COMPOSITION PATTERNS

<div class="pattern-grid">

### 🎯 FOCUSED DOMAINS
Each server handles one specific domain

### 🔗 UNIQUE NAMESPACES
Avoid tool/resource name collisions

### 🤝 CLIENT ORCHESTRATION
Let client combine server capabilities

</div>

## ▶ NAMESPACE COLLISION AVOIDANCE

```json
{
  "git-server": {
    "tools": ["git_commit", "git_status", "git_diff"],
    "namespace": "git"
  },
  "fs-server": {
    "tools": ["read_file", "write_file", "list_directory"],
    "namespace": "filesystem"
  },
  "db-server": {
    "tools": ["query_data", "insert_record", "update_record"],
    "namespace": "database"
  }
}
```

</div>

<div class="demo-section">

## 🎮 LIVE DEMO: CONCURRENT CONNECTIONS

<div class="demo-note">
  <strong>DEMONSTRATION:</strong> Claude connects to Everything Server + Git Server + Filesystem Server concurrently
</div>

```terminal
$ claude-desktop
[LOADING] Connecting to configured MCP servers...

[CONNECTED] everything-server
  ├── Tools: echo, add, longRunningOperation, sampleLLM
  ├── Resources: test://static/resource/42, test://dynamic
  └── Prompts: simple_prompt, resource_prompt, complex_prompt

[CONNECTED] git-server
  ├── Tools: git_commit, git_status, git_diff, git_log
  └── Resources: repo://current/status, repo://current/branches

[CONNECTED] filesystem-server
  ├── Tools: read_file, write_file, list_directory, search_files
  └── Resources: file://workspace/, file://config/

[ORCHESTRATION] Client can now combine all server capabilities
[WORKFLOW] Create file → Git commit → Database log → Generate summary
```

### Key Observations:
- **Concurrent connections** - multiple servers active simultaneously
- **Namespace separation** - no tool name conflicts
- **Intelligent orchestration** - client combines capabilities
- **Workflow composition** - complex multi-server operations

</div>

<div class="benefits-grid">

## ▶ ARCHITECTURAL BENEFITS

```
├── SCALABILITY       │ Add servers without modifying existing ones
├── MAINTAINABILITY   │ Each server has focused responsibilities
├── REUSABILITY       │ Servers can be shared across projects
├── FAULT ISOLATION   │ Server failures don't cascade
└── TEAM OWNERSHIP    │ Different teams can own different servers
```

</div>

<div class="slide-footer">
  <span class="demo-ready">🎮 MULTI-SERVER DEMO READY</span>
  <span class="next-indicator">▶ NEXT: Live Demo - Everything Server + Inspector</span>
</div>

<div class="cyberpunk-navigation">
  <header class="slide-header">
    <div class="terminal-prompt">
      > ADVANCED MCP PRESENTATION
    </div>
    <div class="slide-counter">
      SLIDE 09/16
    </div>
  </header>

  <footer class="slide-navigation">
    <div class="nav-controls">
      <button class="nav-btn prev-btn" onclick="window.location.href='08-sampling-model'">
        <span class="btn-glow">◀ PREV</span>
      </button>

      <div class="progress-container">
        <div class="ascii-progress">
          [<span class="progress-bar">█████████░░░░░░░</span>]
          <span class="progress-percent">56%</span>
        </div>
      </div>

      <button class="nav-btn next-btn" onclick="window.location.href='10-live-demo'">
        <span class="btn-glow">NEXT ▶</span>
      </button>
    </div>
  </footer>
</div>