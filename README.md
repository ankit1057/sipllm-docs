# SipLLM documentation portal

The published, offline, zero-dependency documentation portal for
**[SipLLM](https://github.com/ankit1057/sipllm)** — a dependency-free, CPU-first
LLM inference engine in C++17 that runs GGUF models larger than available RAM via
bounded-memory transformer-layer streaming.

**Live site:** https://ankit1057.github.io/sipllm-docs/

> [!IMPORTANT]
> This repository holds **generated HTML only**. Do not edit the `.html` files by
> hand — they are produced from Markdown source. It is consumed by the main
> project as a git submodule at `sipllm/site/`.

## How it is built

The source of truth lives in the main repo under
[`ankit1057/sipllm`](https://github.com/ankit1057/sipllm):

- `docs/**/*.md` — the Markdown pages (Product · Architecture · API · Journal · Project)
- `docs/assets/{style.css,app.js}` — the portal shell + client-side search
- `docs/build.py` — a stdlib-only Markdown→HTML static-site generator (no third-party deps)

Regenerate and refresh this repo:

```bash
cd sipllm
python3 docs/build.py         # renders docs/**/*.md -> site/*.html
cd site && git add -A && git commit -m "docs: rebuild portal" && git push
```

`.nojekyll` is committed so GitHub Pages serves every file verbatim (no Jekyll
processing). The portal is fully static and works offline — just open `index.html`.
