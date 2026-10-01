---
name: codebase-relationship-indexer
description: "Constructs semantic relationship graphs and cross-file dependencies across repository subdirectories."
---

# Codebase Relationship Indexer

## Overview
The `codebase-relationship-indexer` skill recursively crawls project trees to extract symbol definitions, import hierarchies, and component affinities, serializing them into structured dependency graphs.

## Indexing Strategy
- **AST Parsing:** Identify classes, function signatures, docstrings, and decorator bindings.
- **Cross-File Affinities:** Score relationships (`direct_match`, `partial_match`, `reference`, `utility`) between existing components and planned implementations.
- **Token Efficiency:** Summarize file roles to inform agent planning without loading full source files.
