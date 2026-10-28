# Repolex Knowledge Graph of napari/packaging

RDF knowledge graph data for [napari/packaging](https://github.com/napari/packaging), parsed by [repolex](https://repolex.ai).

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
rlex download napari/packaging
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── d175b4834ff78a756f3985f0e7cb9fc2fd68c1fd
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── d175b4834ff78a756f3985f0e7cb9fc2fd68c1fd
│           └── chunk-001.nq.gz
├── blob
│   ├── 0ea5809b21e618e4c8777b51cea413e867c43197.nq.gz
│   ├── 10ef541c44cd205508d4b5ba22566d28bf01a447.nq.gz
│   ├── 15d244909d54abae3801c9e8b102b929062b9097.nq.gz
│   ├── 356454a13463ea9d09c946b1e25578288c079ccb.nq.gz
│   ├── 5be2d839e5ee57154076bc1d4471c96d85751dd3.nq.gz
│   ├── 5cca4a98b3e369372034edd3e5990a7e63c01acf.nq.gz
│   ├── 5f26f7b1b745b4736cfe749a9dc39a9d82d77a34.nq.gz
│   ├── 643c3a67249bc961e655ee03c77f57e5bf6298c8.nq.gz
│   ├── 8f90816c2ea507c5e91cd5f45812eb138d3f8430.nq.gz
│   ├── 95a4a84c08d4a764659a569cd57eb666b81d6d5c.nq.gz
│   ├── 9636212b22a2d56a2cd49f8202bf1d7b2a98bfb2.nq.gz
│   ├── be091cbf1b284dce6206a91da6ca3bf00c9727dd.nq.gz
│   ├── d4369c8a57eb5110dc3057b8d8b22af7acb8dfae.nq.gz
│   ├── df0c4b57c74aeed0c521fe2f34e38e95f8833abf.nq.gz
│   └── f32bd3d04b8f7885b9f95ef01aeca4dc0989732c.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── d175b4834ff78a756f3985f0e7cb9fc2fd68c1fd.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 23 files
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

[napari/packaging](https://github.com/napari/packaging)

---
*Parsed on 2026-10-28 by [repolex](https://repolex.ai)*
