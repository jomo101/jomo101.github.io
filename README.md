# Personal academic website — jomo101.github.io

Plain HTML + CSS. No build step, no dependencies, no JS framework.
GitHub Pages serves it as-is.

## Files

| File | What it is |
|---|---|
| `index.html` | Home — bio, topic cards, selected work, positions/education, awards, news |
| `research.html` | Research areas incl. software & HPC; commented-out Talks scaffold |
| `publications.html` | Full publication list by type |
| `code.html` | Software and data releases |
| `style.css` | All styling. Colors live in the two `:root` blocks at the top. |
| `assets/photo.jpg` | **Still the placeholder silhouette — replace with a real photo.**\
`sips -Z 800 --cropToHeightWidth 800 800 <src>.jpg --out assets/photo.jpg` |
| `cv.pdf` | Copy of `Resume_CV/moscoso_cv_2026.pdf`. **Currently unlinked** — the CV item was removed from the nav. Re-add `<a href="cv.pdf">CV</a>` to each page's `<nav>` to restore it. |
| `.nojekyll` | Tells GitHub Pages to skip Jekyll processing |

## Colors — UNC Carolina Blue

Defined once in `style.css`, light and dark:

| Token | Light | Dark | Used for |
|---|---|---|---|
| `--brand` | `#4B9CD3` | `#4B9CD3` | Carolina Blue: rules, card tops, flags |
| `--accent` | `#1A6091` | `#7FC1E8` | Link text, section labels |
| `--navy` | `#13294B` | `#cfe3f3` | Headings |
| `--bg` | `#fcfdfe` | `#0d1826` | Page ground |

True Carolina Blue `#4B9CD3` only reaches 3.0:1 on white, which fails WCAG AA
for body-size text, so links use the darker `#1A6091` and `#4B9CD3` stays
decorative. Every text/background pair on the site is at or above 5.0:1 in both
modes — if you change a color, re-check before publishing.

Dark mode follows the visitor's system setting automatically.

## Publishing

**Live at https://jomo101.github.io** — repo `jomo101/jomo101.github.io`,
Pages serving `main` at root. Push to `main` and the site rebuilds in a minute
or two:

```bash
git add -A && git commit -m "..." && git push
```

`cv.pdf` is in `.gitignore` on purpose: nothing on the site links to it, and it
carries a phone number and home address that would otherwise be publicly
downloadable at `jomo101.github.io/cv.pdf`. To publish a CV, put a scrubbed copy
in the repo and re-add the nav link.

Working copy: `~/Desktop/website`.

## Before publishing — open items

- **`assets/photo.jpg` is a placeholder.** Square crop, ~600×600 or larger.
- **The RHMC sampler is back on the site**, rewritten from the notes in
  `~/Research2026/HMC/` (status doc of 2026-07-28 + git log on `hpc-mpi`).
  It is marked "Private repository" because `github.com/jomo101/plaquette-hmc`
  is not public. Making it public would let the integrator table link to the
  code that produced it — the single highest-value change available to the site.
- **No CUDA or GPU claim appears anywhere**, deliberately. The notes contain no
  GPU work: `qc`'s README lists GPU offloading as not yet implemented, and the
  `-gpu` branch appears in the status doc only as an open question. Add this
  back when there is a measured number, not before.
- **The AVX-512 kernels belong to the `qc` library (a collaborator's).** The
  site credits them as such and claims only what is actually mine: the
  multi-RHS architecture note and the batched-rational solver.
- **Talks** are a commented-out scaffold in `research.html`. Uncomment and fill
  in from the CV.
- **PyCALQ's repo README does not publish the 17.7 s → 40 ms benchmark**, but
  `code.html` cites it. Add a short Performance note to the repo README so the
  number is checkable by anyone who follows the link — that is the whole point
  of the link being there.

## Editing

- **Text**: open the `.html` files, edit between the tags.
- **Colors**: `style.css`, the `:root` blocks.
- **Math**: MathJax is loaded on every page. Write `$E = mc^2$` inline or
  `$$...$$` for display.
- **Adding a publication**: copy an existing `<li>` in `publications.html`.
  Wrap your own name in `<span class="me">…</span>`. Add
  `<span class="flag">Editors' Suggestion</span>` inside the title span for
  awarded papers.

## Local preview

```bash
python3 -m http.server 8000
```

then open http://localhost:8000
