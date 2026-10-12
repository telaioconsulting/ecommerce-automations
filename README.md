# Telaio - Ecommerce Automations

Website of **Telaio - Ecommerce Automations**, a service by [Telaio](https://telaioconsulting.github.io/): four automations for Shopify shops (customer replies, courier labels and shipping notices, stock, monthly accounts), each available on its own. The site is in Italian.

- **Live:** https://telaioconsulting.github.io/ecommerce-automations/
- **Stack:** static HTML, CSS and JavaScript, no build step and no dependencies to install. Each page is a folder with an `index.html`.
- **Shared files:** `style.css`, `motion.css`, `script.js` and `motion.js` come from the Telaio website and keep its look and motion; `site.css` holds this site's own additions (header lockup, header breakpoint, service blocks). Fonts are self-hosted in `assets/fonts/` with their SIL Open Font License files; the animation libraries (GSAP, Lenis) are in `assets/vendor/`, with versions and licences in its README. No page calls an external server.
- **Paths:** every internal link and asset uses a relative path (`style.css` from the home, `../style.css` from a page folder), so the site works both under `/ecommerce-automations/` and at the root of its own domain. Only canonical URLs, Open Graph tags, structured data and the sitemap use absolute URLs.

## Pages

| Page | Path |
|---|---|
| Home | `/` (`index.html`) |
| Clienti | `/clienti/` |
| Spedizioni | `/spedizioni/` |
| Magazzino | `/magazzino/` |
| Conti | `/conti/` |
| Come funziona | `/come-funziona/` |
| Domande frequenti | `/domande-frequenti/` |
| Chi c'è dietro | `/chi-siamo/` |
| Check-up | `/check-up/` |
| Privacy | `/privacy/` |
| Cookie | `/cookie/` |
| Not found | `404.html` |

## Publishing

GitHub Pages serves the `main` branch from the repository root (Settings, Pages, "Deploy from a branch", `main`, `/ (root)`). The empty `.nojekyll` file tells Pages to serve the files as they are. Push to `main` and the site updates in about a minute. While the site lives under `/ecommerce-automations/`, crawlers read only the `robots.txt` at the root of `telaioconsulting.github.io`, so this repo's `robots.txt` takes effect only on a custom domain; until then, submit `sitemap.xml` in Search Console or list it in the root `robots.txt`.

## Custom domain

1. Add a `CNAME` file at the root containing the domain (for example `www.example.com`), and set the same domain in Settings, Pages.
2. Point the domain's DNS to GitHub Pages (a `CNAME` record to `telaioconsulting.github.io` for a subdomain, or the GitHub Pages `A` records for an apex domain), then enable "Enforce HTTPS".
3. Replace `https://telaioconsulting.github.io/ecommerce-automations/` with the new address in the canonical, `og:url`, `og:image` and structured data of every page, in `sitemap.xml` and in `robots.txt`. Also update `twitter:image`, the site address written in the first paragraph of `privacy/index.html`, and the `/ecommerce-automations` prefix in the `<base>` script of `404.html` if the old path should no longer apply.

Relative links need no change. `404.html` works out its base folder from the address, so it works in both setups.
