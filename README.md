# nijo-website-dist

Public hosting repo for **[nijostudio.com](https://nijostudio.com)**.

This repo contains **no source code**. It exists only because GitHub Pages
cannot publish from a private repository on a free organization plan — so the
private source repo builds the site and pushes the result here.

## How it works

```
Sapienity/nijo-website  (private, source)
  push to main
      │
      ▼
  GitHub Actions: npm ci && npm run build   →  out/
      │
      │  force-push (SSH deploy key)
      ▼
Sapienity/nijo-website-dist  →  gh-pages branch  →  GitHub Pages  →  nijostudio.com
```

## Do not edit this repo

The `gh-pages` branch is **force-pushed on every deploy**. Any commit made
here directly will be erased without warning. All changes belong in the
private source repo.

## Notes

- `.nojekyll` disables Jekyll, which would otherwise strip the `_next/`
  directory that the Next.js static export depends on.
- `CNAME` is emitted by the build, not set through the Pages UI — the force
  push would delete a UI-managed one and silently detach the domain.
