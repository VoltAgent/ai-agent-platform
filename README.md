# VoltAgent AI Agent Platform

<div align="center">
<a href="https://github.com/VoltAgent/voltagent/">
<img width="1800" alt="VoltAgent Platform" src="https://github.com/user-attachments/assets/9259e833-0f5c-4eb6-8cc7-4e6930cc27e1" />
</a>
</div>

<br/>

## What Are AI Agents?

AI agents wrap Large Language Models (LLMs) with tools, memory, and reasoning capabilities. Unlike chatbots that respond to single prompts, agents:

- Plan multi-step problem solutions
- Call APIs, databases, and external services via tools
- Persist context across conversations and sessions
- Coordinate with other agents
- Evaluate and adapt through feedback loops


### Why Building AI Agents Takes Time

<br/> 
<div align="center">
<a href="https://github.com/VoltAgent/voltagent/">
<img width="800" height="500" alt="diagram" src="https://github.com/user-attachments/assets/825c64ff-4033-4b0b-a8eb-192352633fd9" />
</a>
</div>

<br/> 

Shipping agents means solving:

- **Orchestration**: Coordinating agents, tools, and workflows
- **Memory**: Persisting conversation history and semantic context
- **Retrieval**: Grounding responses in proprietary data (RAG)
- **Safety**: Input validation, output filtering, guardrails
- **Observability**: Trace visualization, cost tracking, debugging
- **Deployment**: Scaling across edge, serverless, and server environments
- **Monitoring**: Performance, quality, and cost analytics

Building this from scratch requires significant engineering effort.

## What You Need to Build AI Agents

Building production AI agents requires solving 11 categories of infrastructure:

### Core Runtime

The foundation of any agent system. You need a runtime that manages agent lifecycle, coordinates LLM calls, and handles responses safely without reinventing the wheel for every project.

- Agent orchestration engine
- LLM provider abstraction (OpenAI, Anthropic, Google, etc.)
- Streaming response handling
- Cancellation & timeout controls
- Type-safe agent definitions

