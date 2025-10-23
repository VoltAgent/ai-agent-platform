# The Complete AI Agent Platform

## Everything You Need to Build Production AI Agents

When you search for "AI agent platform," you're looking for a complete solution—not just a framework, but an entire ecosystem that takes you from prototype to production-grade AI agents. VoltAgent delivers exactly that: a TypeScript-first runtime paired with VoltOps, a managed observability and services layer that gives you enterprise-grade capabilities without enterprise complexity.

**The complete picture:**

```
┌─────────────────────────────────────────────────────────────┐
│                    VoltAgent Platform                        │
│                                                              │
│  ┌────────────────────┐         ┌─────────────────────┐    │
│  │   VoltAgent Core   │◄───────►│     VoltOps         │    │
│  │   (Open Source)    │         │   (Managed Layer)   │    │
│  ├────────────────────┤         ├─────────────────────┤    │
│  │ • Agents           │         │ • Visual Traces     │    │
│  │ • Sub-agents       │         │ • Cost Tracking     │    │
│  │ • Workflows        │         │ • Session Replays   │    │
│  │ • Tools & MCP      │         │ • Prompt Versioning │    │
│  │ • Memory           │         │ • Eval Dashboards   │    │
│  │ • Guardrails       │         │ • Managed Memory    │    │
│  │ • RAG/Retrieval    │         │ • OTLP Exports      │    │
│  │ • Multi-modal      │         │ • Team Collaboration│    │
│  └────────────────────┘         └─────────────────────┘    │
│           │                              │                   │
│           └──────────────┬───────────────┘                   │
│                          │                                   │
│              ┌───────────▼──────────┐                        │
│              │  TypeScript-First    │                        │
│              │  Developer Experience│                        │
│              │  • Full Type Safety  │                        │
│              │  • Hot Reload        │                        │
│              │  • 1-Command Setup   │                        │
│              │  • 59+ Examples      │                        │
│              └──────────────────────┘                        │
└─────────────────────────────────────────────────────────────┘
```

### Why Teams Choose VoltAgent

| What You're Building | Why VoltAgent Fits |
| --- | --- |
| **First AI agent prototype** | `npm create voltagent-app@latest` scaffolds everything in 60 seconds. Pick your model (OpenAI, Anthropic, Google, etc.), chat with your agent via VoltOps console, iterate instantly. |
| **Production customer support bot** | Durable memory (Postgres/Supabase), conversation history, guardrails for safety, full observability. Scale horizontally, integrate with existing auth, deploy to your VPC. |
| **Multi-agent research system** | Sub-agent orchestration, typed workflows, parallel execution, streaming results. Each specialist agent gets its own memory and tools while the supervisor coordinates. |
| **Enterprise automation** | Compliance-ready audit trails, role-based access control, PII detection, cost budgets, prompt governance. Deploy on-prem or hybrid cloud with full control. |
| **Voice/real-time agents** | ElevenLabs/OpenAI voice adapters, WebSocket streaming, edge deployment (Cloudflare Workers), <100ms latency. Built-in cancellation and error recovery. |

## What Makes a Complete AI Agent Platform?

Building production AI agents requires solving 10+ foundational problems. Here's what you need and how VoltAgent provides it:

