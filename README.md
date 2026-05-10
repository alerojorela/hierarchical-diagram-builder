# Hierarchical Diagram Builder

A browser-based tool for visualizing hierarchical data in three different ways:

- **Binary Tree** — SVG diagram of a labeled binary tree
- **Taxonomy Grid** — Recursive subdivision of a rectangle (treemap-style)
- **Tabulator** — Hierarchical data rendered as a merged-cell table

## Usage

Open `index.html` in a browser. Select a tool, enter your data, and click **Render**.

### Input formats

Binary Tree and Tabulator share a unified input with three interchangeable formats:

| Format | Example |
|---|---|
| **Bracket** | `[TP [NP [Det the] [N cat]] [VP [V sat]]]` |
| **Bracket (indented)** | Same as above, with line breaks after each `[` |
| **Tree** | One node per line, indentation (tab or 4 spaces) = depth |

Taxonomy Grid uses its own bracket notation where spaces separate siblings and `[...]` creates grouping: `[A B [C D] E]`

### Controls

- **Max depth** — Limit rendering depth (0 = unlimited)
- **Export** — Download as SVG (tree), HTML (grid), or CSV (table)
- **Copy URL** — Shareable link with your data embedded in the URL

### Taxonomy Grid options

- **Cell Action** — Select, Copy text, or Reorder cells visually
- **Method** — CSS Flex or CSS Grid rendering
- **Margin** — Spacing between cells in pixels

## Embedding

Each tool is available as a standalone HTML page for iframe embedding:

```html
<!-- Binary Tree -->
<iframe src="binarydivision.html?q=[A [B] [C [D] [E]]]&depth=3"
        width="600" height="400"></iframe>

<!-- Taxonomy Grid -->
<iframe src="taxogrid.html?q=[A B [C D]]&method=0&margin=2&action=select"
        width="400" height="400"></iframe>

<!-- Tabulator -->
<iframe src="tabulate.html?q=Animals%0A%09Mammals%0A%09%09Cat%0A%09%09Dog&depth=0"
        width="400" height="300"></iframe>
```

## Project structure

```
index.html              Main application (unified interface)
binarydivision.html     Embeddable binary tree renderer
taxogrid.html           Embeddable taxonomy grid renderer
tabulate.html           Embeddable tabulator renderer
js/
  common.js             Shared utilities
  parsernode.js          PEG.js parser for labeled bracket notation
  parserterminal.js      PEG.js parser for terminal-only bracket notation
  taxogrid.js            Taxogrid rendering (CSS Flex / CSS Grid)
  binarydivision.js      Binary tree SVG rendering
style/
  common.css             Shared CSS utilities
  graphicOutput.css      Main layout and typography
  taxogrid.css           Taxogrid-specific styles
```

## License

[GPLv3](LICENSE)

## Author

Alejandro Rojo Gualix
