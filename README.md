# AstroYuga API Docs

Interactive OpenAPI / Swagger reference for the AstroYuga backend — every
endpoint with its request body, query params, responses, and the role(s) it
requires.

**Live docs:** https://hotelmgmtcrm.github.io/astroyuga-docs/

## How it stays up to date

This repo is **published automatically**. It is not edited by hand.

- The backend repo ([`astroyugawork/backend`](https://github.com/astroyugawork/backend))
  defines the API with `@nestjs/swagger`.
- On every push to the backend's `main` branch, the
  `Publish OpenAPI docs` GitHub Action regenerates `openapi.json` and commits
  it here.
- GitHub Pages serves `index.html` + `openapi.json` — so the live docs
  refresh within a minute of any backend change.

## Files

| File | Purpose |
|------|---------|
| `index.html`  | Swagger UI shell — loads `openapi.json` |
| `openapi.json`| The spec itself — **auto-generated, do not edit** |
| `.nojekyll`   | Tells GitHub Pages to serve files as-is |

## Testing endpoints

1. Open the live docs.
2. Top-right, choose the **server** — `Production` or `Local development`.
3. Click **Authorize** and paste a `Bearer` JWT (get one from
   `POST /auth/verify-otp`).
4. Expand any endpoint → **Try it out** → **Execute**.

> Each endpoint shows a `🔒 Access` line stating whether it is public or which
> role (USER / ASTROLOGER / ADMIN / SUPER_ADMIN) it needs.

## One-time setup

1. **Backend repo** → Settings → Secrets and variables → Actions → add
   `DOCS_REPO_TOKEN` — a Personal Access Token with `contents: write` on this
   repository. The `Publish OpenAPI docs` workflow uses it to push the
   regenerated spec here.
2. GitHub Pages is already enabled (branch `main`, folder `/`).

> If you later transfer this repo into the `astroyugawork` org, update the
> clone URL in the backend's `.github/workflows/publish-openapi.yml`.
