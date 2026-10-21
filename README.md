# Repolex Knowledge Graph of PyCQA/oeuvre

RDF knowledge graph data for [PyCQA/oeuvre](https://github.com/PyCQA/oeuvre), parsed by [repolex](https://repolex.ai).

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
rlex download PyCQA/oeuvre
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 927deab3558f7f455b6dfca2167651eddc437a5d
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 927deab3558f7f455b6dfca2167651eddc437a5d
│           └── chunk-001.nq.gz
├── blob
│   ├── 38976540cc4f1a603e1b469deca270f8b4358561.nq.gz
│   ├── 3c09210b00f825aa945b64cad03418a482561f40.nq.gz
│   ├── 49c8f6b535f811291f9a0559116228ac7b9bc655.nq.gz
│   ├── 4c620cee4a53e8432fdef3096d17e818a4a1d1c9.nq.gz
│   ├── 86a42def9eacba0359f17e2ae696b7e41c766681.nq.gz
│   ├── 923b61996e82d8c3e92ccdee086389bcab3ae089.nq.gz
│   ├── a89faf9a8f83f99137ae41df7588d0d4e37b6dfe.nq.gz
│   ├── a90b9c910c9f8fd0b6b1629aadf9ee0882f8d622.nq.gz
│   ├── fd5d4c20d36be55a6e2c2307d168a1ba74cfcfb7.nq.gz
│   └── fe8936215986784461acbb531af89963d9daa206.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 927deab3558f7f455b6dfca2167651eddc437a5d.nq.gz
├── issue
│   └── issue.nq.gz
└── tag
    └── tag.nq.gz

12 directories, 17 files
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

[PyCQA/oeuvre](https://github.com/PyCQA/oeuvre)

---
*Parsed on 2026-10-21 by [repolex](https://repolex.ai)*
