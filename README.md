# Arshis-Memory-Pro
Advanced memory management system for AI agents with 200K+ capacity, hybrid retrieval, and smart decay.
---

# Arshis-Memory-Pro

<div align="center">

**Advanced Memory System for AI Agents**

[![Version](https://img.shields.io/badge/version-v1.0-blue.svg)](https://github.com/TaylliSun/Arshis-Memory-Pro/releases)
[![License](https://img.shields.io/badge/license-MIT-orange.svg)](LICENSE)
[![Features](https://img.shields.io/badge/features-20+-red.svg)](docs/FEATURES.md)

Long-term memory storage, intelligent retrieval, and knowledge management for AI agents.

[Features](#features) | [Installation](#installation) | [Usage](#usage) | [Commands](#commands) | [API](#api)

</div>

---

## Overview

Arshis-Memory-Pro is an advanced memory management system for AI agents, featuring long-term storage, intelligent retrieval, and automated knowledge organization.

### Key Features

- **100K Memory Capacity** - Store up to 100,000 memories with smart decay
- **Hybrid Retrieval** - Vector similarity + BM25 keyword search
- **Auto Categorization** - 15 categories with automatic tagging
- **Smart Decay** - 730-day half-life with importance-based retention
- **Project Isolation** - Separate memory libraries for different projects
- **Advanced Search** - Full-text search with filters and time ranges

---

## Features

### Core Functions

#### 1. Automatic Memory Capture
- Automatically saves important conversations
- Configurable capture thresholds (5+ characters)
- Smart importance scoring (0.0-1.0)

#### 2. Intelligent Retrieval
- Hybrid search: Vector (50%) + BM25 (50%)
- Top-100 reranking for accuracy
- Category and tag filtering
- Time-range filtering

#### 3. Memory Management
- 100,000 memory capacity (20,000 active + 80,000 archive)
- 730-day half-life decay
- Automatic cleanup of low-importance memories (<0.05)
- Project-based isolation

#### 4. Advanced Search
```bash
# Search memories
#search protagonist

# Search by category
#search character category:role

# Search by time range
#search recent 7 days

# View statistics
#memory-stats
```

#### 5. Dream Mode
```bash
# Record dream/inspiration
#dream Dreamt about protagonist flying

# Review today
#review-today

# Morning brief
#morning-brief

# Creative incubation
#incubate How to design interesting combat system
```

#### 6. Memory Visualization
```bash
# Tag cloud
#tag-cloud

# Category distribution
#category-dist

# Growth curve (last 30 days)
#growth-curve 30

# Memory graph
#memory-graph protagonist

# Importance distribution
#importance-dist
```

#### 7. Reminders
```bash
# Set reminder
#reminder weekly-review weekly

# View reminders
#list-reminders

# Important memory reminder
#important-reminder

# Project progress
#project-progress Tianlie
```

#### 8. Import/Export
```bash
# Export memories
#export Tianlie

# Import from Markdown
#import /path/to/file.md

# Batch import
#batch-import /path/to/docs
```

---

## Installation

### Quick Install

```bash
# Download release
wget https://github.com/TaylliSun/Arshis-Memory-Pro/releases/download/v1.0/Arshis-Memory-Pro-clean.zip

# Extract to skills directory
unzip Arshis-Memory-Pro-clean.zip -d ~/.openclaw/workspace/skills/

# Verify installation
test -f ~/.openclaw/workspace/skills/Arshis-Memory-Pro-release/SKILL.md && echo "✅ Installation successful"
```

### Configuration

Add to `~/.openclaw/openclaw.json`:

```json
{
  "plugins": {
    "entries": {
      "Arshis-Memory-Pro": {
        "enabled": true,
        "config": {
          "autoCapture": true,
          "autoRecall": true,
          "recallLimit": 20,
          "injectMinLength": 5,
          "categories": ["Uncategorized", "Knowledge", "Ideas", "Other"],
          "maxMemories": 100000,
          "activeLimit": 20000,
          "archiveLimit": 80000,
          "decay": {
            "enabled": true,
            "halfLife": 730,
            "minImportance": 0.05
          },
          "retrieval": {
            "mode": "hybrid",
            "vectorWeight": 0.5,
            "bm25Weight": 0.5,
            "rerank": true,
            "rerankTopK": 100
          }
        }
      }
    }
  }
}
```

---

## Usage

### Basic Commands

| Command | Description | Example |
|---|---|---|
| `#remember [content]` | Save memory manually | `#remember Protagonist name: Alan` |
| `#search [keywords]` | Search memories | `#search protagonist personality` |
| `#memory-stats` | View statistics | `#memory-stats` |
| `#export [project]` | Export memories | `#export Tianlie` |
| `#import [file]` | Import from file | `#import /path/to/file.md` |

### Advanced Commands

| Command | Description | Example |
|---|---|---|
| `#dream [content]` | Record dream/inspiration | `#dream Flying in sky` |
| `#review-today` | Review today's memories | `#review-today` |
| `#morning-brief` | Morning brief | `#morning-brief` |
| `#incubate [question]` | Creative incubation | `#incubate Combat design` |
| `#tag-cloud` | View tag cloud | `#tag-cloud` |
| `#category-dist` | Category distribution | `#category-dist` |
| `#growth-curve [days]` | Growth curve | `#growth-curve 30` |
| `#memory-graph [keyword]` | Memory relationship graph | `#memory-graph protagonist` |
| `#reminder [type] [freq]` | Set reminder | `#reminder weekly-review weekly` |
| `#list-reminders` | View reminders | `#list-reminders` |

---

## API

### Memory Core API

```bash
# Store memory
python3 scripts/memory_core.py store "Memory content" 0.7 knowledge

# Recall memories
python3 scripts/memory_core.py recall "Search keyword" 5

# View stats
python3 scripts/memory_core.py stats
```

### Advanced Search API

```bash
# Search with filters
python3 scripts/advanced_search.py "#search protagonist category:role"

# Export memories
python3 scripts/advanced_search.py "#export Tianlie"
```

---

## Project Structure

```
Arshis-Memory-Pro/
├── scripts/ # Core scripts (14 files)
│ ├── memory_core.py # Core memory functions
│ ├── advanced_search.py # Advanced search
│ ├── dream_mode.py # Dream mode
│ ├── memory_visualization.py # Visualization
│ ├── memory_reminder.py # Reminders
│ ├── memory_import.py # Import/Export
│ ├── smart_summary.py # Smart summary
│ └── ... (7 more scripts)
├── docs/ # Documentation
├── SKILL.md # Skill definition
├── HOOK_SETUP.md # Hook setup guide
└── CLEANUP_REPORT.md # Cleanup report
```

---

## Performance

| Metric | Value |
|---|---|
| **Memory Capacity** | 100,000 memories |
| **Retrieval Speed** | <200ms (100K memories) |
| **Storage Size** | ~50MB (100K memories) |
| **Memory Usage** | ~1-2GB (100K memories) |
| **Half-life** | 730 days (2 years) |

---

## Requirements

- **Python**: 3.8+
- **OpenClaw**: 1.0+
- **Dependencies**: None (pure Python standard library)
- **Platform**: Windows / Linux / macOS

---

## License

This project is licensed under the [MIT License](LICENSE) - commercial-friendly, free to use and modify.

---

## Acknowledgments

Thanks to the following resources:
- SiliconFlow for embedding models
- LanceDB for vector storage
- OpenClaw platform

---

## Contact

- **GitHub**: https://github.com/TaylliSun/Arshis-Memory-Pro
- **Issues**: https://github.com/TaylliSun/Arshis-Memory-Pro/issues
- **Author**: TaylliSun (Arshis)

---

<div align="center">

**Arshis-Memory-Pro v1.0**

*Advanced Memory System for AI Agents*

Author: TaylliSun (Arshis)  
License: MIT

If this project helps you, please give it a star!

</div>
```

---
