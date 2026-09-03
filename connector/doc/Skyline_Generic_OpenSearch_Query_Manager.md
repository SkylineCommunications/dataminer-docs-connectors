---
uid: Connector_help_Skyline_Generic_OpenSearch_Query_Manager
---
# Skyline Generic OpenSearch Query Manager

> TODO: To be defined.

## Knowledge graph (graphify)

This repository uses [graphify](https://github.com/safishamsi/graphify) to maintain a navigable knowledge graph of the codebase (`graphify-out/`, gitignored — not committed).

Because `graphify-out/` is excluded from version control, a fresh clone starts with **no graph and no local git hook** (git hooks live in `.git/hooks/`, which is never part of a clone). Each contributor must run the setup below once after cloning.

### One-time setup after cloning

```bash
# Build the graph for the first time
graphify .

# Install a local post-commit hook that auto-rebuilds the graph after every commit
graphify hook install
```

### Useful commands

| Command | Purpose |
|---|---|
| `graphify .` | Full pipeline build (interactive HTML, graph.json, GRAPH_REPORT.md) |
| `graphify . --update` | Incremental rebuild — re-extracts only new/changed files |
| `graphify . --cluster-only` | Re-run community clustering on the existing graph |
| `graphify hook install` | Install the post-commit hook (auto-rebuilds graph on code changes after each commit) |
| `graphify hook status` | Check whether the hook is installed |
| `graphify hook uninstall` | Remove the hook |
| `graphify query "<question>"` | Ask a question about the codebase using the graph |
| `graphify explain "<Node>"` | Get a plain-language explanation of a node |

> **Note:** The post-commit hook only rebuilds the graph on **your own local commits**, and only for **code** file changes (doc/paper/image changes still need a manual `graphify . --update`). It is not distributed via git — every contributor must run `graphify hook install` locally after cloning.
