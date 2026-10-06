# Bellewether — 6-country MVP

Interactive data explorer for the **Belonging as Prevention and Digital Gender Hostility
Predictive Model** country packages: gender-based violence × far-right political support ×
climate, for Sweden, Germany, the Netherlands, Australia, Brazil (with a 19-state map) and
South Korea, plus a cross-country indexed comparison view.

This repo contains the **production static build** (compiled React/Vite app, no build step
needed at deploy time).

- Preview password: set at build time (client-side gate; for real protection put Cloudflare
  Access in front of the domain).
- SPA fallback is handled by `_redirects` (Cloudflare Pages).

## Deploy to Cloudflare Pages (bellewether.tannencentre.org)

1. **Cloudflare dashboard → Workers & Pages → Create → Pages → Connect to Git** → select
   this repo (`GonzoDevRando/bellewether`).
2. Build settings: framework preset **None**, build command **(empty)**, output directory **/**.
3. After the first deploy, open the project → **Custom domains → Set up a custom domain** →
   enter `bellewether.tannencentre.org`. Cloudflare creates the DNS record for you — do
   **not** add a manual DNS record; DNS alone would serve the wrong content because content
   selection happens at the Cloudflare edge, keyed to the Pages project that claims the domain.
4. Optional but recommended: **Zero Trust → Access → Add an application** (self-hosted) for
   `bellewether.tannencentre.org` to get real server-side authentication instead of the
   client-side gate.

## Source

App source and data pipeline live in the Kimi Work workspace; rebuilds are produced with
`VITE_GATE=1 npm run build` and the `dist/` contents copied here.
