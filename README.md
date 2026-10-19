# Telaio - Ecommerce Automations

Website of **Telaio - Ecommerce Automations**, a service by [Telaio](https://telaioconsulting.com/): five automations for Shopify shops (stock, customer replies, courier labels and shipping notices, supplier orders, monthly accounts), each available on its own, plus services built on request. The site is in Italian.

- **Live:** https://telaioconsulting.com/ecommerce-automations/ (the old https://telaioconsulting.github.io/ecommerce-automations/ addresses redirect there)
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
| Fornitori | `/fornitori/` |
| Conti | `/conti/` |
| Come funziona | `/come-funziona/` |
| Domande frequenti | `/domande-frequenti/` |
| Chi c'è dietro | `/chi-siamo/` |
| Check-up | `/check-up/` |
| Privacy | `/privacy/` |
| Cookie | `/cookie/` |
| Not found | `404.html` |

## Publishing

GitHub Pages serves the `main` branch from the repository root (Settings, Pages, "Deploy from a branch", `main`, `/ (root)`). The empty `.nojekyll` file tells Pages to serve the files as they are. Push to `main` and the site updates in about a minute. While the site lives under `/ecommerce-automations/`, crawlers read only the `robots.txt` at the root of `telaioconsulting.com` (the Telaio site), which lists this site's `sitemap.xml`; this repo's `robots.txt` takes effect only on a domain of its own.

## Custom domain

The site has no domain of its own: as a project site of the `telaioconsulting` account it follows the domain of the Telaio site (`telaioconsulting.com`, set there with a `CNAME` file), so it is served at `https://telaioconsulting.com/ecommerce-automations/`. Every absolute address in the pages (canonical, `og:url`, `og:image`, `twitter:image`, structured data, `sitemap.xml`, `robots.txt`, the site address in the first paragraph of `privacy/index.html`) uses that address.

To give it a domain of its own later:

1. Add a `CNAME` file at the root containing the domain (for example `automazioni.example.com`), and set the same domain in Settings, Pages.
2. Point the domain's DNS to GitHub Pages (a `CNAME` record to `telaioconsulting.github.io` for a subdomain, or the GitHub Pages `A` records for an apex domain), then enable "Enforce HTTPS".
3. Replace `https://telaioconsulting.com/ecommerce-automations/` with the new address in the places listed above, and the `/ecommerce-automations` prefix in the `<base>` script of `404.html`.
