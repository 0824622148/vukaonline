# Vuka Online — vukaonline.co.za

The Vuka Online marketing site. Hand-written HTML with Tailwind (Play CDN) and
Alpine.js from CDN. **No build step** — the source in this folder is what ships.

Published by **GitHub Pages** from `main` / root:
<https://github.com/0824622148/vukaonline>

| | |
|---|---|
| Live site | <https://vukaonline.co.za> |
| Preview (always current `main`) | <https://0824622148.github.io/vukaonline/> |
| Domain registrar / DNS | Afrihost (`ns.dns1.co.za`, `ns.dns2.co.za`, `ns.otherdns.net`, `ns.otherdns.com`) |
| Email | Zoho (`mx.zoho.com`) — **independent of web hosting** |
| Forms | [Web3Forms](https://web3forms.com) |

---

## Pages

| File | URL | Purpose |
|---|---|---|
| `index.html` | `/` | Landing page. Real client work under `#work`. |
| `gallery.html` | `/gallery.html` | **Starting points** — illustrative designs for *fictional* businesses, labelled "example". Not client work. |
| `privacy.html` / `terms.html` | `/privacy.html`, `/terms.html` | Legal |
| `404.html` | any unmatched path | GitHub Pages serves this automatically |
| `templates/*/index.html` | `/templates/<industry>/` | Redirect stubs for the previous site's URLs → `/gallery.html` |

---

## Making a change

```bash
cd "c:/Users/Victor/Documents/Web Design Agency/10_Website"
python -m http.server 8765     # then open http://localhost:8765
```

Edit, check locally, then:

```bash
git add -A
git commit -m "describe the change"
git push
```

GitHub Pages rebuilds in about a minute. Confirm on the preview URL before
announcing anything.

### What gets published

This folder holds ~78 MB of raw source material (`Brand activation project/`,
`assets/New Images/`, `assets/Testimonial Background Images/`, loose `.png`
originals). `.gitignore` is a **whitelist** — it ignores everything, then
re-admits only the ~2.6 MB that actually ships. If you add a new image, put it
in `assets/photos/` or `assets/logos/` as `.webp`, or it will not be published.

Check before pushing:

```bash
git ls-files | wc -l          # expect ~70
git ls-files -z | xargs -0 du -ch | tail -1   # expect ~2.6M, never 78M
```

---

## Forms

Both the contact form and the footer newsletter post to Web3Forms via
`sendToWeb3Forms()` in `index.html`. The access key lives in one place:

```js
const WEB3FORMS_KEY = 'YOUR_ACCESS_KEY_HERE';
```

Get a key free at [web3forms.com](https://web3forms.com) — you enter an email
address and the key is sent to you; there is no account to create. The key is a
public submission key and is safe to commit.

Both forms **fail closed**: if the key is missing or the request is rejected,
the visitor sees an error pointing at WhatsApp rather than a false success. Each
form carries a `botcheck` honeypot.

---

## DNS

Only these records point at the website. **Do not change `NS` or `MX`** — the
`MX` records are what keep `hello@vukaonline.co.za` working, and they are
unrelated to where the site is hosted.

| Record | Value |
|---|---|
| `A` @ | `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153` |
| `AAAA` @ | `2606:50c0:8000::153`, `:8001::153`, `:8002::153`, `:8003::153` |
| `CNAME` www | `0824622148.github.io` |

To roll back to the old Afrihost site, set the `A` record to `102.222.124.12`.
The previous site remains in `../public_html/` and on the Afrihost server.

---

## Known follow-ups

- **Tailwind Play CDN** (~3 MB) still loads at runtime. Fine for now; purging it
  means introducing a build step, which this site deliberately avoids.
- **No analytics.** Nothing is installed. Add a `gtag` snippet to `<head>` if
  wanted — note the privacy policy currently states we run no analytics cookies,
  so update that page too.
- **Company registration number** is not shown on the legal pages.

---

*Vuka Online — Be found. Be trusted. Be paid.*
