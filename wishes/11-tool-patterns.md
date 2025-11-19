# Slide 11: Tool Design Patterns

<div class="slide-header">
  <h1 class="slide-title">
    > TOOL DESIGN PATTERNS <span class="subtitle-accent">[BEST PRACTICES]</span>
  </h1>
</div>

<div class="patterns-overview">

## ▶ TOOL CATEGORIZATION STRATEGY

<div class="concept-highlight">
  <strong>Categorize tools by domain: devops, data, creative - with consistent metadata patterns</strong>
</div>

```json
{
  "categories": {
    "devops": ["git_commit", "deploy_service", "run_tests"],
    "data": ["query_database", "transform_csv", "generate_report"],
    "creative": ["generate_image", "write_story", "compose_music"],
    "analysis": ["analyze_code", "find_patterns", "summarize_data"]
  }
}
```

</div>

<div class="structured-metadata">

## ▶ STRUCTURED METADATA PATTERN

<div class="demo-note">
  <strong>DEMONSTRATION:</strong> `annotatedMessage` shows structured metadata (error/success/debug)
</div>

```json
{
  "tool": "annotatedMessage",
  "response": {
    "content": "Operation completed successfully",
    "metadata": {
      "type": "success",
      "severity": "info",
      "timestamp": "2025-11-19T10:30:00Z",
      "duration_ms": 150,
      "resources_used": ["cpu", "memory"],
      "debug_info": {
        "execution_path": "standard",
        "cache_hit": true,
        "validation_passed": true
      }
    }
  }
}
```

### Metadata Categories:
- **SUCCESS**: Operation completed without issues
- **WARNING**: Completed but with concerns
- **ERROR**: Failed operation with error details
- **DEBUG**: Development and troubleshooting information

</div>

<div class="design-patterns">

## ▶ ADVANCED DESIGN PATTERNS

<div class="pattern-grid">

### 🔗 RESOURCE REFERENCES
Tools output resource URIs for large datasets

### 🔄 IDEMPOTENT OPERATIONS
Same input always produces same output

### 📦 DECLARATIVE FRAMEWORKS
Use FastMCP for structure-driven development

</div>

## ▶ RESOURCE REFERENCE PATTERN

```ascii
┌──────────────────────────────────────────────────────────────┐
│                 RESOURCE REFERENCE WORKFLOW                  │
├──────────────────────────────────────────────────────────────┤
│                                                              │
│  1. Tool Execution    2. Large Output     3. Resource Ref   │
│  ┌─────────────┐     ┌─────────────┐     ┌─────────────┐    │
│  │ query_large │────►│ Generate    │────►│ Return URI  │    │
│  │ _dataset    │     │ 10MB result │     │ resource:// │    │
│  └─────────────┘     └─────────────┘     │ /results/42 │    │
│                                          └─────────────┘    │
│                                                 │            │
│                      4. Client Access          ▼            │
│                      ┌─────────────┐     ┌─────────────┐    │
│                      │ Client      │────►│ Fetch       │    │
│                      │ requests    │     │ resource    │    │
│                      │ resource    │     │ content     │    │
│                      └─────────────┘     └─────────────┘    │
│                                                              │
│  Benefits: Efficient memory usage, streaming support        │
└──────────────────────────────────────────────────────────────┘
```

</div>

<div name="fastmcp-framework">

## ▶ FASTMCP DECLARATIVE FRAMEWORK

```python
from fastmcp import FastMCP

# Declarative tool definition
@app.tool()
def analyze_code(
    file_path: str,
    language: str = "auto",
    include_metrics: bool = True
) -> dict:
    """Analyze code quality and complexity metrics."""
    return {
        "complexity": calculate_complexity(file_path),
        "quality_score": assess_quality(file_path),
        "suggestions": generate_suggestions(file_path),
        "metadata": {
            "language": detect_language(file_path),
            "lines_of_code": count_lines(file_path),
            "analysis_version": "2.1.0"
        }
    }
```

### FastMCP Benefits:
- **Type Safety**: Automatic JSON schema generation
- **Documentation**: Self-documenting tool interfaces
- **Validation**: Built-in parameter validation
- **Debugging**: Enhanced error reporting and logging

</div>

<div class="demo-section">

## 🎮 LIVE DEMO: ANNOTATED MESSAGE

```terminal
$ mcp-inspector
> Call annotatedMessage tool with different scenarios

[SUCCESS SCENARIO]
Input: message="Process completed", type="success"
Output: {
  "content": "✅ Process completed successfully",
  "metadata": {
    "type": "success",
    "severity": "info",
    "execution_time": "0.15s",
    "resource_usage": "low"
  }
}

[ERROR SCENARIO]
Input: message="Database connection failed", type="error"
Output: {
  "content": "❌ Database connection failed",
  "metadata": {
    "type": "error",
    "severity": "high",
    "error_code": "DB_CONN_001",
    "troubleshooting": "Check network connectivity"
  }
}
```

### Pattern Applications:
- **Consistent structure** across all tool responses
- **Rich debugging information** for development
- **Standardized error handling** patterns
- **Performance monitoring** data collection

</div>

<div class="slide-footer">
  <span class="demo-ready">🎮 STRUCTURED METADATA DEMO READY</span>
  <span class="next-indicator">▶ NEXT: Security Best Practices</span>
</div>

<div class="cyberpunk-navigation">
  <header class="slide-header">
    <div class="terminal-prompt">
      > ADVANCED MCP PRESENTATION
    </div>
    <div class="slide-counter">
      SLIDE 11/16
    </div>
  </header>

  <footer class="slide-navigation">
    <div class="nav-controls">
      <button class="nav-btn prev-btn" onclick="window.location.href='10-live-demo'">
        <span class="btn-glow">◀ PREV</span>
      </button>

      <div class="progress-container">
        <div class="ascii-progress">
          [<span class="progress-bar">███████████░░░░░</span>]
          <span class="progress-percent">69%</span>
        </div>
      </div>

      <button class="nav-btn next-btn" onclick="window.location.href='12-security-practices'">
        <span class="btn-glow">NEXT ▶</span>
      </button>
    </div>
  </footer>
</div>