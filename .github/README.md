# Foundations of Numerical Relativity — Talk Materials

This repository contains the slides and supporting material for the talk  
**“Foundations of Numerical Relativity”**, delivered at the  
**Escuela de Física Teórica de Valparaíso (CeFiTeV), 2025**.

The slides are written in Markdown using **Marp**, embedded within a lightweight  
**Hugo** website that can be built and viewed locally or published via GitHub Pages.

The published online version is available at:

👉 https://crisbh.github.io/foundations-numerical-relativity-talk/

---

## 📄 Contents

- `slides/` — Source Markdown for the talk (Marp format).  
- `static/images/` — Figures and diagrams used in the slides.  
- `content/` — Hugo content pages (front page, description).  
- `themes/hugo-book/` — Theme included as a Git submodule.  
- `public/` — Deployment worktree for GitHub Pages (ignored on `main`).  
- `Makefile` — Build rules for slides and site generation.

---

## 🛠️ Build Instructions (Reproducible Workflow)

### 1. Clone the repository (with theme submodule)

```bash
git clone --recurse-submodules https://github.com/crisbh/foundations-numerical-relativity-talk.git
cd foundations-numerical-relativity-talk
```
