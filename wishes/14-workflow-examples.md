# Slide 14: Advanced Workflow Examples

<div class="slide-header">
  <h1 class="slide-title">
    > ADVANCED WORKFLOW EXAMPLES <span class="subtitle-accent">[END-TO-END]</span>
  </h1>
</div>

<div class="workflow-overview">

## ▶ COMPLETE AI WORKFLOW PATTERNS

<div class="concept-highlight">
  <strong>Claude: resource → prompt → sampling → action - combining all four MCP primitives</strong>
</div>

```ascii
┌──────────────────────────────────────────────────────────────────┐
│                    COMPLETE WORKFLOW CHAIN                      │
├──────────────────────────────────────────────────────────────────┤
│                                                                  │
│  1. RESOURCE      2. PROMPT       3. SAMPLING     4. ACTION      │
│  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐ ┌───────────┐ │
│  │ Load data   │─►│ Template    │─►│ AI analysis │►│ Execute   │ │
│  │ from URI    │  │ with args   │  │ & decision  │ │ tool call │ │
│  └─────────────┘  └─────────────┘  └─────────────┘ └───────────┘ │
│                                                                  │
│  Claude orchestrates the entire chain intelligently             │
└──────────────────────────────────────────────────────────────────┘
```

</div>

<div class="demo-workflows">

## 🎮 LIVE DEMO WORKFLOWS

### 📊 WORKFLOW 1: AI DATA ANALYSIS

<div class="demo-note">
  <strong>DEMONSTRATION:</strong> Use `sampleLLM` to write markdown summary from resource
</div>

```terminal
$ mcp-inspector
> Multi-step workflow demonstration

STEP 1: Load Resource
> Browse to test://static/resource/42
> Data: {"metrics": [...], "timestamp": "2025-11-19T10:45:00Z"}

STEP 2: Apply Prompt Template
> Select resource_prompt template
> Set resource_uri: "test://static/resource/42"
> Generate analysis prompt

STEP 3: AI Sampling
> Call sampleLLM with generated prompt
> AI analyzes resource data
> Produces structured markdown summary

STEP 4: Action (Optional)
> Save summary as new resource
> Trigger notification workflow
> Update dashboard display

[RESULT] Complete AI-driven data analysis pipeline
```

### 🎨 WORKFLOW 2: MULTI-MODAL CREATION

<div class="demo-note">
  <strong>DEMONSTRATION:</strong> Combine `complex_prompt` + `getTinyImage` to mix modalities
</div>

```terminal
STEP 1: Complex Prompt Generation
> Execute complex_prompt with creative parameters
> Generate detailed image description

STEP 2: Image Generation
> Call getTinyImage with AI-generated description
> Create visual content based on prompt

STEP 3: Multi-Modal Output
> Combine text analysis + generated image
> Create rich content presentation

[RESULT] AI-generated content with both text and visuals
```

</div>

<div class="real-world-examples">

## ▶ PRODUCTION WORKFLOW PATTERNS

### 🔄 AUTOMATED CODE REVIEW

```python
# Multi-server workflow example
async def automated_code_review_workflow():
    # 1. Resource: Get changed files from Git
    changed_files = await git_server.call_tool("git_diff", {"format": "unified"})

    # 2. Prompt: Apply code review template
    review_prompt = await prompt_server.get_prompt(
        "code_review_template",
        {"diff_content": changed_files, "language": "python"}
    )

    # 3. Sampling: AI analyzes code quality
    ai_review = await sampling_server.call_tool(
        "sampleLLM",
        {"prompt": review_prompt}
    )

    # 4. Action: Post review comments
    await git_server.call_tool(
        "post_review_comment",
        {"content": ai_review, "pr_id": pr_id}
    )
```

### 📈 REAL-TIME MONITORING PIPELINE

```yaml
workflow_name: "performance_monitoring"
triggers:
  - schedule: "*/5 minutes"
  - webhook: "/alerts/performance"

steps:
  1. resource_collection:
     - server: monitoring_server
     - tool: collect_metrics
     - output: metrics_resource_uri

  2. analysis_prompt:
     - server: prompt_server
     - template: performance_analysis
     - args: {resource_uri: "${step1.metrics_resource_uri}"}

  3. ai_assessment:
     - server: ai_server
     - tool: sampleLLM
     - input: "${step2.rendered_prompt}"

  4. alert_action:
     - server: notification_server
     - tool: send_alert
     - condition: "${step3.severity} > 'warning'"
```

</div>

<div class="live-subscription-demo">

## 🎮 LIVE DEMO: SUBSCRIPTION WORKFLOWS

<div class="demo-note">
  <strong>DEMONSTRATION:</strong> Subscribed resource auto-refresh visible in Inspector
</div>

```terminal
$ mcp-inspector
> Navigate to Resources tab
> Subscribe to test://static/resource/42
> Watch real-time updates trigger workflow chains

[T+00s] Resource updated → Trigger analysis workflow
[T+00s] AI processes new data → Generate insights
[T+01s] Workflow completes → Update dashboard
[T+05s] Resource updated → Repeat cycle

[AUTOMATION] Fully automated reactive workflows
[EFFICIENCY] Only processes when data changes
[SCALABILITY] Multiple subscribers, single source
```

### Subscription Benefits:
- **Event-Driven**: Only executes when data changes
- **Resource Efficient**: No polling overhead
- **Real-Time Response**: Immediate workflow triggers
- **Parallel Processing**: Multiple workflows can subscribe

</div>

<div class="enterprise-patterns">

## ▶ ENTERPRISE INTEGRATION PATTERNS

<div class="integration-grid">

### 🔗 API GATEWAY INTEGRATION
MCP servers behind enterprise API management

### 📊 WORKFLOW ORCHESTRATION
Integration with tools like Airflow, Temporal

### 🔐 IDENTITY FEDERATION
SSO integration with corporate identity providers

### 📈 BUSINESS INTELLIGENCE
AI workflows feeding into BI dashboards

</div>

## ▶ OBSERVABILITY IN WORKFLOWS

```
├── Distributed Tracing    │ Follow requests across multiple servers
├── Workflow Metrics       │ Success rates, execution times, bottlenecks
├── Business Metrics       │ ROI, productivity gains, quality improvements
├── Error Analysis         │ Failure modes, recovery patterns, prevention
└── Performance Tuning     │ Optimization opportunities, resource usage
```

</div>

<div class="slide-footer">
  <span class="live-indicator">● MULTI-MODAL DEMOS ACTIVE</span>
  <span class="next-indicator">▶ NEXT: Key Takeaways</span>
</div>

<div class="cyberpunk-navigation">
  <header class="slide-header">
    <div class="terminal-prompt">
      > ADVANCED MCP PRESENTATION
    </div>
    <div class="slide-counter">
      SLIDE 14/16
    </div>
  </header>

  <footer class="slide-navigation">
    <div class="nav-controls">
      <button class="nav-btn prev-btn" onclick="window.location.href='13-deployment-performance'">
        <span class="btn-glow">◀ PREV</span>
      </button>

      <div class="progress-container">
        <div class="ascii-progress">
          [<span class="progress-bar">██████████████░░</span>]
          <span class="progress-percent">87%</span>
        </div>
      </div>

      <button class="nav-btn next-btn" onclick="window.location.href='15-recap-takeaways'">
        <span class="btn-glow">NEXT ▶</span>
      </button>
    </div>
  </footer>
</div>