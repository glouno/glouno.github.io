# glouno.github.io

The GitHub Pages root forwards visitors to [Paul Béglin's portfolio](https://paul.beglin.fr/).
The original Task Tindr hackathon demo is preserved at
[glouno.github.io/task-tindr/](https://glouno.github.io/task-tindr/).

## Implementation

- `index.html`: browser-level forwarding with a canonical URL, immediate HTML
  refresh, JavaScript history replacement and a visible fallback link.
- `task-tindr/index.html`: byte-for-byte copy of the original hackathon page.
- `.nojekyll`: publish directly as a static site.

This is an HTML/browser redirect, not an HTTP 301/308. It adds no trackers or
external scripts. Query parameters and arbitrary old paths are not forwarded.

## Hosting and deployment

GitHub Pages publishes `main` at `/`, with HTTPS enabled and no custom domain.
Pushes to `main` publish this site. `paul.beglin.fr` remains hosted on Vercel;
its DNS and hosting configuration are independent of this forwarding page.
No CNAME file is needed for this approach.

GitHub's static-site model:
https://docs.github.com/en/pages/getting-started-with-github-pages/what-is-github-pages

After publishing, verify that the root browser navigation reaches the portfolio
and `/task-tindr/` still renders the original demo.

Rollback: restore the root page from `task-tindr/index.html` (or Git history),
then commit and push that version. Keep the archived demo available.
