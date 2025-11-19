# Slide 13: Deployment and Performance

<div class="slide-header">
  <h1 class="slide-title">
    > DEPLOYMENT & PERFORMANCE <span class="subtitle-accent">[SCALE READY]</span>
  </h1>
</div>

<div class="deployment-overview">

## ▶ PRODUCTION DEPLOYMENT ARCHITECTURE

<div class="concept-highlight">
  <strong>Async I/O, graceful shutdowns, containerization with resource limits</strong>
</div>

```ascii
┌──────────────────────────────────────────────────────────────────┐
│                 PRODUCTION DEPLOYMENT STACK                      │
├──────────────────────────────────────────────────────────────────┤
│                                                                  │
│  ┌─────────────┐     ┌─────────────┐     ┌─────────────┐        │
│  │ LOAD        │────►│ MCP SERVER  │────►│ RESOURCES   │        │
│  │ BALANCER    │     │ CONTAINER   │     │ (DB/FILES)  │        │
│  │ (nginx)     │     │ (Docker)    │     │             │        │
│  └─────────────┘     └─────────────┘     └─────────────┘        │
│         │                    │                    │              │
│         ▼                    ▼                    ▼              │
│  ┌─────────────┐     ┌─────────────┐     ┌─────────────┐        │
│  │ TLS TERM    │     │ RESOURCE    │     │ MONITORING  │        │
│  │ + AUTH      │     │ LIMITS      │     │ & LOGGING   │        │
│  └─────────────┘     └─────────────┘     └─────────────┘        │
│                                                                  │
│  Horizontal scaling with multiple container instances            │
└──────────────────────────────────────────────────────────────────┘
```

</div>

<div class="performance-patterns">

## ▶ ASYNC I/O AND CONCURRENCY

```python
import asyncio
from typing import AsyncGenerator

@server.tool()
async def process_large_dataset(data_source: str) -> AsyncGenerator[str, None]:
    """Process large dataset with streaming results."""

    # Async file processing
    async with aiofiles.open(data_source, 'r') as file:
        async for chunk in file:
            # Non-blocking processing
            result = await process_chunk_async(chunk)

            # Stream results back
            yield f"Processed: {result}"

            # Yield control to event loop
            await asyncio.sleep(0)

# Concurrent tool execution
async def handle_multiple_requests():
    tasks = [
        process_tool_a(),
        process_tool_b(),
        process_tool_c()
    ]
    results = await asyncio.gather(*tasks, return_exceptions=True)
    return results
```

## ▶ GRACEFUL SHUTDOWN PATTERNS

<div class="shutdown-grid">

### 🛑 SIGNAL HANDLING
SIGTERM, SIGINT for clean shutdown

### ⏳ REQUEST COMPLETION
Wait for active requests to finish

### 🔄 RESOURCE CLEANUP
Close connections, flush buffers, save state

</div>

</div>

<div class="demo-section">

## 🎮 LIVE DEMO: RESOURCE SCOPING

<div class="demo-note">
  <strong>DEMONSTRATION:</strong> `listRoots` shows file scoping and safe enumeration
</div>

```terminal
$ mcp-inspector
> Call listRoots tool

Response: {
  "roots": [
    {
      "uri": "file:///workspace/mcp-demo",
      "name": "MCP Demo Project",
      "description": "Demo project files and resources"
    },
    {
      "uri": "file:///shared/templates",
      "name": "Shared Templates",
      "description": "Read-only template library"
    }
  ],
  "access_policy": {
    "read": ["*.md", "*.json", "*.yaml"],
    "write": ["workspace/**/*"],
    "exclude": [".env", "credentials.*", "*.key"]
  }
}

[SECURITY] Only listed roots accessible
[PERFORMANCE] Efficient directory enumeration
[AUDIT] All access attempts logged
```

### Performance Optimizations:
- **Lazy Loading**: Resources loaded on demand
- **Caching Strategy**: Frequently accessed data cached
- **Batch Operations**: Multiple file operations combined
- **Index Optimization**: Fast directory traversal

</div>

<div class="containerization">

## ▶ CONTAINERIZED DEPLOYMENT

```dockerfile
# Production-ready MCP server container
FROM python:3.11-slim

# Security: non-root user
RUN useradd -m -u 1000 mcpuser

# Performance: multi-stage build for smaller image
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# Resource limits in docker-compose
services:
  mcp-server:
    build: .
    user: "1000:1000"
    deploy:
      resources:
        limits:
          cpus: '2.0'
          memory: 1G
        reservations:
          cpus: '0.5'
          memory: 256M
    healthcheck:
      test: ["CMD", "curl", "-f", "http://localhost:8000/health"]
      interval: 30s
      timeout: 10s
      retries: 3
```

## ▶ MONITORING & OBSERVABILITY

<div class="monitoring-grid">

### 📊 METRICS COLLECTION
Response times, throughput, error rates, resource usage

### 🔍 DISTRIBUTED TRACING
Request flows across multiple servers

### 📈 PERFORMANCE DASHBOARDS
Real-time operational insights

### 🚨 ALERTING
Automated notifications for anomalies

</div>

</div>

<div class="scaling-strategies">

## ▶ HORIZONTAL SCALING STRATEGIES

```yaml
# Kubernetes deployment example
apiVersion: apps/v1
kind: Deployment
metadata:
  name: mcp-server
spec:
  replicas: 3
  selector:
    matchLabels:
      app: mcp-server
  template:
    spec:
      containers:
      - name: mcp-server
        image: mcp-server:latest
        resources:
          requests:
            memory: "256Mi"
            cpu: "250m"
          limits:
            memory: "512Mi"
            cpu: "500m"
        livenessProbe:
          httpGet:
            path: /health
            port: 8000
        readinessProbe:
          httpGet:
            path: /ready
            port: 8000
```

### Scaling Considerations:
- **Stateless Design**: Servers can be replicated easily
- **Load Distribution**: Round-robin or intelligent routing
- **Health Checks**: Automatic failover and recovery
- **Rolling Updates**: Zero-downtime deployments

</div>

<div class="slide-footer">
  <span class="demo-ready">🎮 SCOPING DEMO READY</span>
  <span class="next-indicator">▶ NEXT: Advanced Workflow Examples</span>
</div>

<div class="cyberpunk-navigation">
  <header class="slide-header">
    <div class="terminal-prompt">
      > ADVANCED MCP PRESENTATION
    </div>
    <div class="slide-counter">
      SLIDE 13/16
    </div>
  </header>

  <footer class="slide-navigation">
    <div class="nav-controls">
      <button class="nav-btn prev-btn" onclick="window.location.href='12-security-practices'">
        <span class="btn-glow">◀ PREV</span>
      </button>

      <div class="progress-container">
        <div class="ascii-progress">
          [<span class="progress-bar">█████████████░░░</span>]
          <span class="progress-percent">81%</span>
        </div>
      </div>

      <button class="nav-btn next-btn" onclick="window.location.href='14-workflow-examples'">
        <span class="btn-glow">NEXT ▶</span>
      </button>
    </div>
  </footer>
</div>