# Architecture — AI2figma

## Layers

```
┌─────────────────────────────────────────────────────────────────┐
│ Agent Host — Codex / DSH / Claude / Cursor (owns all reasoning) │
└───────────────────────────────┬─────────────────────────────────┘
                                │ MCP (stdio JSON-RPC, 31 tools)
┌───────────────────────────────▼─────────────────────────────────┐
│ MCP server — host state machine, nextAction contracts           │
├─────────────────────────────────────────────────────────────────┤
│ Protocol — 51 zod-validated Figma methods (the single source    │
│ of truth for every request and result)                          │
├─────────────────────────────────────────────────────────────────┤
│ Orchestrator — context resolver, intent router, planners,       │
│ executors, verifiers, lock guard, correction loops              │
├─────────────────────────────────────────────────────────────────┤
│ Design engine — tokens, blueprint, 26+ semantic primitives,     │
│ construction matrix + deterministic reference compiler          │
├─────────────────────────────────────────────────────────────────┤
│ Tools — FigmaAdapter (batch/transaction/export), VisionAdapter, │
│ WorkspaceAdapter, ToolPolicy                                   │
├─────────────────────────────────────────────────────────────────┤
│ Local bridge — HTTP + WebSocket, schema validation, transaction │
│ shadow, action log, screenshot cache, locks, one-shot overrides │
└───────────────────────────────┬─────────────────────────────────┘
                                │ WebSocket
┌───────────────────────────────▼─────────────────────────────────┐
│ Figma plugin — real Plugin API: native nodes, transactions,     │
│ stash-based delete recovery, pluginData locks                   │
└─────────────────────────────────────────────────────────────────┘
```

## Design invariants

1. **Typed writes only.** The model never executes arbitrary JavaScript inside Figma. Every mutation is
   an `AtomicOperation` validated against a zod schema before dispatch.
2. **No automatic write retries.** Timeouts on writes surface as `TIMEOUT_UNCERTAIN` and are reconciled
   against real Figma state instead of silently retried.
3. **Transactions with shadow snapshots.** A batch is one transaction; failures roll back fully.
   Nested transactions are refused, never silently merged.
4. **Locks live in the document.** Locks are written to node `pluginData`, survive file saves, and
   require a one-shot human override token to bypass.
5. **Evidence with hashes.** Terminal states are backed by write-once artifacts (plans, receipts,
   captures, ledgers); replaying the same input performs zero new writes and produces identical hashes.
6. **Fail closed.** Integrity checks recompute coverage/warnings/ownership from raw ledgers; a mismatch
   stops the run (`RECONCILIATION_REQUIRED` / `HUMAN_ACTION_REQUIRED`) instead of claiming completion.

## Reference reconstruction pipeline

```
Local raster (PNG/JPEG/WebP)
  → deterministic pixel measurement (in-house PNG codec + pixel analysis)
  → host-authored decomposition manifest (work order → submission → integrity check)
  → construction compiler (115-element support matrix, quality gate)
  → verified native construction (write receipt + readback + rollback)
  → asset settlement (local component reuse / Community transfer / media / vectors)
  → target capture + region fidelity ledger (per-region pixel metrics)
  → scoped correction (failed regions only, PASS regions locked, max 2 rounds)
  → visual review → COMPLETE only when every gate passes
```

## What is intentionally not public

Source code, internal contracts, commissioning harnesses and evidence archives. This document and
`METRICS.md` describe the system at a level sufficient to evaluate its scale and engineering quality
without disclosing implementation.
