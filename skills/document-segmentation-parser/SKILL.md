---
name: document-segmentation-parser
description: "Parses PDF papers and technical documentation into structured sections and mathematical formulations."
---

# Document Segmentation Parser

## Overview
The `document-segmentation-parser` skill converts complex multi-column academic PDF files into cleanly structured markdown or JSON representations, preserving table structures and mathematical notation.

## Capabilities
- Extract section headings (`Abstract`, `Methodology`, `Experiments`, `Conclusion`).
- Transcribe mathematical formulas into KaTeX/LaTeX syntax blocks.
- Filter out bibliographies and acknowledgments to preserve agent context windows.
