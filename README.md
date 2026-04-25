---
name: Arshis-Memory-Pro
description: OpenClaw Primary Memory Plugin with LanceDB vector database, hybrid retrieval, self-evolution, Arshis Dreaming Engine, and context injection control.
version: 5.0.0
author: Arshis
license: MIT-0
---

# Arshis-Memory-Pro

[![License: MIT-0](https://img.shields.io/badge/License-MIT--0-green.svg)](LICENSE)
[![OpenClaw](https://img.shields.io/badge/OpenClaw-2026.4.0+-blue.svg)](https://docs.openclaw.ai)
[![Python](https://img.shields.io/badge/Python-3.9+-green.svg)](https://www.python.org)

OpenClaw Primary Memory Plugin for indie developers and power users. Manages long-term memory with vector search, self-evolution, dreaming engine, and strict context injection control.

## Modes

### Primary Mode (default)
- Takes over OpenClaw memory slot
- Replaces memory-core as the primary memory provider
- Uses Arshis Dreaming Engine instead of native dreaming
- Full control over memory injection and context limits

### Helper Mode
- Does not occupy the memory slot
- Coexists with OpenClaw memory-core
- Acts as auxiliary retrieval and scoring system
- Does not interfere with native memory operations

## Core Features

### Memory Storage and Retrieval
- LanceDB vector database (1024-dimensional semantic vectors)
- Hybrid retrieval: vector semantics + BM25 keywords + rerank reordering
- Auto-grading by importance (0.1-1.0): core/working/peripheral
- Self-evolution engine adapts retrieval weights based on feedback

### Arshis Dreaming Engine v1.0
- Light Sleep (30 min): Summarize recent conversations and short-term memories
- Deep Sleep (120 min): Distill long-term patterns and themes
- REM Dream (360 min): Generate creative cross-category connections
- Forgetting (30 day decay): Archive low-value, old memories
- Promotion: Promote high-value, frequently-recalled memories to long-term

### Context Injection Control
- Summary-only mode by default (not full memory text)
- Maximum 8 memories injected per query (configurable)
- Relevance threshold filtering (default: 0.72)
- Max context token limit (default: 12,000)
- Low-relevance memories excluded from injection
- Prevents context explosion from memory overload

### Self-Evolution
- Automatic feedback collection on every retrieval
- Parameter auto-optimization (weights, decay cycles, thresholds)
- Strategy generation from error patterns
- Architectural reflection: detects systemic issues and reports

### Privacy and Safety
- No external network requests
- No data collection or upload
- No external LLM calls
- No API keys required
- Local storage only
- Auto-capture disabled by default
- User confirmation required for destructive operations

## Usage

### Store Memory
```
store_memory({ text: "The five races are Human, Fox, Feather, Spirit, and Stone.", importance: 0.9, category: "worldview" })
```

### Recall Memory
```
recall_memory({ query: "five races", limit: 5 })
```

### Delete Memory
```
delete_memory({ memory_id: "abc123..." })
```

### Memory Statistics
```
memory_stats()
```

### Dream Cycles
```
run_dream_cycle({ mode: "light" })      // Summarize recent
run_dream_cycle({ mode: "deep" })       // Distill patterns
run_dream_cycle({ mode: "rem" })        // Creative connections
run_dream_cycle({ mode: "forgetting" }) // Archive old memories
run_dream_cycle({ mode: "promotion" })  // Promote to long-term
```

### Evolution
```
evolution_status()
evolution_report()
```

### Privacy Controls
```
export_memories({ filepath: "/path/to/backup.json" })
clear_memories({ confirm: true })
```

## Configuration (Environment Variables)

| Variable | Default | Description |
|----------|---------|-------------|
| ARSHIS_MEMORY_MODE | primary | primary or helper |
| ARSHIS_PRIMARY_MEMORY | true | Whether to take over memory slot |
| REPLACE_MEMORY_CORE | true | Replace memory-core plugin |
| ARSHIS_DREAMING_ENABLED | true | Enable dreaming engine |
| MAX_MEMORY_INJECTION | 8 | Max memories per query |
| SUMMARY_ONLY_MODE | true | Inject summaries, not full text |
| RELEVANCE_THRESHOLD | 0.72 | Minimum score for injection |
| MAX_CONTEXT_TOKENS_FOR_MEMORY | 12000 | Max tokens for memory context |
| AUTO_CAPTURE_ENABLED | false | Auto-capture conversations |
| REQUIRE_USER_CONFIRMATION | true | Confirm destructive ops |
| LOCAL_ONLY | true | No external network |

## Data Location

All memory data stored locally in:
- `~/.openclaw/data/memory-custom/` (memory database)
- `~/.openclaw/workspace/memory/arshis-dreams/` (dream logs)

## Privacy

This plugin does not make outbound network requests, does not collect or upload user data, does not call external LLM services, and does not require API keys. All data is stored locally. Memory slot takeover only occurs when primary mode is explicitly enabled.

## Requirements

- OpenClaw 2026.4.0+
- Python 3.9+
- LanceDB 0.26+ (for vector storage)
- rank-bm25 0.2.0+ (for keyword search)

## License

MIT-0
