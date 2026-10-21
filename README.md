# Repolex Knowledge Graph of glue-viz/glue-ci

RDF knowledge graph data for [glue-viz/glue-ci](https://github.com/glue-viz/glue-ci), parsed by [repolex](https://repolex.ai).

> **Note**: This data is experimental and subject to change without notice.

## How to use this data

The easiest way to get started is to install the [rlex](https://github.com/repolex-ai/rlex) query tool:

```bash
cargo install --git https://github.com/repolex-ai/rlex
```

Verify the install:

```bash
rlex --help
```

**rlex is designed to be used primarily by LLMs in a terminal.** Start up your favorite AI assistant and ask it to use rlex. It handles the SPARQL — you just ask questions in plain English.

To load this repo's data:

```bash
rlex download glue-viz/glue-ci
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 3226bd1b5fff5866645dba22af135c558a72b8a2
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 3226bd1b5fff5866645dba22af135c558a72b8a2
│           └── chunk-001.nq.gz
├── blob
│   ├── 98d95d3d1a53c20cbd9bbad1efdfac2ff7870721.nq.gz
│   ├── a97caca35be0d0f7336613169e2ce91a14852748.nq.gz
│   ├── b7c34639a364e8a71391a7bd789ca93b50057f0b.nq.gz
│   ├── b85a4d8f37dda3190ef5500ee7cc5c747448ee4f.nq.gz
│   ├── c4993cb3d0363502b3a41ddb5f780a0d0c52e5dd.nq.gz
│   └── e65bb2ef538640268e965b6757ac02947bc3a511.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 3226bd1b5fff5866645dba22af135c558a72b8a2.nq.gz
├── issue
│   └── issue.nq.gz
└── tag
    └── tag.nq.gz

12 directories, 13 files
```

| Directory | What it contains |
|-----------|-----------------|
| `blob/` | Per-file AST graphs, content-addressed by git blob SHA. Each file in the source repo gets its own graph. |
| `aggregate/ast/` | Combined AST graph per parsed commit. Merges all blob graphs for a snapshot of the entire codebase at that point. |
| `aggregate/lsp/` | Language Server Protocol enrichment: resolved symbols, definitions, references, and type information. |
| `aggregate/dataflow/` | Interprocedural data flow edges between functions and modules. |
| `aggregate/repolex/` | Combined graph (AST + LSP + dataflow) per commit. |
| `commit/` | Git commit metadata (author, date, message, parent links). |
| `branch/` | Branch metadata. |
| `tag/` | Tag metadata. |
| `filetree/` | File tree snapshots per commit (which files existed and their blob SHAs). |
| `audit/` | Code architecture and graph audit reports per commit. |

## Source repository

[glue-viz/glue-ci](https://github.com/glue-viz/glue-ci)

---
*Parsed on 2026-10-21 by [repolex](https://repolex.ai)*
