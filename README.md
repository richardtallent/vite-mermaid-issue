# Background

- Mermaid is a markdown-like renderer for various types of charts.
- MarkdownIt is a markdown renderer.
- MarkdownIt-Mermaid is a plugin for MarkdownIt to add Mermaid functionality.

## The Issue

Everything works perfectly under Vite's dev server (`npm run dev`).

However, after building (`npm run build`) and serving up the `dist` folder, I get this error:

```
Uncaught TypeError: t.apply is not a function
at yo.use (vendor.84c6fd4e.js:formatted:7630)
at index.52194890.js:1
```

I don't know if the issue lies with mermaid, markdown-it-mermaid, or vite. I just know that when I remove the mermaid functionality from markdown-it, markdown rendering works fine again.
