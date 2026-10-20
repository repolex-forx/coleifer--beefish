# Repolex Knowledge Graph of coleifer/beefish

RDF knowledge graph data for [coleifer/beefish](https://github.com/coleifer/beefish), parsed by [repolex](https://repolex.ai).

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
rlex download coleifer/beefish
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── f63b808c20599a75b761d9881dc84394ab5bad9f
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── f63b808c20599a75b761d9881dc84394ab5bad9f
│           └── chunk-001.nq.gz
├── blob
│   ├── 384a9a30b911429fdf8a7b71ea3dae2087730a6a.nq.gz
│   ├── 650c0ccc03b83b23874bdd3c3295021b18bc4a48.nq.gz
│   ├── 6c57dc1f050119b31ece1f045cdcfb911493aeb1.nq.gz
│   ├── 9d5d250d095009403f66851f48866f5cfe39703b.nq.gz
│   ├── a64c9fd251d4af08eada1def1cd2d56af71781b7.nq.gz
│   └── c752ab3ead2e7be324e5cafb5e1d53135c16af13.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── f63b808c20599a75b761d9881dc84394ab5bad9f.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 14 files
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

[coleifer/beefish](https://github.com/coleifer/beefish)

---
*Parsed on 2026-10-20 by [repolex](https://repolex.ai)*
