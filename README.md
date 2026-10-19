# Span Lab

An interactive, dependency-free 3D vector-span visualizer for teaching linear algebra. Its entire application lives in **`index.html`** (HTML + CSS + vanilla JavaScript). No npm, build step, Three.js, account, or web service is required.

## Features

- Add or remove **1–8 vectors** in \(\mathbb R^3\), and edit their x/y/z coordinates.
- Shows the **dimension of the span**, including the important zero-vector case:
  - rank 0: origin only;
  - rank 1: a line through the origin;
  - rank 2: a plane through the origin;
  - rank 3: all of \(\mathbb R^3\).
- Drag to rotate the 3D view; scroll/pinch to zoom; reset or fit the view.
- Change scalar coefficients to see one **linear combination** and its head-to-tail vector addition path.
- Color-coded vectors and badges indicating which inputs introduce new independent directions (relative to earlier inputs).
- Five educational presets, a hideable grid, a fullscreen presentation mode, and shareable vector-set URLs.
- Responsive desktop/mobile UI, high-DPI canvas, no external requests.

**Mathematical note:** The highlighted line/plane/volume is clipped to a visual reference cube. The mathematical span always extends without bound. Any 4th, 5th, etc. vector lies in an at-most 3-dimensional span. Rank is computed with two-pass modified Gram–Schmidt and a relative floating-point tolerance, so extremely nearly dependent vectors can be classified as dependent.

## Try it locally

Just double-click `index.html` in any current Chrome, Edge, Safari, or Firefox browser. No web server is needed.

## Publish on GitHub Pages

1. Create a new public GitHub repository, e.g. `span-lab`.
2. Upload the **`index.html`** file to the root of the repository, then commit it. (`README.md` is optional.)
3. Go to **Settings → Pages**. Under **Build and deployment**, select **Deploy from a branch**, choose `main` and `/(root)`, and save.
4. Visit `https://YOUR-USERNAME.github.io/span-lab/` after Pages finishes deploying.

For a user/organization site named `YOUR-USERNAME.github.io`, the project instead appears at `https://YOUR-USERNAME.github.io/`.

## Customize

Open `index.html` with a text editor.

- At the top of the `<style>` section, change the CSS color variables, e.g. `--mint`, `--bg`.
- In the script, edit `MAX_VECTORS` (default 8), `COLORS`, `BOX` (visual cube half-width), or `EXAMPLES`.
- Presets are just 3-component vector arrays.

Useful browser-console helpers:

```js
SpanLab.setVectors([[1, 0, 0], [2, 0, 0]]);  // dependent: rank 1
SpanLab.setVectors([[1, 0, 0], [0, 1, 0]]);  // independent: rank 2
SpanLab.setVectors([[1, 0, 0], [0, 1, 0], [0, 0, 1]]); // rank 3
SpanLab.setCoefficients([1, -0.5, 1]);       // one highlighted combination
SpanLab.getState();                           // inspect current state
```

## Credits / license

This standalone teaching tool is provided under the MIT License. See `LICENSE`.
