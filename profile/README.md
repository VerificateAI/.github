<div align="center">

# 🛡️ Verificate

### The merge gate for AI-written code

**AI writes more code than anyone can carefully review — and it is fluent even when it is wrong.**
Verificate reads every AI-written change and blocks the ones that only *look* right: invented APIs, tests
written to pass, stubs dressed up as finished, secrets written to logs, and defects across the four ISO/IEC 5055
quality areas.

Nothing is executed. Your code is read and checked, never run.

<br>

[![GitHub Marketplace](https://img.shields.io/badge/GitHub_Marketplace-Verificate_Gate-2ea44f?logo=github&logoColor=white)](https://github.com/marketplace/actions/verificate-gate)
[![ISO/IEC 5055](https://img.shields.io/badge/ISO%2FIEC_5055-aligned_checks-2ea44f)](https://verificate.ai)
[![MCP](https://img.shields.io/badge/MCP-in--the--agent--loop-6f42c1)](https://github.com/VerificateAI/verificate-mcp-quickstart)
[![Benchmark](https://img.shields.io/badge/AI_self--review_0%2F6_%E2%86%92_Gate_6%2F6-2ea44f)](https://github.com/VerificateAI/verificate-mcp-quickstart)
[![Website](https://img.shields.io/badge/verificate.ai-000?logo=safari&logoColor=white)](https://verificate.ai)

**[Get started ↓](#-get-started) · [Try free at verificate.ai](https://verificate.ai) · [See the benchmark](https://github.com/VerificateAI/verificate-mcp-quickstart)**

</div>

---

## New in November 2026

- **Claude Haiku 5.5 reviewer.** On our frozen benchmark (12 cases × 3 runs), unsafe approvals fell from
  **6 in 36 to 0 in 36**, with every clean control still approved.
  [Method and numbers](https://github.com/VerificateAI/verificate-mcp-quickstart/blob/master/BENCHMARK_2026-11.md).
- **New deterministic vetoes** for secrets written to logs (10 languages) and invented Python standard-library calls.
- **One decision and a receipt on every verdict**: what was reviewed, by which model and prompt version, and what
  was not verified. A review that cannot cover the scope is never an approval.
- **Used hard in our own engineering:** 3,844 Gate reviews across 54 of our own projects (7 Oct – 10 Nov 2026),
  943 of them rejected and fixed.

## Why teams use it

AI coding tools now write most of the code that lands in pull requests, far more than human reviewers can read
line by line. The worst mistakes are the hardest to spot because the code is confident and plausible: a function
that does not exist, a test that cannot fail, a placeholder that looks finished. Verificate is the reviewer that
catches those, **before a human ever sees the change**.

- ✅ **Catches what AI review misses.** In our September benchmark, a frontier model asked to review code in a
  normal workflow caught **0 of 6** planted problems (a fake API and a self-passing test). Verificate caught
  **6 of 6**, every run, with zero false alarms on clean code.
- 🧭 **Anchored to a standard.** Checks aligned with the four ISO/IEC 5055 areas — security, reliability,
  performance efficiency, maintainability — and ISO/IEC 25010.
- 🔌 **Works in the loop and in CI.** Through the Model Context Protocol it reviews a change *before* your agent
  presents it; as a GitHub Action it blocks the merge until real problems are fixed.
- 🔒 **Read, never run.** Any agent, any IDE: the gate reads the change and returns a verdict. Submitted code is
  never executed.

## 🚀 Get started

**As a GitHub check** — add one file, and the next pull request gets reviewed. No signup, no API key to try it.

```yaml
# .github/workflows/verificate-gate.yml
name: Verificate Gate
on:
  pull_request:
    types: [opened, synchronize, reopened]
permissions:
  contents: read
  pull-requests: write
  id-token: write
jobs:
  verificate-gate:
    runs-on: ubuntu-latest
    steps:
      - uses: VerificateAI/verificate-gate-action@v1
```

**In your agent or IDE** (Cursor, Claude Code, and other MCP clients) — point your client at the hosted MCP
endpoint and the gate becomes a tool your agent calls before it hands you code.
See the **[MCP quickstart](https://github.com/VerificateAI/verificate-mcp-quickstart)**.

## 📦 Projects

| Repo | What it is |
|---|---|
| **[verificate-gate-action](https://github.com/VerificateAI/verificate-gate-action)** | The merge gate as a required GitHub check. |
| **[verificate-mcp-quickstart](https://github.com/VerificateAI/verificate-mcp-quickstart)** | Take a vibe-coded MVP to production. Hosted MCP, free to try. |
| **[verificate-langchain](https://github.com/VerificateAI/verificate-langchain)** | A veto gate for AI-written code in LangChain / LangGraph. |
| **[verificate-mcp](https://github.com/VerificateAI/verificate-mcp)** | Enterprise AI code validation for Cursor and MCP clients. |
| **[verificate-openclaw-guard](https://github.com/VerificateAI/verificate-openclaw-guard)** | The trust layer for OpenClaw — gate every answer and tool call. |

## How it works

Deterministic veto checks run first (is this a placeholder? can this test actually fail? does this standard-library
call exist? is a secret being logged?). No model output can override them. A Claude Haiku 5.5 review then checks the
rest, including whether third-party API calls are real; its high or critical security and API findings block. A rejection
comes only from a problem it can point to concretely, so turning on blocking mode rarely surprises anyone. If the
service is ever unreachable, the check passes and says so — an outage on our side never blocks your team's merges.

<div align="center">

<br>

**Only high-quality code reaches your application. Your reviewers spend their time on design, not on spotting fakes.**

[**Start free at verificate.ai →**](https://verificate.ai)

<sub>Verificate Pty Ltd · [verificate.ai](https://verificate.ai)</sub>

</div>
