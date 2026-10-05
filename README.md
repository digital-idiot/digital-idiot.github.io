# Interactive Explainers

Author: [digital-idiot](https://github.com/digital-idiot)

Four single page interactive explainers from the MTG FCI foundation model work, plus a
landing page that links them.

```
index.html                 landing page, selects one of the four
gradient-descent.html      learning by following the slope
high-dimensions.html       why models lift their data
attention.html             from correlation to self attention
positional-encoding.html   teaching a ViT where its patches are
.nojekyll                  stops GitHub Pages filtering anything
```

Total about 370 KB. Every page is self contained: no local assets, no build step, no
framework. Each demo pulls MathJax, Plotly and web fonts from a CDN, so the pages need a
network connection. The landing page itself has no external dependencies at all.

## Publishing

**Every link is relative**, so this folder works unchanged at any base path: a site root,
`/demo/`, or anywhere deeper. Nothing needs rewriting.

To serve at `<user>.github.io/demo/` pick either route.

**A. A repository named `demo`.** Put these files at the repository root, push, then in
Settings, Pages set the source to `main` and `/ (root)`.

```bash
cp -R docs/. /path/to/demo/
cd /path/to/demo && git add -A && git commit -m "Add interactive explainers" && git push
```

**B. A `demo/` folder inside the `<user>.github.io` repository.** Nothing to configure,
that repository is already served at the domain root.

```bash
mkdir -p /path/to/<user>.github.io/demo
cp -R docs/. /path/to/<user>.github.io/demo/
```

Either way the result is `https://<user>.github.io/demo/`.

## Checking it before you push

```bash
cd docs && python3 -m http.server 8000   # then open http://localhost:8000/
```

Serving over http rather than opening the files directly is worth doing, because a few
library code paths use `fetch`, which some browsers refuse under the `file://` protocol.

## Keyboard

On the landing page, `1` to `4` open a demo and the arrow keys move between the cards.

## Licence

Two licences, which is the usual split for a repository that is part code and part
writing.

- **Code** (the landing page, the demo sources, anything executable): Apache License 2.0,
  full text in [`LICENSE`](LICENSE).
- **Text and figures** (the explanatory writing and the diagrams): Creative Commons
  Attribution 4.0 International,
  [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).

Attribution: digital-idiot, with a link back to the source repository.

Third party libraries keep their own licences. The demos load MathJax (Apache 2.0) and
Plotly (MIT) from a CDN rather than vendoring them.
