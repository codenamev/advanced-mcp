# Slide 12: Security Best Practices

<div class="slide-header">
  <h1 class="slide-title">
    > SECURITY BEST PRACTICES <span class="subtitle-accent">[PRODUCTION READY]</span>
  </h1>
</div>

<div class="security-overview">

## ▶ ENTERPRISE SECURITY ARCHITECTURE

<div class="concept-highlight">
  <strong>OAuth2 authentication, input validation, audit logs, and sandboxed execution</strong>
</div>

```ascii
┌──────────────────────────────────────────────────────────────────┐
│                     SECURITY ARCHITECTURE                       │
├──────────────────────────────────────────────────────────────────┤
│                                                                  │
│  ┌─────────────┐    OAuth2/JWT    ┌─────────────┐               │
│  │   CLIENT    │◄────────────────►│ AUTH SERVER │               │
│  │  (Claude)   │                  │             │               │
│  └─────────────┘                  └─────────────┘               │
│         │                                 │                     │
│         ▼          Validated Token        ▼                     │
│  ┌─────────────┐                  ┌─────────────┐               │
│  │ MCP SERVER  │◄─────────────────┤ VALIDATION  │               │
│  │             │                  │ MIDDLEWARE  │               │
│  └─────────────┘                  └─────────────┘               │
│         │                                                       │
│         ▼                                                       │
│  ┌─────────────┐     ┌─────────────┐     ┌─────────────┐       │
│  │INPUT VALID  │────►│SANDBOX EXEC │────►│AUDIT LOGGER │       │
│  │ + SCHEMA    │     │ + LIMITS    │     │ + MONITOR   │       │
│  └─────────────┘     └─────────────┘     └─────────────┘       │
│                                                                  │
│  Multi-layered security with defense in depth principles        │
└──────────────────────────────────────────────────────────────────┘
```

</div>

<div class="security-patterns">

## ▶ CRITICAL SECURITY PATTERNS

<div class="pattern-grid">

### 🔐 AUTHENTICATION
OAuth2 for HTTP servers, token validation

### ✅ INPUT VALIDATION
Schema enforcement, type checking, bounds validation

### 🏰 SANDBOXING
Restricted file access, process isolation, resource limits

</div>

## ▶ ROOTS-BASED ACCESS CONTROL

```json
{
  "server_config": {
    "name": "secure-filesystem",
    "roots": [
      {
        "uri": "file:///workspace/project1",
        "name": "Project 1 Files",
        "description": "Read/write access to project files only"
      },
      {
        "uri": "file:///shared/docs",
        "name": "Shared Documentation",
        "description": "Read-only access to documentation"
      }
    ]
  }
}
```

### Access Control Benefits:
- **Scope Limitation**: Servers can only access defined roots
- **Path Traversal Prevention**: Cannot access parent directories
- **Audit Trail**: All file operations logged with root context
- **Principle of Least Privilege**: Minimal necessary permissions

</div>

<div class="demo-section">

## 🎮 LIVE DEMO: SECURITY CONSIDERATIONS

<div class="demo-note">
  <strong>DEMONSTRATION:</strong> `printEnv` tool - safe for local debug, dangerous remotely
</div>

```terminal
$ mcp-inspector
> Examine printEnv tool security implications

[LOCAL DEVELOPMENT]
Call: printEnv()
Result: {
  "NODE_ENV": "development",
  "PATH": "/usr/local/bin:/usr/bin",
  "HOME": "/Users/developer",
  "DEMO_MODE": "true"
}
Status: ✅ Safe - controlled environment

[PRODUCTION DEPLOYMENT]
Call: printEnv()
Security Risk: ❌ HIGH RISK
Reason: Could expose:
  - Database credentials
  - API keys and secrets
  - Internal service URLs
  - System configuration details

[MITIGATION]
- Environment filtering
- Production mode restrictions
- Audit logging for sensitive operations
- Role-based access controls
```

### Security Assessment Framework:
1. **Risk Classification**: Low/Medium/High/Critical
2. **Environment Context**: Development vs Production
3. **Data Sensitivity**: Public vs Internal vs Secret
4. **Access Controls**: Who can execute what tools

</div>

<div class="validation-patterns">

## ▶ INPUT VALIDATION & SCHEMA ENFORCEMENT

```python
from pydantic import BaseModel, validator
from typing import Literal

class SecureToolInput(BaseModel):
    file_path: str
    operation: Literal["read", "write", "delete"]
    max_size_bytes: int = 1024 * 1024  # 1MB default

    @validator('file_path')
    def validate_file_path(cls, v):
        # Prevent path traversal
        if '..' in v or v.startswith('/'):
            raise ValueError("Invalid file path")
        return v

    @validator('max_size_bytes')
    def validate_size(cls, v):
        if v > 10 * 1024 * 1024:  # 10MB max
            raise ValueError("File size exceeds limit")
        return v
```

## ▶ AUDIT & MONITORING

<div class="audit-grid">

### 📊 COMPREHENSIVE LOGGING
All tool executions, parameter values, results

### 🚨 ANOMALY DETECTION
Unusual patterns, failed authentications, suspicious activity

### 📈 PERFORMANCE MONITORING
Resource usage, response times, error rates

### 🔍 FORENSIC CAPABILITIES
Full request/response chains for security analysis

</div>

</div>

<div name="production-checklist">

## ✅ PRODUCTION SECURITY CHECKLIST

```
├── Authentication       │ OAuth2/JWT token validation
├── Authorization        │ Role-based access controls (RBAC)
├── Input Validation     │ Schema enforcement, bounds checking
├── Output Sanitization  │ Prevent data leakage, XSS protection
├── Audit Logging        │ Comprehensive request/response logging
├── Rate Limiting        │ Prevent abuse and DoS attacks
├── Encryption           │ TLS in transit, encryption at rest
├── Sandbox Execution    │ Process isolation, resource limits
├── Dependency Security  │ Regular security updates, CVE monitoring
└── Incident Response    │ Alerting, containment, recovery procedures
```

</div>

<div class="slide-footer">
  <span class="demo-ready">🎮 SECURITY DEMO READY</span>
  <span class="next-indicator">▶ NEXT: Deployment & Performance</span>
</div>

<div class="cyberpunk-navigation">
  <header class="slide-header">
    <div class="terminal-prompt">
      > ADVANCED MCP PRESENTATION
    </div>
    <div class="slide-counter">
      SLIDE 12/16
    </div>
  </header>

  <footer class="slide-navigation">
    <div class="nav-controls">
      <button class="nav-btn prev-btn" onclick="window.location.href='11-tool-patterns'">
        <span class="btn-glow">◀ PREV</span>
      </button>

      <div class="progress-container">
        <div class="ascii-progress">
          [<span class="progress-bar">████████████░░░░</span>]
          <span class="progress-percent">75%</span>
        </div>
      </div>

      <button class="nav-btn next-btn" onclick="window.location.href='13-deployment-performance'">
        <span class="btn-glow">NEXT ▶</span>
      </button>
    </div>
  </footer>
</div>