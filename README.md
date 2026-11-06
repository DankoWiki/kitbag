# קיטבג נחשון

An offline packing and return checklist for three weeks at Bahad 1 (Nachshon track). Install it to your phone's home screen and it opens and works with no reception. Your list is stored only on your device.

**App:** https://dankowiki.github.io/kitbag/

## What's here

| Path | What it is |
| --- | --- |
| `src/kitbag-nachshon.html` | The whole app: one HTML file. The same file runs as a Claude artifact (with cross-device sync) and as this offline app. |
| `src/icon.svg`, `src/icons/` | App icon source and the rendered PNGs |
| `build.mjs` | Builds `dist/`: proper `<head>`, self-hosted fonts, manifest, service worker |
| `icons.mjs` | Re-renders `src/icons/` from `src/icon.svg` (needs Playwright) |

The page checks `window.KITBAG_PWA`, which the build sets. When it's set, the page shows the install hint and file backup. Without `window.claude` (outside claude.ai), the page saves to `localStorage`.

## Build and deploy

```sh
npm install
npm run build          # writes dist/
```

Deploy by pushing the contents of `dist/` to the `gh-pages` branch. Each build stamps a new cache version into `sw.js`, so installed copies update the next time they open with a connection.

## Moving your list between versions

In the **סופ״ש** tab, open **גיבוי והעברה**. Use **העתק גיבוי כטקסט** on one version, paste it into the other one, and tap **בדוק את הטקסט**.