📖 [Agent Overview docs ↗](https://voltagent.dev/docs/agents/overview/)

### Tools & Integration

Agents become useful when they can interact with external systems. You need a framework to define tools safely, handle API failures gracefully, and connect to existing services without writing custom adapters for each one.

- Tool/function calling framework
- API integration patterns
- Error handling & retries
- Rate limiting & backpressure
- Model Context Protocol (MCP) support

📖 [Tools docs ↗](https://voltagent.dev/docs/agents/tools/) | [MCP docs ↗](https://voltagent.dev/docs/agents/mcp/)

### Multi-Agent Coordination

Complex problems require teams of specialized agents working together. You need a way to route tasks to the right agent, share context between them, and coordinate their work without building custom message passing infrastructure.

- Sub-agent orchestration
- Task routing & delegation
- Context sharing across agents
- Parallel execution & streaming

📖 [Sub-agents docs ↗](https://voltagent.dev/docs/agents/sub-agents/)

### Memory & State

Agents need to remember past conversations and learn from interactions. You need persistent storage that lets agents recall context, search historical data semantically, and keep each user's information separate and secure.

- Conversation history storage
- Session management
- Semantic search & recall
- Multi-user isolation
- Database adapters (Postgres, Supabase, etc.)

📖 [Memory Overview docs ↗](https://voltagent.dev/docs/agents/memory/overview/)

### Workflow Automation

Real business processes involve multiple steps, branching logic, and human approvals. You need a workflow engine that can orchestrate complex automations, pause for human input, and recover from failures without starting over.

- Multi-step pipelines
- Conditional logic & branching
- Parallel execution
- Human-in-the-loop gates
- Suspend/resume capabilities

📖 [Workflows docs ↗](https://voltagent.dev/docs/workflows/overview/)

### Retrieval & RAG

Agents need to ground their responses in your company's data, not just general knowledge. You need retrieval systems that can search your documents semantically, combine multiple search strategies, and work with any vector database.

- Vector store integrations
- Document chunking & embedding
- Semantic search
- Hybrid search strategies
- Custom retriever interfaces

📖 [RAG Overview docs ↗](https://voltagent.dev/docs/rag/overview/)

### Safety & Compliance

Production agents handle sensitive data and user inputs you can't fully control. You need guardrails that block malicious prompts, filter harmful outputs, detect PII leaks, and prevent abuse before problems reach users.

- Input validation & sanitization
- Output filtering & moderation
- Prompt injection detection
- PII detection & masking
- Rate limiting & abuse prevention

📖 [Guardrails docs ↗](https://voltagent.dev/docs/guardrails/overview/)

### Observability & Debugging

You can't fix what you can't see. When agents misbehave, you need to trace every decision, replay sessions exactly as users experienced them, track costs per interaction, and identify performance bottlenecks in real-time.

- Distributed tracing (OpenTelemetry)
- Real-time logging
- Cost tracking per agent/session/user
- Session replay capability
- Error diagnostics & stack traces
- Performance metrics & bottleneck detection

📖 [VoltOps Platform docs ↗](https://voltagent.dev/docs/observability/developer-console/)

### Quality Assurance

Manual testing doesn't scale for AI systems. You need automated evaluations that measure accuracy and hallucination rates, catch regressions in CI/CD pipelines, and track quality trends as you iterate on prompts and models.

- Automated evaluation framework
- Scorer registry (accuracy, relevance, safety)
- Dataset management
- A/B testing infrastructure
- Regression detection
- CI/CD integration

📖 [Evaluations docs ↗](https://voltagent.dev/docs/evals/overview/)

### Deployment & Scale

Different use cases demand different infrastructure. You need deployment options for traditional servers, serverless platforms, and edge networks—plus the ability to scale horizontally without rewriting your agent code.

- Server adapters (Node.js, serverless, edge)
- Horizontal scaling support
- Load balancing
- Docker/Kubernetes configs
- Environment-specific optimization

📖 [Deployment docs ↗](https://voltagent.dev/docs/deployment/overview/)

### Team Collaboration

As teams grow, coordination becomes critical. You need prompt version control for safe deployments, cost tracking by team or project, audit logs for compliance, and role-based access to control who can modify what.

- Prompt version control
- Cost attribution & budgets
- Audit trails & compliance logs
- Role-based access control
- Shared dashboards & analytics

📖 [Operation Context docs ↗](https://voltagent.dev/docs/agents/context/)

Building and maintaining this requires expertise in distributed systems, LLM APIs, databases, observability, security, and DevOps.

## VoltAgent Platform

VoltAgent provides a TypeScript runtime (VoltAgent Core) and managed observability layer (VoltOps).

### Quick Start

Create a new VoltAgent project in seconds:

```bash
npm create voltagent-app@latest
```

Example agent setup:

```typescript
import { VoltAgent, Agent, Memory } from "@voltagent/core";
import { LibSQLMemoryAdapter } from "@voltagent/libsql";
import { honoServer } from "@voltagent/server-hono";
import { openai } from "@ai-sdk/openai";

const memory = new Memory({
  storage: new LibSQLMemoryAdapter({ url: "file:./.voltagent/memory.db" }),
});

const agent = new Agent({
  name: "my-agent",
  instructions: "A helpful assistant",
  model: openai("gpt-4o-mini"),
  tools: [weatherTool],
  memory,
});

new VoltAgent({
  agents: { agent },
  workflows: { expenseApprovalWorkflow },
  server: honoServer(),
});
```

Run your agent:

```bash
npm run dev
```

📖 [Quick Start Guide ↗](https://voltagent.dev/docs/quick-start/)

### Platform Components

```
┌──────────────────────────────────────────────────────┐
│              VoltAgent Platform                      │
│                                                      │
│  ┌────────────────────┐      ┌─────────────────────┐│
│  │   VoltAgent Core   │◄────►│      VoltOps        ││
│  │   (Open Source)    │      │  (Managed Layer)    ││
│  ├────────────────────┤      ├─────────────────────┤│
│  │ • Agents           │      │ • Visual Traces     ││
│  │ • Sub-agents       │      │ • Cost Tracking     ││
│  │ • Workflows        │      │ • Session Replays   ││
│  │ • Tools & MCP      │      │ • Prompt Versioning ││
│  │ • Memory           │      │ • Eval Dashboards   ││
│  │ • Guardrails       │      │ • Managed Memory    ││
│  │ • RAG/Retrieval    │      │ • Dataset Management││
│  │ • Evals & Scorers  │      │ • OTLP Exports      ││
│  │ • Multi-modal      │      │ • Team Collaboration││
│  └────────────────────┘      └─────────────────────┘│
└──────────────────────────────────────────────────────┘
```

## Platform Capabilities

VoltAgent provides solutions for 11 categories of agent infrastructure:

### ✅ Core Agent Runtime

You need type-safe agent definitions to catch errors early, a way to change prompts without redeploying, support for multiple LLM providers so you're not locked in, streaming for real-time responses, and the ability to cancel long operations.

**VoltAgent provides:** `Agent` class with TypeScript types and Zod validation, 30+ LLM providers via Vercel AI SDK (OpenAI, Anthropic, Google, Mistral, Groq, xAI, Ollama), dynamic instructions from code or VoltOps prompt store, native streaming with backpressure handling, and graceful cancellation with timeout controls.

**📖 [Agent Overview docs ↗](https://voltagent.dev/docs/agents/overview/)**

### ✅ Tool Integration & External APIs

You need tools with type validation to prevent bad inputs, hooks to add logging and auth checks, error handling with retries when APIs fail, rate limiting to avoid hitting API quotas, and MCP support to connect to existing integrations.

**VoltAgent provides:** `createTool` with Zod schemas and auto-generated OpenAPI specs, tool registries and reusable toolkits, before/after hooks for logging/auth/retries, Model Context Protocol (MCP) client for 100+ integrations (GitHub, Google Drive, Zapier), and ability to expose your tools as MCP servers for Claude Desktop and Cline.

**📖 [Tools docs ↗](https://voltagent.dev/docs/agents/tools/) | [MCP docs ↗](https://voltagent.dev/docs/agents/mcp/)**

### ✅ Multi-Agent Orchestration

You need to split complex tasks across specialized agents, route work to the right agent, share memory between agents, and track which agent spent what.

**VoltAgent provides:** Supervisor patterns with `agent.run()` nesting, sub-agent streaming and partial results, shared memory across agent hierarchies, and cost attribution per sub-agent in VoltOps.

**📖 [Sub-agents docs ↗](https://voltagent.dev/docs/agents/sub-agents/)**

### ✅ Memory & Persistence

You need to remember past conversations, search old messages to recall facts, resume sessions without losing context, and keep each user's data separate.

**VoltAgent provides:** Pluggable memory adapters (InMemory, LibSQL, Postgres, Supabase, Managed via VoltOps), working memory for short-term context, semantic search over conversation history, and thread/session management with user isolation.

**📖 [Memory Overview docs ↗](https://voltagent.dev/docs/agents/memory/overview/)**

### ✅ Workflow Automation

You need to run multiple steps in order or at the same time, branch based on conditions, pause for human approval, and recover from failures without starting over.

**VoltAgent provides:** Workflow engine with `andThen`, `andAgent`, `andAll`, `andWhen`, `andRace` steps, suspend/resume for human approval gates, REST API execution with progress streaming, and workflow versioning with replay.

**📖 [Workflows docs ↗](https://voltagent.dev/docs/workflows/overview/)**

### ✅ Retrieval & RAG

You need to search your documents semantically, combine keyword and vector search, chunk documents properly, and switch between vector databases without rewriting code.

**VoltAgent provides:** Retriever abstraction for Chroma, Pinecone, and Qdrant, custom retriever interfaces, embedding generation via AI SDK, and retrieval step tracing in VoltOps.

**📖 [RAG Overview docs ↗](https://voltagent.dev/docs/rag/overview/)**

### ✅ Safety & Guardrails

You need to validate user inputs to block malicious prompts, filter outputs to prevent harmful content, detect prompt injection, mask personal information, and enforce rate limits.

**VoltAgent provides:** Input/output guardrail decorators, prompt injection detection, stream-friendly moderation, and policy violation logging in VoltOps.

**📖 [Guardrails docs ↗](https://voltagent.dev/docs/guardrails/overview/)**

### ✅ Observability & Debugging

You need to see what your agent did step-by-step, track token costs per agent or user, replay sessions to debug issues, and test prompt changes safely before deploying.

**VoltAgent provides:** VoltOps Console with visual trace timelines and waterfall views, per-agent/session/user token and cost breakdown, session replay with exact state/memory/tool results, OpenTelemetry export to VoltOps/DataDog/Grafana via OTLP, and prompt management for versioning, A/B testing, and rollback.

**📖 [VoltOps Platform docs ↗](https://voltagent.dev/docs/observability/developer-console/)**

### ✅ Quality Assurance & Testing

You need to run automated tests on your agents, measure accuracy and hallucination rates, catch regressions in CI/CD, and track quality over time.

**VoltAgent provides:** `@voltagent/evals` framework for offline and live evaluations, prebuilt scorers (accuracy, relevance, hallucination, PII leakage), custom scorer development, VoltOps eval dashboards with pass/fail trends, and CI pipeline integration.

**📖 [Evaluations docs ↗](https://voltagent.dev/docs/evals/overview/)**

### ✅ Deployment Flexibility

You need to deploy to Node.js servers, serverless platforms like Vercel, edge networks like Cloudflare Workers, or mix on-prem and cloud—without rewriting code.

**VoltAgent provides:** `@voltagent/server-hono` for standalone Node servers, `@voltagent/serverless-hono` for Vercel/Netlify/AWS Lambda, edge-compatible adapters for Cloudflare Workers, Docker/Kubernetes deployment guides, and environment-specific memory strategies.

**📖 [Deployment docs ↗](https://voltagent.dev/docs/deployment/overview/)**

### ✅ Team Collaboration & Governance

You need to version prompts before deploying, track costs by team or project, keep audit logs for compliance, handle PII properly for GDPR/CCPA, and control which agents can use which tools.

**VoltAgent provides:** Prompt version control in source and VoltOps store, cost attribution tags (team, project, user), audit trails with user/session correlation, PII handling and data retention policies, and role-based tool access via OperationContext.

**📖 [Operation Context docs ↗](https://voltagent.dev/docs/agents/context/)**

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
| **Deployment** | Configure servers, handle secrets, set up monitoring, write Dockerfiles | Hono server, serverless adapters, K8s examples provided |
| **Team collaboration** | Build prompt editor, cost dashboards, audit log viewer | VoltOps console with team views, cost attribution, session replays |
| **Estimated time to production** | Significant engineering effort | 1-2 weeks (prototype to MVP) |

### Why Teams Choose VoltAgent

Here's how VoltAgent fits different use cases:

| What You're Building | Why VoltAgent Fits |
| --- | --- |
| **First AI agent prototype** | `npm create voltagent-app@latest` scaffolds everything in 60 seconds. Pick your model (OpenAI, Anthropic, Google, etc.), chat with your agent via VoltOps console, iterate instantly. |
| **Production customer support bot** | Durable memory (Postgres/Supabase), conversation history, guardrails for safety, full observability. Scale horizontally, integrate with existing auth, deploy to your VPC. |
| **Multi-agent research system** | Sub-agent orchestration, typed workflows, parallel execution, streaming results. Each specialist agent gets its own memory and tools while the supervisor coordinates. |
| **Enterprise automation** | Compliance-ready audit trails, role-based access control, PII detection, cost budgets, prompt governance. Deploy on-prem or hybrid cloud with full control. |
| **Voice/real-time agents** | ElevenLabs/OpenAI voice adapters, WebSocket streaming, edge deployment (Cloudflare Workers), <100ms latency. Cancellation and error recovery. |

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

## When to Use Each Capability

| Scenario | Recommended Capability | Why it helps | Example | VoltOps Features |
| --- | --- | --- | --- | --- |
| Prototype a conversational agent | `npm create voltagent-app@latest` scaffold + default agent | Instant project setup with VoltAgent server, VoltOps console link, and example workflow ([Quick Start ↗](https://voltagent.dev/docs/quick-start/)) | [base ↗](https://github.com/voltagent/voltagent/tree/main/examples/base) | Auto-tracing, live logs |
| Connect to APIs or services | `createTool`, toolkits, Model Context Protocol client | Type-safe tools with lifecycle hooks and MCP connectivity ([Tools ↗](https://voltagent.dev/docs/agents/tools/), [MCP Client ↗](https://voltagent.dev/docs/agents/mcp/)) | [with-tools ↗](https://github.com/voltagent/voltagent/tree/main/examples/with-tools), [with-mcp ↗](https://github.com/voltagent/voltagent/tree/main/examples/with-mcp) | Tool call traces, latency tracking |
| Coordinate multiple specialists | Supervisor + sub-agents | Route tasks, stream outputs, and maintain context across a team of agents ([Sub-agents ↗](https://voltagent.dev/docs/agents/sub-agents/)) | [with-subagents ↗](https://github.com/voltagent/voltagent/tree/main/examples/with-subagents), [with-youtube-to-blog ↗](https://github.com/voltagent/voltagent/tree/main/examples/with-youtube-to-blog) | Agent hierarchy view, sub-agent cost attribution |
| Retain knowledge across sessions | Memory adapters (InMemory, LibSQL, Postgres, Supabase, Managed) | Switch storage without rewriting logic, add semantic recall or working memory ([Memory Overview ↗](https://voltagent.dev/docs/agents/memory/overview/)) | [with-postgres ↗](https://github.com/voltagent/voltagent/tree/main/examples/with-postgres), [with-working-memory ↗](https://github.com/voltagent/voltagent/tree/main/examples/with-working-memory) | Memory queries in traces, session replays |
| Ground responses in your data | Retriever integrations + RAG examples | Bring vector stores (Chroma, Pinecone, Qdrant) or custom retrievers into agents ([RAG Overview ↗](https://voltagent.dev/docs/rag/overview/)) | [with-rag-chatbot ↗](https://github.com/voltagent/voltagent/tree/main/examples/with-rag-chatbot), [with-chroma ↗](https://github.com/voltagent/voltagent/tree/main/examples/with-chroma) | Retrieval step inspection, source attribution |
| Automate complex flows | Workflow engine steps (`andThen`, `andAgent`, `andAll`, `andWhen`, `andRace`) | Build multi-step automation with validation, human-in-the-loop, and REST execution ([Workflows ↗](https://voltagent.dev/docs/workflows/overview/)) | [with-workflow ↗](https://github.com/voltagent/voltagent/tree/main/examples/with-workflow) | Step-by-step visualization, conditional branch traces |
| Enforce policy & safety | Input/output guardrails | Stream-friendly moderation, prompt injection protection, validation ([Guardrails ↗](https://voltagent.dev/docs/guardrails/overview/)) | [with-guardrails ↗](https://github.com/voltagent/voltagent/tree/main/examples/with-guardrails) | Policy violation alerts, blocked request logs |
| Observe production behaviour | VoltOps console, OpenTelemetry exporters, managed dashboards | Live traces, cost analytics, replay runs, integrate with VoltOps or custom OTLP targets ([Logging & Observability ↗](https://voltagent.dev/docs/observability/logging/), [Vercel AI Exporter ↗](https://voltagent.dev/docs/integrations/vercel-ai/)) | [with-voltagent-exporter ↗](https://github.com/voltagent/voltagent/tree/main/examples/with-voltagent-exporter) | Full trace timeline, token/cost breakdown, replay debugging |
| Run automated evaluations | `@voltagent/evals` + VoltOps scoring | Offline/online tests, scorer registry, CI gates, VoltOps run summaries ([Evaluations ↗](https://voltagent.dev/docs/evals/overview/)) | [with-offline-evals ↗](https://github.com/voltagent/voltagent/tree/main/examples/with-offline-evals), [with-live-evals ↗](https://github.com/voltagent/voltagent/tree/main/examples/with-live-evals) | Eval run dashboards, pass/fail metrics, regression detection |
| Deploy reliably | Hono server adapters, serverless runners | Ship to Node servers, Cloudflare Workers, Netlify Functions, or hybrid setups ([Deployment Overview ↗](https://voltagent.dev/docs/deployment/overview/)) | [with-nextjs ↗](https://github.com/voltagent/voltagent/tree/main/examples/with-nextjs), [with-cloudflare-workers ↗](https://github.com/voltagent/voltagent/tree/main/examples/with-cloudflare-workers) | Production traces, per-environment cost tracking |

## Observability & Monitoring with VoltOps

VoltOps transforms agent development from black-box guesswork into data-driven iteration.

<div align="center">
<img alt="VoltOps Observability Overview" src="https://cdn.voltagent.dev/console/observability.png" />
</div>

<br/>

🎬 [Try Live Demo ↗](https://console.voltagent.dev/demo)

Here's how to leverage observability at each stage:

### Local Development
- **Auto-tracing**: Run `pnpm dev` and VoltOps automatically captures every agent invocation, tool call, and memory access—no configuration required.
- **Live logs**: Stream-friendly console output shows exactly what the agent is thinking, which tools it's calling, and how long each step takes.

  📖 [Logging docs ↗](https://voltagent.dev/docs/observability/logging/)
- **Instant feedback**: Spot prompt issues, inefficient tool chains, or memory misses in real-time before committing code.

### Production Monitoring
- **Trace timelines**: Visual waterfall view shows agent reasoning, tool latency, LLM response time, and total request duration. Identify bottlenecks at a glance.

  <div align="center">
  <img alt="VoltOps Traces" src="https://cdn.voltagent.dev/console/traces.png" />
  </div>

  <br/>

  📖 [Developer Console docs ↗](https://voltagent.dev/docs/observability/developer-console/)
- **Cost tracking**: Per-agent, per-session, and per-user token usage with real-time cost calculation. Set budget alerts and analyze spend by model, tool, or workflow step.

  <div align="center">
  <img alt="VoltOps Dashboard" src="https://cdn.voltagent.dev/console/dashboard.png" />
  </div>

  <br/>

- **Session replays**: Reproduce any user interaction by replaying the exact agent state, memory contents, and tool results. Debug edge cases and validate fixes.
- **Error diagnostics**: Stack traces, failed tool calls, guardrail blocks, and timeout events appear inline with full context—no more hunting through fragmented logs.

  <div align="center">
  <img alt="VoltOps Logs" src="https://cdn.voltagent.dev/console/logs.png" />
  </div>

  <br/>

### Quality Assurance
- **Evaluation dashboards**: Compare prompt versions, model choices, or tool configurations using `@voltagent/evals`. VoltOps aggregates pass/fail rates, scorer distributions, and regression indicators.

  📖 [Evaluations docs ↗](https://voltagent.dev/docs/evals/overview/)
- **Prompt versioning**: Manage instructions in VoltOps prompt store, A/B test variations, and roll back problematic changes without redeploying code.

  📖 [Agent Prompts docs ↗](https://voltagent.dev/docs/agents/prompts/)
- **Regression detection**: CI pipelines call offline evals; VoltOps flags runs where accuracy, latency, or cost metrics degrade beyond thresholds.

### Advanced Integration
- **OTLP exports**: Forward traces to VoltOps, DataDog, Grafana, or any OpenTelemetry-compatible backend for unified observability.

  📖 [Vercel AI Exporter docs ↗](https://voltagent.dev/docs/integrations/vercel-ai/)
- **Custom metrics**: Emit business-level events (e.g., "order_placed", "research_complete") alongside LLM telemetry for end-to-end analytics.
- **Managed memory inspection**: Query conversation history, working memory, and semantic recall state via VoltOps UI or REST API to validate knowledge retention.

  📖 [Managed Memory docs ↗](https://voltagent.dev/docs/agents/memory/managed-memory/)

**Actionable insights**: Use VoltOps data to optimize prompts (reduce token waste), refine tools (parallelize slow calls), tune memory (increase recall depth), and control costs (switch models or cache aggressively).

## Deployment Environments & Decision Guide

VoltAgent adapts to diverse hosting strategies. Choose based on request patterns, persistence needs, and operational constraints:

### Local Development
- **Best for**: Rapid iteration, debugging, full observability access.
- **Setup**: `npm create voltagent-app@latest`, then `pnpm dev` starts Hono server with hot reload.
- **Memory**: InMemory, LibSQL, or Postgres—test migration paths early.
- **Observability**: Automatic VoltOps tracing to local console; add `VOLTAGENT_PUBLIC_KEY` for remote dashboards.
- **Limitations**: Single-process, no load balancing.

### Node.js Servers (VPS, Kubernetes, ECS)
- **Best for**: High-throughput APIs, long-running workflows, complex sub-agent orchestration, full persistence.
- **Setup**: Deploy `@voltagent/server-hono` as a standalone Node process or Docker container.

  📖 [Deployment Overview docs ↗](https://voltagent.dev/docs/deployment/overview/)
- **Memory**: Postgres, Supabase, or Turso for durable, queryable history.

  📖 [with-postgres ↗](https://github.com/voltagent/voltagent/tree/main/examples/with-postgres) | [with-supabase ↗](https://github.com/voltagent/voltagent/tree/main/examples/with-supabase) | [with-turso ↗](https://github.com/voltagent/voltagent/tree/main/examples/with-turso)
- **Observability**: OTLP exporter sends traces to VoltOps or custom backends; leverage persistent storage for audit trails.
- **Scaling**: Horizontal scaling via load balancer; shared database ensures session continuity across instances.
- **Considerations**: Manage secrets (API keys, DB credentials) via env vars or secret managers; monitor memory/CPU usage for cost efficiency.

### Serverless Functions (Vercel, Netlify)
- **Best for**: Sporadic traffic, REST APIs, frontend-integrated agents, minimal ops overhead.
- **Setup**: Use `@voltagent/serverless-hono` adapter.

  📖 [with-nextjs ↗](https://github.com/voltagent/voltagent/tree/main/examples/with-nextjs) | [with-netlify-functions ↗](https://github.com/voltagent/voltagent/tree/main/examples/with-netlify-functions)
- **Memory**: InMemory (session-scoped) or REST-based managed memory (VoltOps) to avoid cold-start penalties.
- **Observability**: VoltOps remote tracing required since logs are ephemeral; session replays compensate for lack of persistent local logs.
- **Scaling**: Auto-scales with traffic; pay-per-invocation pricing favors bursty workloads.
- **Limitations**: 10-30s execution timeouts (check provider limits); no background jobs or multi-hour workflows; cold starts add 100-500ms latency.
- **Optimization**: Minimize bundle size, cache embeddings/prompts, use streaming responses to stay within time limits.

### Edge Runtimes (Cloudflare Workers)
- **Best for**: Global low-latency APIs, stateless agents, real-time interactions (chat, voice).
- **Setup**: `@voltagent/serverless-hono` with Cloudflare-compatible storage.

  📖 [with-cloudflare-workers ↗](https://github.com/voltagent/voltagent/tree/main/examples/with-cloudflare-workers) | [Cloudflare Workers docs ↗](https://voltagent.dev/docs/deployment/cloudflare-workers/)
- **Memory**: InMemory per-request or Durable Objects for distributed state; avoid heavy database calls (use KV/R2 for caching).
- **Observability**: VoltOps remote tracing mandatory; edge logs are minimal—rely on structured telemetry.
- **Scaling**: Massive horizontal scale, <50ms cold starts, geographic distribution.
- **Limitations**: No Node.js APIs (fs, child_process), strict CPU/memory caps, 1MB script size; skip heavy vector libraries or LLM SDKs.
- **Use cases**: Chat widgets, voice bots, content moderation—anything latency-sensitive and stateless.

## Building Your First Production Agent

### Quick Start (Prototype to MVP)
1. **Scaffold the project**: `npm create voltagent-app@latest` gives you agents, workflows, VoltOps-ready observability, and scripts for dev/lint/test.
2. **Wire your model**: Choose from 30+ Vercel AI SDK providers (OpenAI, Anthropic, Google, Mistral, Groq, xAI, etc.) and switch via configuration.

   📖 [Providers & Models docs ↗](https://voltagent.dev/docs/getting-started/providers-models/)
3. **Add domain knowledge**: Leverage retrievers and memory adapters to persist conversations and surface relevant context.

   📖 [Working Memory docs ↗](https://voltagent.dev/docs/agents/memory/working-memory/)
4. **Expose tools and workflows**: Register tools and workflows in VoltAgent so they appear in REST APIs, VoltOps console, and (optionally) MCP servers.

   📖 [API Overview docs ↗](https://voltagent.dev/docs/api/overview/) | [MCP Server docs ↗](https://voltagent.dev/docs/agents/mcp/mcp-server/)
5. **Instrument observability**: Run locally with automatic VoltOps tracing; add `VOLTAGENT_PUBLIC_KEY`/`VOLTAGENT_SECRET_KEY` for remote telemetry, exports, and managed memory.

### Production Hardening Checklist
- **Error handling**: Wrap tool calls in try/catch, define retry policies for transient failures, implement circuit breakers for flaky APIs.
- **Guardrails**: Add input validation (prompt injection, PII detection), output filters (profanity, hallucination checks), and rate limits.

  📖 [Guardrails docs ↗](https://voltagent.dev/docs/guardrails/overview/)
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
- **VoltOps prompt store**: Upload production prompts to VoltOps for A/B testing, staged rollouts, and instant rollback without redeployment.

  📖 [Agent Prompts docs ↗](https://voltagent.dev/docs/agents/prompts/)
- **Dynamic overrides**: Let agents fetch instructions from VoltOps at runtime; tag versions, track usage per variant, compare eval scores across iterations.
- **Collaboration workflow**: Prompt engineers draft in VoltOps, engineers merge to source control after evals pass, ops team manages production versions.

### Tool Schema Documentation
- **Treat tools as API contracts**: Every `createTool` call should include `description`, `parameters` (Zod schema), and `purpose` fields. Document edge cases, rate limits, and failure modes.
- **Shared toolkit registry**: Organize tools into reusable kits (e.g., `@company/payments-tools`, `@company/crm-tools`); publish to internal npm registry for cross-team reuse.
- **MCP exposure**: Tools automatically appear in MCP servers, making them discoverable to Claude Desktop, Cline, and other MCP clients.

  📖 [MCP Server docs ↗](https://voltagent.dev/docs/agents/mcp/mcp-server/)
- **Changelog discipline**: Version tool schemas, deprecate old signatures gracefully, and notify consumers of breaking changes via release notes.

### Context & Session Standards
- **OperationContext conventions**: Standardize metadata keys (e.g., `userId`, `sessionId`, `tenantId`, `traceId`) so tools, hooks, and workflows access consistent data.

  📖 [Operation Context docs ↗](https://voltagent.dev/docs/agents/context/)
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
- **Third-party SLAs**: Document which LLM providers process data, where models run (US/EU/multi-region), and data residency guarantees for enterprise procurement.



## Next Steps

- [Quick Start Guide ↗](https://voltagent.dev/docs/quick-start/): Build your first agent in 5 minutes
- [VoltAgent Blog ↗](https://voltagent.dev/blog/): Patterns, case studies, and implementation details
- [Discord Community ↗](https://s.voltagent.dev/discord): Help, project discussion, architecture questions
- [GitHub Repository ↗](https://github.com/voltagent/voltagent): Source code and contributions
- [Documentation ↗](https://voltagent.dev/docs/): API reference and guides
