# Repolex Knowledge Graph of seatgeek/thefuzz

RDF knowledge graph data for [seatgeek/thefuzz](https://github.com/seatgeek/thefuzz), parsed by [repolex](https://repolex.ai).

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
rlex download seatgeek/thefuzz
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 1ba86f33a19deedcf886b74cf6efffd79495a50f
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 1ba86f33a19deedcf886b74cf6efffd79495a50f
│           └── chunk-001.nq.gz
├── blob
│   ├── 24a8e6e95f1c87167ec9fe95bf6206d1fe5ff570.nq.gz
│   ├── 2c15b14399f9e131e7a9770e08bbf91d708f8ce7.nq.gz
│   ├── 3b75cb907d3045e3e81b2c64974137da57738cac.nq.gz
│   ├── 40c1115463c1cc9cfb9799d07d9aa26f6a0c8ad1.nq.gz
│   ├── 4df42c0c7f632d0f36f6be5109d86912d58d899e.nq.gz
│   ├── 5020d6e9725ce9a021c8a08bbd62743c9cc897ca.nq.gz
│   ├── 66d9d1e396e8699c133dff518583ff96b155df56.nq.gz
│   ├── 745c12ab59d94d5e675ef74cfbc3ed1d51db7e30.nq.gz
│   ├── 769b79aab23c21dad523597f6f0c6345116ecbb0.nq.gz
│   ├── 7c23c40e26da8d402f163f65eb502632609f96d6.nq.gz
│   ├── 7d86e4836ee820afe491df74ffe3ca408f4bb0d8.nq.gz
│   ├── 86916a2b5533751365b735b2f13c64b9b1e3ee19.nq.gz
│   ├── 8b137891791fe96927ad78e64b0aad7bded08bdc.nq.gz
│   ├── a69711a256a468d8f669f9f0d2ab37215604ed0a.nq.gz
│   ├── a6b3f7421b4118084679adbdffbf5170b958dd20.nq.gz
│   ├── b4b26305ae8afd56e2687da4de8a18cf77e8840a.nq.gz
│   ├── bcda741d8eb2b6c136237245c9cfe1f8d81a12e3.nq.gz
│   ├── ce6d836fa6ce9fc7437ca4cc896cf0bc00c3f990.nq.gz
│   ├── f2f8253e51c67ebcf660ac0c0a2dc5321dd44342.nq.gz
│   ├── f598525fac4bc02119ad5f570ece3ff7544224a7.nq.gz
│   ├── f816a697af1d7e5a1f386b3ee82eea3b633d3a1d.nq.gz
│   └── fcf7e1eaee322481723f93360a7aa69e3cb402e6.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 1ba86f33a19deedcf886b74cf6efffd79495a50f.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 30 files
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

[seatgeek/thefuzz](https://github.com/seatgeek/thefuzz)

---
*Parsed on 2026-10-18 by [repolex](https://repolex.ai)*