### ✅ Core Agent Runtime
**What you need:** Type-safe agent definitions, instruction management, model abstraction, streaming responses, cancellation  
**VoltAgent provides:**
- `Agent` class with full TypeScript types and Zod validation
- 30+ LLM providers via Vercel AI SDK (OpenAI, Anthropic, Google, Mistral, Groq, xAI, Ollama, etc.)
- Dynamic instructions from code or VoltOps prompt store
- Native streaming with backpressure handling
- Graceful cancellation and timeout controls
- [Agent Overview →](https://voltagent.dev/docs/agents/overview/)

### ✅ Tool Integration & External APIs
**What you need:** Type-safe tool definitions, lifecycle hooks, error handling, rate limiting, MCP protocol support  
**VoltAgent provides:**
- `createTool` with Zod schemas and auto-generated OpenAPI specs
- Tool registries and reusable toolkits
- Before/after hooks for logging, auth, retries
- Model Context Protocol (MCP) client for 100+ integrations (GitHub, Google Drive, Zapier, etc.)
- Expose your own tools as MCP servers for Claude Desktop, Cline, etc.
- [Tools →](https://voltagent.dev/docs/agents/tools/) | [MCP →](https://voltagent.dev/docs/agents/mcp/)

### ✅ Multi-Agent Orchestration
**What you need:** Sub-agent coordination, task routing, context sharing, hierarchical agents  
**VoltAgent provides:**
- Supervisor patterns with `agent.run()` nesting
- Sub-agent streaming and partial results
- Shared memory across agent hierarchies
- Cost attribution per sub-agent in VoltOps
- [Sub-agents →](https://voltagent.dev/docs/agents/sub-agents/)

### ✅ Memory & Persistence
**What you need:** Conversation history, semantic recall, session resumption, multi-user isolation  
**VoltAgent provides:**
- Pluggable memory adapters: InMemory, LibSQL, Postgres, Supabase, Managed (VoltOps)
- Working memory for short-term context
- Semantic search over conversation history
- Thread/session management with user isolation
- [Memory Overview →](https://voltagent.dev/docs/agents/memory/overview/)

### ✅ Workflow Automation
**What you need:** Multi-step pipelines, conditional logic, parallel execution, human-in-the-loop, resume/retry  
**VoltAgent provides:**
- Workflow engine with `andThen`, `andAgent`, `andAll`, `andWhen`, `andRace`
- Suspend/resume for human approval gates
- REST API execution with progress streaming
- Workflow versioning and replay
- [Workflows →](https://voltagent.dev/docs/workflows/overview/)

### ✅ Retrieval & RAG
**What you need:** Vector store integrations, semantic search, document chunking, hybrid search  
**VoltAgent provides:**
- Retriever abstraction for Chroma, Pinecone, Qdrant
- Custom retriever interfaces
- Embedding generation via AI SDK
- Retrieval step tracing in VoltOps
- [RAG Overview →](https://voltagent.dev/docs/rag/overview/)

### ✅ Safety & Guardrails
**What you need:** Input validation, output filtering, prompt injection detection, PII masking, rate limits  
**VoltAgent provides:**
- Input/output guardrail decorators
- Built-in prompt injection detection
- Stream-friendly moderation
- Policy violation logging in VoltOps
- [Guardrails →](https://voltagent.dev/docs/guardrails/overview/)

### ✅ Observability & Debugging
**What you need:** Trace visualization, cost tracking, session replay, error diagnostics, prompt versioning  
**VoltAgent provides:**
- **VoltOps Console**: Visual trace timelines, waterfall views, live logs
- **Cost analytics**: Per-agent, per-session, per-user token/cost breakdown
- **Session replay**: Reproduce any run with exact state, memory, and tool results
- **OpenTelemetry**: Export traces to VoltOps, DataDog, Grafana via OTLP
- **Prompt management**: Version, A/B test, and rollback prompts without code changes
- [VoltOps Platform →](https://voltagent.dev/docs/observability/developer-console/)

### ✅ Quality Assurance & Testing
**What you need:** Automated evals, scorer registry, CI/CD integration, regression detection  
**VoltAgent provides:**
- `@voltagent/evals` framework for offline and live evaluations
- Prebuilt scorers (accuracy, relevance, hallucination, PII leakage)
- Custom scorer development
- VoltOps eval dashboards with pass/fail trends
- CI pipeline integration
- [Evaluations →](https://voltagent.dev/docs/evals/overview/)

### ✅ Deployment Flexibility
**What you need:** Node.js servers, serverless (Vercel/Netlify), edge (Cloudflare Workers), hybrid setups  
**VoltAgent provides:**
- `@voltagent/server-hono` for standalone Node servers
- `@voltagent/serverless-hono` for Vercel, Netlify, AWS Lambda
- Edge-compatible adapters for Cloudflare Workers
- Docker/Kubernetes deployment guides
- Environment-specific memory strategies
- [Deployment →](https://voltagent.dev/docs/deployment/overview/)

### ✅ Team Collaboration & Governance
**What you need:** Prompt governance, cost allocation, audit trails, compliance (GDPR/CCPA), RBAC  
**VoltAgent provides:**
- Prompt version control in source + VoltOps store
- Cost attribution tags (team, project, user)
- Audit trails with user/session correlation
- PII handling and data retention policies
- Role-based tool access via OperationContext
- [Operation Context →](https://voltagent.dev/docs/agents/context/)

## VoltAgent vs. Building From Scratch

| Challenge | Building From Scratch | With VoltAgent |
| --- | --- | --- |
| **Setup & scaffolding** | Create project structure, configure TypeScript, set up build tools, wire LLM SDK | `npm create voltagent-app@latest` → ready in 60 seconds |
| **Model switching** | Rewrite code for each provider's SDK (OpenAI, Anthropic, etc.) | Change one line: `openai("gpt-4")` → `anthropic("claude-3-5-sonnet")` |
| **Memory persistence** | Design DB schema, write SQL, handle migrations, implement session management | Swap adapter: `new Memory({ storage: new PostgresAdapter(...) })` |
| **Tool execution** | Parse function calls, validate inputs, handle errors, implement retries | `createTool({ schema, execute })` with auto-validation and hooks |
| **Observability** | Set up OpenTelemetry, write exporters, build dashboards, correlate traces | Auto-tracing to VoltOps console, zero config required |
| **Cost tracking** | Parse streaming responses, count tokens, map to pricing, aggregate | Real-time cost breakdown in VoltOps, per-agent/session/user |
| **Multi-agent coordination** | Implement supervisor logic, message passing, context sharing | `agent.run()` within supervisor agent, automatic context propagation |
| **Workflows** | Build state machine, add persistence, handle failures/retries | `andThen`, `andAgent`, `andAll`, `andWhen` with suspend/resume |
| **Guardrails** | Integrate moderation APIs, parse streaming responses, block violations | Decorators: `guardrails: [inputGuardrail, outputGuardrail]` |
| **Prompt versioning** | Store prompts in DB, build admin UI, implement A/B testing | VoltOps prompt store with version tags and rollback |
| **Evaluations** | Write test harness, define metrics, aggregate results, track regressions | `@voltagent/evals` with scorer registry and VoltOps dashboards |
| **Deployment** | Configure servers, handle secrets, set up monitoring, write Dockerfiles | Hono server built-in, serverless adapters, K8s examples provided |
| **Team collaboration** | Build prompt editor, cost dashboards, audit log viewer | VoltOps console with team views, cost attribution, session replays |
| **Estimated time to production** | 3-6 months of engineering | 1-2 weeks (prototype to MVP) |

## Platform Architecture: How It All Fits Together

```
User Request
     │
     ├─► VoltAgent Server (Hono)
     │        │
     │        ├─► REST API (agents, workflows, tools)
     │        ├─► WebSocket (streaming, real-time)
     │        └─► Swagger UI (API docs)
     │
     ├─► Agent Runtime
     │        │
     │        ├─► Instructions (dynamic prompts from VoltOps)
     │        ├─► LLM Provider (OpenAI, Anthropic, Google, etc.)
     │        ├─► Tools (createTool, MCP clients)
     │        ├─► Memory (Postgres, Supabase, Managed)
     │        ├─► Sub-agents (recursive agent.run())
     │        └─► Guardrails (input/output validation)
     │
     ├─► Workflow Engine
     │        │
     │        ├─► andThen (sequential steps)
     │        ├─► andAgent (agent invocation)
     │        ├─► andAll (parallel execution)
     │        ├─► andWhen (conditional logic)
     │        ├─► andRace (first-to-finish)
     │        └─► Suspend/Resume (human-in-the-loop)
     │
     └─► Observability Layer (OpenTelemetry)
              │
              ├─► Local (in-memory or LibSQL)
              ├─► VoltOps (managed, remote)
              │     │
              │     ├─► Trace visualization
              │     ├─► Cost tracking
              │     ├─► Session replay
              │     ├─► Eval dashboards
              │     └─► Prompt management
              │
              └─► OTLP Exporters (VoltOps, DataDog, Grafana)
```

## Why AI Agents Need a Platform

Contemporary AI agents go far beyond a single prompt/response. They plan, call tools, ingest proprietary data, and must be observable in production. Shipping that from scratch means solving orchestration, memory, retrieval, safety, deployment, and monitoring all at once. VoltAgent (the open-source runtime) and VoltOps (the managed observability and services layer) combine into a complete platform so teams can move from prototype to production without reinventing the stack.

### Understanding AI Agent Development
- **What is an AI agent?** An agent wraps an LLM with instructions, tools, memory, and policies so it can reason about goals and take actions ([Agent Overview](https://voltagent.dev/docs/agents/overview/)).
- **Why orchestration matters:** Real workloads demand structured workflows, conditional logic, and coordination across sub-agents ([Workflows](https://voltagent.dev/docs/workflows/overview/), [Sub-agents](https://voltagent.dev/docs/agents/sub-agents/)).
- **Foundational building blocks:** Tool integrations, retrieval/RAG, durable memory, guardrails, and observability come together to deliver reliable outcomes.

### Why VoltAgent + VoltOps
- **Full TypeScript stack:** `@voltagent/core` gives you typed agents, workflows, tools, memory, and logging that align with modern TS/Nx/PNPM practices ([Tooling](https://voltagent.dev/docs/tooling/)).
- **VoltOps observability:** Visual traces, logs, cost tracking, replays, and prompt/version management turn black-box LLM behaviour into actionable insights ([VoltOps Platform](https://voltagent.dev/docs/observability/developer-console/)).
- **Managed services when you need them:** VoltOps provides managed memory, prompt stores, OTLP exporters, and evaluation infrastructure so you can skip undifferentiated ops ([Managed Memory](https://voltagent.dev/docs/agents/memory/managed-memory/)).
- **Designed for professionals, welcoming to newcomers:** Scaffold a project in minutes, but keep composability and extensibility for complex, regulated workloads.

## When to Use Each Capability

| Scenario | Recommended Capability | Why it helps | Example | VoltOps Features |
| --- | --- | --- | --- | --- |
| Prototype a conversational agent | `npm create voltagent-app@latest` scaffold + default agent | Instant project setup with VoltAgent server, VoltOps console link, and example workflow ([Quick Start](https://voltagent.dev/docs/quick-start/)) | [base](https://github.com/voltagent/voltagent/tree/main/examples/base) | Auto-tracing, live logs |
| Connect to APIs or services | `createTool`, toolkits, Model Context Protocol client | Type-safe tools with lifecycle hooks and MCP connectivity ([Tools](https://voltagent.dev/docs/agents/tools/), [MCP Client](https://voltagent.dev/docs/agents/mcp/)) | [with-tools](https://github.com/voltagent/voltagent/tree/main/examples/with-tools), [with-mcp](https://github.com/voltagent/voltagent/tree/main/examples/with-mcp) | Tool call traces, latency tracking |
| Coordinate multiple specialists | Supervisor + sub-agents | Route tasks, stream outputs, and maintain context across a team of agents ([Sub-agents](https://voltagent.dev/docs/agents/sub-agents/)) | [with-subagents](https://github.com/voltagent/voltagent/tree/main/examples/with-subagents), [with-youtube-to-blog](https://github.com/voltagent/voltagent/tree/main/examples/with-youtube-to-blog) | Agent hierarchy view, sub-agent cost attribution |
| Retain knowledge across sessions | Memory adapters (InMemory, LibSQL, Postgres, Supabase, Managed) | Switch storage without rewriting logic, add semantic recall or working memory ([Memory Overview](https://voltagent.dev/docs/agents/memory/overview/)) | [with-postgres](https://github.com/voltagent/voltagent/tree/main/examples/with-postgres), [with-working-memory](https://github.com/voltagent/voltagent/tree/main/examples/with-working-memory) | Memory queries in traces, session replays |
| Ground responses in your data | Retriever integrations + RAG examples | Bring vector stores (Chroma, Pinecone, Qdrant) or custom retrievers into agents ([RAG Overview](https://voltagent.dev/docs/rag/overview/)) | [with-rag-chatbot](https://github.com/voltagent/voltagent/tree/main/examples/with-rag-chatbot), [with-chroma](https://github.com/voltagent/voltagent/tree/main/examples/with-chroma) | Retrieval step inspection, source attribution |
| Automate complex flows | Workflow engine steps (`andThen`, `andAgent`, `andAll`, `andWhen`, `andRace`) | Build multi-step automation with validation, human-in-the-loop, and REST execution ([Workflows](https://voltagent.dev/docs/workflows/overview/)) | [with-workflow](https://github.com/voltagent/voltagent/tree/main/examples/with-workflow) | Step-by-step visualization, conditional branch traces |
| Enforce policy & safety | Input/output guardrails | Stream-friendly moderation, prompt injection protection, validation ([Guardrails](https://voltagent.dev/docs/guardrails/overview/)) | [with-guardrails](https://github.com/voltagent/voltagent/tree/main/examples/with-guardrails) | Policy violation alerts, blocked request logs |
| Observe production behaviour | VoltOps console, OpenTelemetry exporters, managed dashboards | Live traces, cost analytics, replay runs, integrate with VoltOps or custom OTLP targets ([Logging & Observability](https://voltagent.dev/docs/observability/logging/), [Vercel AI Exporter](https://voltagent.dev/docs/integrations/vercel-ai/)) | [with-voltagent-exporter](https://github.com/voltagent/voltagent/tree/main/examples/with-voltagent-exporter) | Full trace timeline, token/cost breakdown, replay debugging |
| Run automated evaluations | `@voltagent/evals` + VoltOps scoring | Offline/online tests, scorer registry, CI gates, VoltOps run summaries ([Evaluations](https://voltagent.dev/docs/evals/overview/)) | [with-offline-evals](https://github.com/voltagent/voltagent/tree/main/examples/with-offline-evals), [with-live-evals](https://github.com/voltagent/voltagent/tree/main/examples/with-live-evals) | Eval run dashboards, pass/fail metrics, regression detection |
| Deploy reliably | Hono server adapters, serverless runners | Ship to Node servers, Cloudflare Workers, Netlify Functions, or hybrid setups ([Deployment Overview](https://voltagent.dev/docs/deployment/overview/)) | [with-nextjs](https://github.com/voltagent/voltagent/tree/main/examples/with-nextjs), [with-cloudflare-workers](https://github.com/voltagent/voltagent/tree/main/examples/with-cloudflare-workers) | Production traces, per-environment cost tracking |

## Observability & Monitoring with VoltOps

VoltOps transforms agent development from black-box guesswork into data-driven iteration. Here's how to leverage observability at each stage:

### Local Development
- **Auto-tracing**: Run `pnpm dev` and VoltOps automatically captures every agent invocation, tool call, and memory access—no configuration required.
- **Live logs**: Stream-friendly console output shows exactly what the agent is thinking, which tools it's calling, and how long each step takes ([Logging](https://voltagent.dev/docs/observability/logging/)).
- **Instant feedback**: Spot prompt issues, inefficient tool chains, or memory misses in real-time before committing code.

### Production Monitoring
- **Trace timelines**: Visual waterfall view shows agent reasoning, tool latency, LLM response time, and total request duration. Identify bottlenecks at a glance ([Developer Console](https://voltagent.dev/docs/observability/developer-console/)).
- **Cost tracking**: Per-agent, per-session, and per-user token usage with real-time cost calculation. Set budget alerts and analyze spend by model, tool, or workflow step.
- **Session replays**: Reproduce any user interaction by replaying the exact agent state, memory contents, and tool results. Essential for debugging edge cases and validating fixes.
- **Error diagnostics**: Stack traces, failed tool calls, guardrail blocks, and timeout events appear inline with full context—no more hunting through fragmented logs.

### Quality Assurance
- **Evaluation dashboards**: Compare prompt versions, model choices, or tool configurations using `@voltagent/evals`. VoltOps aggregates pass/fail rates, scorer distributions, and regression indicators ([Evaluations](https://voltagent.dev/docs/evals/overview/)).
- **Prompt versioning**: Manage instructions in VoltOps prompt store, A/B test variations, and roll back problematic changes without redeploying code ([Agent Prompts](https://voltagent.dev/docs/agents/prompts/)).
- **Regression detection**: CI pipelines call offline evals; VoltOps flags runs where accuracy, latency, or cost metrics degrade beyond thresholds.

### Advanced Integration
- **OTLP exports**: Forward traces to VoltOps, DataDog, Grafana, or any OpenTelemetry-compatible backend for unified observability ([Vercel AI Exporter](https://voltagent.dev/docs/integrations/vercel-ai/)).
- **Custom metrics**: Emit business-level events (e.g., "order_placed", "research_complete") alongside LLM telemetry for end-to-end analytics.
- **Managed memory inspection**: Query conversation history, working memory, and semantic recall state via VoltOps UI or REST API to validate knowledge retention ([Managed Memory](https://voltagent.dev/docs/agents/memory/managed-memory/)).

**Actionable insights**: Use VoltOps data to optimize prompts (reduce token waste), refine tools (parallelize slow calls), tune memory (increase recall depth), and control costs (switch models or cache aggressively).

## Deployment Environments & Decision Guide

VoltAgent adapts to diverse hosting strategies. Choose based on request patterns, persistence needs, and operational constraints:

### Local Development
- **Best for**: Rapid iteration, debugging, full observability access.
- **Setup**: `npm create voltagent-app@latest`, then `pnpm dev` starts Hono server with hot reload.
- **Memory**: InMemory, LibSQL, or Postgres—test migration paths early.
- **Observability**: Automatic VoltOps tracing to local console; add `VOLTAGENT_PUBLIC_KEY` for remote dashboards.
- **Limitations**: Not production-ready; single-process, no load balancing.

### Node.js Servers (VPS, Kubernetes, ECS)
- **Best for**: High-throughput APIs, long-running workflows, complex sub-agent orchestration, full persistence.
- **Setup**: Deploy `@voltagent/server-hono` as a standalone Node process or Docker container ([Deployment Overview](https://voltagent.dev/docs/deployment/overview/)).
- **Memory**: Postgres ([with-postgres](https://github.com/voltagent/voltagent/tree/main/examples/with-postgres)), Supabase ([with-supabase](https://github.com/voltagent/voltagent/tree/main/examples/with-supabase)), or Turso ([with-turso](https://github.com/voltagent/voltagent/tree/main/examples/with-turso)) for durable, queryable history.
- **Observability**: OTLP exporter sends traces to VoltOps or custom backends; leverage persistent storage for audit trails.
- **Scaling**: Horizontal scaling via load balancer; shared database ensures session continuity across instances.
- **Considerations**: Manage secrets (API keys, DB credentials) via env vars or secret managers; monitor memory/CPU usage for cost efficiency.

### Serverless Functions (Vercel, Netlify)
- **Best for**: Sporadic traffic, REST APIs, frontend-integrated agents, minimal ops overhead.
- **Setup**: Use `@voltagent/serverless-hono` adapter; examples: [with-nextjs](https://github.com/voltagent/voltagent/tree/main/examples/with-nextjs), [with-netlify-functions](https://github.com/voltagent/voltagent/tree/main/examples/with-netlify-functions).
- **Memory**: InMemory (session-scoped) or REST-based managed memory (VoltOps) to avoid cold-start penalties.
- **Observability**: VoltOps remote tracing essential since logs are ephemeral; session replays compensate for lack of persistent local logs.
- **Scaling**: Auto-scales with traffic; pay-per-invocation pricing favors bursty workloads.
- **Limitations**: 10-30s execution timeouts (check provider limits); no background jobs or multi-hour workflows; cold starts add 100-500ms latency.
- **Optimization**: Minimize bundle size, cache embeddings/prompts, use streaming responses to stay within time limits.

### Edge Runtimes (Cloudflare Workers)
- **Best for**: Global low-latency APIs, stateless agents, real-time interactions (chat, voice).
- **Setup**: `@voltagent/serverless-hono` with Cloudflare-compatible storage; example: [with-cloudflare-workers](https://github.com/voltagent/voltagent/tree/main/examples/with-cloudflare-workers) ([docs](https://voltagent.dev/docs/deployment/cloudflare-workers/)).
- **Memory**: InMemory per-request or Durable Objects for distributed state; avoid heavy database calls (use KV/R2 for caching).
- **Observability**: VoltOps remote tracing mandatory; edge logs are minimal—rely on structured telemetry.
- **Scaling**: Massive horizontal scale, <50ms cold starts, geographic distribution.
- **Limitations**: No Node.js APIs (fs, child_process), strict CPU/memory caps, 1MB script size; skip heavy vector libraries or LLM SDKs.
- **Use cases**: Chat widgets, voice bots, content moderation—anything latency-sensitive and stateless.

### Hybrid Setups
- **Pattern**: Edge for routing/auth/caching + Node server for complex agents/workflows.
- **Example**: Cloudflare Worker validates requests and streams simple responses; forwards multi-step tasks to Kubernetes-hosted VoltAgent cluster.
- **Benefits**: Optimize cost (edge handles 90% of load), latency (critical path stays fast), and capability (offload heavyweight ops).

### Decision Matrix

| Request Pattern | Memory Needs | Latency Priority | Cost Sensitivity | Recommended Environment |
| --- | --- | --- | --- | --- |
| High-throughput API (>10 req/s sustained) | Durable, queryable | Moderate | Low | Node.js + Postgres/Supabase |
| Bursty traffic (spikes, idle periods) | Session-scoped or managed | Moderate | High | Vercel/Netlify Functions |
| Real-time chat/voice (<100ms target) | Minimal or cached | Critical | Moderate | Cloudflare Workers |
| Long workflows (>30s, multi-agent) | Durable, shareable | Low | Low | Node.js (Kubernetes/ECS) |
| Frontend-integrated (Next.js app) | Session or managed | Moderate | High | Next.js API routes (Vercel) |
| Multi-region global service | Distributed or replicated | Critical | Moderate | Cloudflare Workers + R2/KV |

## Building Your First Production Agent

### Quick Start (Prototype to MVP)
1. **Scaffold the project**: `npm create voltagent-app@latest` gives you agents, workflows, VoltOps-ready observability, and scripts for dev/lint/test.
2. **Wire your model**: Choose from 30+ Vercel AI SDK providers (OpenAI, Anthropic, Google, Mistral, Groq, xAI, etc.) and switch via configuration ([Providers & Models](https://voltagent.dev/docs/getting-started/providers-models/)).
3. **Add domain knowledge**: Leverage retrievers and memory adapters to persist conversations and surface relevant context ([Working Memory](https://voltagent.dev/docs/agents/memory/working-memory/)).
4. **Expose tools and workflows**: Register tools and workflows in VoltAgent so they appear in REST APIs, VoltOps console, and (optionally) MCP servers ([API Overview](https://voltagent.dev/docs/api/overview/), [MCP Server](https://voltagent.dev/docs/agents/mcp/mcp-server/)).
5. **Instrument observability**: Run locally with automatic VoltOps tracing; add `VOLTAGENT_PUBLIC_KEY`/`VOLTAGENT_SECRET_KEY` for remote telemetry, exports, and managed memory.

### Production Hardening Checklist
- **Error handling**: Wrap tool calls in try/catch, define retry policies for transient failures, implement circuit breakers for flaky APIs.
- **Guardrails**: Add input validation (prompt injection, PII detection), output filters (profanity, hallucination checks), and rate limits ([Guardrails](https://voltagent.dev/docs/guardrails/overview/)).
- **Load testing**: Simulate peak traffic with `k6`, `Artillery`, or `Locust`; measure p95 latency, error rates, and token consumption under load.
- **Model fallback**: Configure primary/fallback provider pairs (e.g., GPT-4 → GPT-3.5-turbo on timeout); test graceful degradation.
- **Cost controls**: Set per-user/per-session budgets in VoltOps, cache expensive embeddings/retrievals, use smaller models for simple tasks.
- **Security review**: Rotate API keys, validate user inputs, sanitize tool outputs, audit memory access patterns, enforce least-privilege IAM roles.
- **Monitoring & alerts**: Define SLOs (e.g., 95% of requests < 2s, error rate < 1%), configure VoltOps alerts, integrate with PagerDuty/Slack.
- **Versioning & rollback**: Tag agent/prompt versions in source control, use VoltOps prompt management for instant rollback, maintain eval suites for regression checks.
- **Compliance & auditing**: Log all user interactions, anonymize PII in traces, configure data retention policies, generate audit trails for regulated industries.

## Team Collaboration & Governance

As agent fleets grow, coordinated development and policy enforcement become critical. VoltAgent + VoltOps provide patterns for scaling teams while maintaining quality and compliance.

### Prompt Governance
- **Source control first**: Store instructions, system prompts, and few-shot examples in `.md` or `.txt` files under version control. Review changes via PRs with clear diffs.
- **VoltOps prompt store**: Upload production prompts to VoltOps for A/B testing, staged rollouts, and instant rollback without redeployment ([Agent Prompts](https://voltagent.dev/docs/agents/prompts/)).
- **Dynamic overrides**: Let agents fetch instructions from VoltOps at runtime; tag versions, track usage per variant, compare eval scores across iterations.
- **Collaboration workflow**: Prompt engineers draft in VoltOps, engineers merge to source control after evals pass, ops team manages production versions.

### Tool Schema Documentation
- **Treat tools as API contracts**: Every `createTool` call should include `description`, `parameters` (Zod schema), and `purpose` fields. Document edge cases, rate limits, and failure modes.
- **Shared toolkit registry**: Organize tools into reusable kits (e.g., `@company/payments-tools`, `@company/crm-tools`); publish to internal npm registry for cross-team reuse.
- **MCP exposure**: Tools automatically appear in MCP servers, making them discoverable to Claude Desktop, Cline, and other MCP clients ([MCP Server](https://voltagent.dev/docs/agents/mcp/mcp-server/)).
- **Changelog discipline**: Version tool schemas, deprecate old signatures gracefully, and notify consumers of breaking changes via release notes.

### Context & Session Standards
- **OperationContext conventions**: Standardize metadata keys (e.g., `userId`, `sessionId`, `tenantId`, `traceId`) so tools, hooks, and workflows access consistent data ([Operation Context](https://voltagent.dev/docs/agents/context/)).
- **Audit trails**: Pass `userId` and `requestId` through all agent invocations; VoltOps traces automatically correlate sessions for compliance reviews.
- **Cost attribution**: Tag contexts with `teamId` or `projectId`; export VoltOps data to BI tools for chargeback accounting.
- **Access control**: Inject user permissions into context; tools check `context.user.role` before executing sensitive operations.

### Cost Management & Budgets
- **Per-agent quotas**: Set monthly token limits per agent in VoltOps; block requests once exceeded, alert finance team.
- **Team dashboards**: Aggregate spend by team, project, or user cohort; identify cost outliers (inefficient prompts, runaway loops).
- **Model tiering**: Route simple queries to fast/cheap models (GPT-3.5, Gemini Flash), reserve expensive models (GPT-4, Claude Opus) for complex reasoning or guardrail failures.
- **Caching strategy**: Store frequent tool results, embeddings, and retrieval hits in Redis/KV; reduce redundant LLM calls by 30-50%.

### Compliance & Data Governance
- **PII handling**: Mask or tokenize sensitive data before sending to LLMs; use guardrails to detect accidental PII leakage in outputs.
- **Data retention**: Configure VoltOps to auto-delete traces after 30/90 days per GDPR/CCPA; export audit logs to immutable storage for regulated industries.
- **Right to erasure**: Implement memory purge APIs; when a user requests deletion, wipe their sessions from Postgres/Supabase and VoltOps.
- **Access logs**: Track who viewed session replays, modified prompts, or accessed user memory; integrate VoltOps with SIEM for security monitoring.
- **Third-party SLAs**: Document which LLM providers process data, where models run (US/EU/multi-region), and data residency guarantees—essential for enterprise procurement.

## Best Practices for Agent Teams

- **Keep instructions source-controlled**: Combine dynamic instructions with VoltOps prompt management for collaboration and auditing ([Agent Prompts](https://voltagent.dev/docs/agents/prompts/)).
- **Use context maps intentionally**: Share metadata, session IDs, and workflow state via `OperationContext` so tools and hooks stay in sync ([Operation Context](https://voltagent.dev/docs/agents/context/)).
- **Version tools & workflows**: Group related tools into toolkits, attach schemas, and document purpose fields so supervisors and MCP clients expose clear capabilities.
- **Plan for observability from day one**: Even in development, VoltOps gives you live traces and logs—do not wait for production outages to add telemetry.
- **Automate quality checks**: Combine guardrails, automated evals, and VoltOps session replays to catch regressions before they reach users.
- **Mind platform-specific limits**: When deploying to edge/serverless, choose adapters (InMemory or REST-based) that respect the target's runtime constraints ([Cloudflare Workers](https://voltagent.dev/docs/deployment/cloudflare-workers/), [Netlify Functions](https://voltagent.dev/docs/deployment/netlify-functions/)).
- **Optimize for cost**: Cache aggressively, use smaller models for routine tasks, set budget alerts, and analyze token usage per agent/workflow in VoltOps.
- **Design for failure**: Implement retries with exponential backoff, fallback to cheaper models on timeout, and surface errors gracefully to users.
- **Test with production data**: Clone anonymized sessions from VoltOps for offline evals; replay real user interactions to validate prompt changes.
- **Document agent capabilities**: Maintain a README or wiki listing each agent's purpose, tools, memory strategy, and example use cases—onboard new team members faster.

## Who This Ecosystem Serves

- **New builders** get batteries-included scaffolding, sensible defaults, and VoltOps' visual feedback loop to understand agent behaviour quickly.
- **Experienced teams** keep full control via TypeScript APIs, Nx/Lerna workspaces, server plugins, and OpenTelemetry pipelines, while adopting managed components selectively.
- **Enterprise & regulated use cases** benefit from multi-agent orchestration, audit-ready logs, VoltOps replays, guardrail enforcement, and deployment flexibility across VPCs, serverless, or hybrid topologies.

## Learn By Example: 59+ Production Patterns

Browse real implementations across industries and use cases in the [examples gallery](https://github.com/voltagent/voltagent/tree/main/examples):

**By Domain:**
- **Commerce & Support**: WhatsApp bots, recipe generators, customer service agents
- **Content & Media**: YouTube-to-blog converters, ad creators with BrowserBase, content moderators
- **Knowledge & Research**: Research assistants, GitHub analyzers, RAG chatbots with Chroma/Pinecone/Qdrant
- **Automation**: MCP ecosystems (Zapier, Google Drive, Hugging Face, Composio, Peaka)
- **Voice & Real-time**: ElevenLabs, OpenAI, xsAI voice agents with streaming

**By Technology:**
- **Model Providers**: OpenAI, Anthropic, Google, Groq, Mistral, Amazon Bedrock, xAI
- **Memory**: Postgres, Supabase, Turso/LibSQL, Managed (VoltOps)
- **Deployment**: Next.js, Cloudflare Workers, Netlify Functions, Nuxt
- **Advanced**: Guardrails, evals, hooks, JWT auth, dynamic prompts, thinking tools

Each example includes complete source code, setup instructions, and VoltOps configuration.

## Continue Exploring

- **[Quick Start Guide](https://voltagent.dev/docs/quick-start/)**: Build your first agent in 5 minutes
- **[VoltAgent Blog](https://voltagent.dev/blog/)**: Latest patterns, case studies, and best practices
- **[Discord Community](https://s.voltagent.dev/discord)**: Get help, share projects, discuss architecture
- **[GitHub Repository](https://github.com/voltagent/voltagent)**: Star, fork, contribute
- **[Documentation](https://voltagent.dev/docs/)**: Deep dive into every feature

---

**VoltAgent and VoltOps form a cohesive platform that accelerates every step of professional AI agent development—from the first "hello world" conversation to monitored, reliable agent fleets in production. Everything you need is here. Start building today.**
