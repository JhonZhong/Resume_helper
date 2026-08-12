---
name: resume-helper
description: Extract evidence-based technical experience and resume-worthy highlights from a user-selected software, hardware, research, or engineering project, then produce concise Chinese resume project content. Use when a user asks to analyze a local project or repository, infer their likely responsibilities, identify the technology stack, summarize project background/methods/results, quantify contributions, rewrite a project for a resume, or generate project experience bullets. Always obtain the project dates from the user before producing the final entry.
---

# Resume Helper

Turn a selected project into concise, credible Chinese resume content. Inspect available project evidence, infer a defensible role, and emphasize the user's actions, technical difficulty, and measurable impact.

## Workflow

### 1. Confirm the project and dates

- Identify the project selected by the user. If the selection is ambiguous, ask which project or directory to analyze.
- Always ask the user for the project start and end dates before producing the final entry. Prefer `YYYY.MM-YYYY.MM`; accept `至今` for an ongoing project.
- Do not infer dates from file timestamps, Git history, dependency versions, or documentation.
- If a selected project is accessible locally, inspect it directly. If it is not accessible, request a repository link, files, or a brief description.
- Ask only for information that cannot be established safely from the available evidence.

### 2. Collect project evidence

Inspect the most informative sources first:

1. README files, architecture documents, reports, requirements, and deployment instructions.
2. Dependency manifests, build files, container files, and environment configuration.
3. Source layout, entry points, API routes, schemas, protocol definitions, tests, and CI configuration.
4. Git history or contribution evidence when available and relevant.

Extract:

- Project problem, intended users or scenario, and overall architecture.
- Languages, frameworks, databases, middleware, protocols, engineering techniques, and named concepts actually used.
- Major modules and end-to-end data or control flows.
- Reliability, security, performance, automation, visualization, deployment, or testing work.
- Verifiable outcomes and useful scale indicators such as module count, modes, endpoints, supported scenarios, test coverage, latency, throughput, or data volume.

Treat documentation claims and implementation evidence separately. Prefer implementation evidence when they conflict.

### 3. Infer the responsibility

Infer a short responsibility label from the breadth and depth of the work, such as `核心开发者（全栈）`, `后端开发`, `算法开发`, `嵌入式开发`, or `项目负责人`.

- Use `核心开发者` only when evidence shows ownership of central modules or an end-to-end path.
- Use `项目负责人` only when leadership, planning, coordination, or overall ownership is evidenced.
- Do not invent team size, leadership, business ownership, or personal contribution.
- If repository evidence cannot distinguish the user's contribution from the team's work, phrase bullets around implemented modules and ask for clarification only when authorship materially changes the result.

### 4. Select the technology stack

List only technologies supported by files, code, configuration, or the user's statements. Cover applicable categories without printing category labels:

- Languages: C/C++, Java, Python, JavaScript/TypeScript, and others.
- Frameworks: Vue, React, Flask, Spring, LangChain, LangGraph, and others.
- Databases: MySQL, MongoDB, PostgreSQL, and others.
- Middleware: Redis, Kafka, RabbitMQ, and others.
- Techniques and concepts: RAG, MCP, Harness, computer vision, distributed systems, and others.
- Protocols and interfaces: TCP/IP, HTTP, WebSocket, SSL/TLS, MQTT, JSON, Protobuf, and others.

Normalize common names (`Vue`, `React`, `C++`, `PostgreSQL`, `SSL/TLS`). Omit generic tools that add little signal unless they are central to the project. Order items by relevance to the user's contribution.

### 5. Draft the introduction

Write one coherent paragraph of no more than 100 Chinese characters, excluding punctuation and Latin technology names when exact counting is impractical. Allocate the content approximately as follows:

- 20%: project background or problem.
- 30%: overall method or architecture.
- 50%: achieved capabilities or effects.

State demonstrated capabilities rather than unsupported business impact. Do not repeat the full technology stack.

### 6. Draft three or four highlights

Write 3-4 bullets, each no more than 80 Chinese characters. Give each bullet a short descriptive label followed by a colon.

Use this structure where possible:

`action + technical object or method + problem solved + measurable result or scope`

- Lead with strong, accurate verbs such as `设计`, `实现`, `重构`, `优化`, `搭建`, `封装`, or `主导`.
- Focus on what the user did, not a generic feature inventory.
- Prefer specific mechanisms and engineering trade-offs over adjectives.
- Use numbers only when evidenced or directly derivable. Counts of implemented modules, modes, protocols, callbacks, or supported scenarios are valid quantitative signals.
- Never fabricate percentages, latency, throughput, user counts, accuracy, cost savings, or team size.
- Avoid weak phrases such as `参与了`, `负责相关工作`, `大幅提升`, or `效果良好` unless made concrete.
- Keep the bullets complementary: architecture/core implementation, difficult mechanism, quality/performance/security, and end-to-end outcome are useful dimensions.

### 7. Verify before answering

Check that:

- The project dates came from the user.
- Every named technology and protocol has evidence.
- The responsibility label is defensible.
- The introduction and every bullet satisfy their length limits.
- There are exactly 3 or 4 non-overlapping highlights.
- All metrics are sourced or directly derivable.
- No confidential values, credentials, internal hosts, or sensitive implementation details appear.

If evidence is weak, use conservative wording and briefly note any important assumption after the formatted entry.

## Output Format

Return the final entry in Chinese using exactly this structure. Do not add a separate analysis section.

For a complete rendered example, read [RESUME_EXAMPLE.md](RESUME_EXAMPLE.md). Use it only as a format and writing-quality reference; never copy its project facts into another user's output.

```text
项目名称：<名称>    项目职责：<职责>    项目时间：<YYYY.MM-YYYY.MM/至今>
技术栈：<技术1>、<技术2>、<技术3>……
项目介绍：<不超过100字；背景、方法、效果约为2:3:5>
项目亮点：
- <亮点标题>：<用户行动、技术方法、解决的问题与结果；整点不超过80字>
- <亮点标题>：<用户行动、技术方法、解决的问题与结果；整点不超过80字>
- <亮点标题>：<用户行动、技术方法、解决的问题与结果；整点不超过80字>
```

Add a fourth bullet only when it introduces a distinct, evidence-backed contribution.
