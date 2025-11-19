**Title: Building Advanced MCP Servers: Techniques, Patterns, and Examples**

**Slide 1: Title Slide**

* Building Advanced MCP Servers
* AI Engineering Working Group | November 2025
* Your Name

**Slide 2: What is MCP? (Quick Recap)**

* Open protocol for connecting LLMs to external tools, data, and prompts
* Enables modular, scalable integration (M + N problem)
* Server = "Toolbox" for the model

**Slide 3: Advanced Focus Today**

* How to build *MCP servers*, not just use them
* Advanced features: tools, prompts, resources, sampling
* Secure, scalable design patterns
* Live example: Everything MCP Server + MCP Inspector

---

**Slide 4: Core Server Architecture**

* Use MCP SDKs (Python, Go, Java) to expose tools
* Modular design: one domain per server
* Stateless, idempotent tool functions
* Transport options: stdio vs HTTP/SSE
* *Example: Everything Server's add & echo tools – minimal schema, fast feedback*

**Slide 5: Tools: The Heart of an MCP Server**

* Define name, title, description, and JSON schema
* *Example: Everything Server's `longRunningOperation` tool – shows async streaming + notifications*
* Prefer fine-grained tools over monoliths
* Descriptive metadata helps LLM choose intelligently

**Slide 6: Resources: Read-Only Context for Models**

* Provide structured content on demand (URI-based)
* *Example: test://static/resource/42 in Everything Server auto-updates every 5s*
* Great for large data (file contents, search results)
* Visible in Inspector tab, subscribable for updates

**Slide 7: Prompt Templates**

* Reusable structured conversations
* *Example: `resource_prompt` uses a dynamic argument to load a resource*
* Separate prompt content from tool logic
* Store in config or external file for reusability

**Slide 8: Sampling: Server-Asks-Model**

* Server sends prompt to model mid-tool execution
* *Example: `sampleLLM` tool in Everything Server triggers completions*
* Use for summarization, code-gen, user emulation
* Always validate output before trusting actions

---

**Slide 9: Multi-Server Architecture**

* Compose specialized servers: Git, Filesystem, DB, etc.
* *Example: Claude connects to Everything Server + Git Server + Filesystem Server concurrently*
* Keep scopes focused, let client orchestrate
* Use unique namespaces to avoid collisions

**Slide 10: Live Demo: Everything MCP Server + MCP Inspector**

* Launch with: `npx -y @modelcontextprotocol/server-everything`
* Inspect tools, resources, prompts in real time
* *Try: call `echo`, invoke `complex_prompt`, subscribe to a resource*
* Zero-setup, safe for live exploration

**Slide 11: Tool Design Patterns**

* Categorize tools (devops, data, creative)
* *Example: `annotatedMessage` shows structured metadata (error/success/debug)*
* Reference large outputs via resources
* Use frameworks like FastMCP for declarative structure

**Slide 12: Security Best Practices**

* OAuth2 for HTTP servers
* *Example: `printEnv` tool is safe for local debug, dangerous remotely*
* Input validation and schema enforcement
* Use Roots to restrict access scope (e.g. sandbox file I/O)
* Audit logs, confirmation tools for destructive actions

**Slide 13: Deployment and Performance**

* Async I/O and concurrency for scaling
* Graceful shutdowns, version negotiation
* *Example: `listRoots` shows file scoping and safe enumeration*
* Stream large results or expose them as resources
* Containerize servers (Docker) with limits

---

**Slide 14: Advanced Workflow Examples**

* Claude: resource → prompt → sampling → action
* *Demo: Use `sampleLLM` to write markdown summary from resource*
* Combine `complex_prompt` + `getTinyImage` to mix modalities
* Subscribed resource auto-refresh visible in Inspector

**Slide 15: Recap & Key Takeaways**

* MCP servers provide tools, resources, prompts, and sampling
* Everything Server = gold-standard for demos
* Secure by design, optimized for AI agents
* Build modular, testable, and observable components

**Slide 16: Resources & Questions**

* [modelcontextprotocol.info](https://modelcontextprotocol.info)
* GitHub: model-context/reference-servers
* [Everything Server on npm](https://www.npmjs.com/package/@modelcontextprotocol/server-everything)
* [genai-toolbox (Google)](https://github.com/google/genai-toolbox)
* MCP Inspector: inspect tools/resources live
* Questions?

