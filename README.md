# Vuka Landing Page

Production-ready landing page for **Vuka** — South African web design agency.

Built with: HTML5 · Tailwind CSS · Alpine.js · Formspree

---

## Before You Go Live — 2 Things to Update

### 1. WhatsApp Number
In `index.html`, find this line and replace `27XXXXXXXXX` with your actual number:

```html
href="https://wa.me/27XXXXXXXXX?text=..."
```

Format: `27` + your number without the leading zero.  
Example: `0821234567` → `27821234567`

---

### 2. Formspree (Lead Form → Your Email)

1. Go to [formspree.io](https://formspree.io) and create a free account
2. Create a new form → copy the form ID (looks like `xabc1234`)
3. In `index.html`, find this line and replace `YOUR_FORM_ID`:

```js
const FORMSPREE_ID = 'YOUR_FORM_ID';
```

Free tier: 50 submissions/month. Paid plans from $10/month for more volume.

---

## Deploy to Netlify (Recommended — Free)

1. Go to [netlify.com](https://netlify.com) → sign up free
2. Drag and drop the `10_Website/` folder onto the deploy zone
3. Your site is live instantly on a `*.netlify.app` URL
4. Add your custom domain (e.g. `vuka.co.za`) in **Site settings → Domain management**
5. Netlify handles SSL automatically (free)

**Total time to deploy: under 5 minutes.**

---

## Deploy to Vercel (Alternative)

1. Go to [vercel.com](https://vercel.com) → sign up free
2. Click **Add New → Project**
3. Import from Git or drag the folder
4. Set Framework Preset to **Other**
5. Deploy — done

---

## For Production (Remove Tailwind CDN)

The Tailwind Play CDN is fine for getting started, but for production you should purge unused styles:

```bash
npm install -D tailwindcss
npx tailwindcss -i ./input.css -o ./output.css --minify
```

Then replace the CDN `<script>` tag with a `<link>` to the minified CSS file. This reduces CSS from ~3MB to ~5KB.

---

## Template Reuse (For Client Sites)

To clone this as a template for a new client:

1. Duplicate `index.html` → rename to `clientname/index.html`
2. Find/replace these brand tokens at the top of the file:
   - `#3DBF50` → client's primary colour
   - `vuka` → client brand name
   - All copy (headlines, pricing, testimonials) → client-specific content
3. Update the Formspree ID and WhatsApp number
4. Deploy to a new Netlify site with the client's domain

**Time to launch a new client site: ~2 hours from template.**

---

## SEO Checklist

Before going live:

- [ ] Update `<title>` and `<meta name="description">` with your exact target keywords
- [ ] Update `og:url` to your actual domain
- [ ] Submit site to [Google Search Console](https://search.google.com/search-console)
- [ ] Create a `sitemap.xml` (Netlify plugin available, or use xml-sitemaps.com)
- [ ] Add Google Analytics — paste your `G-XXXXXXXX` tag into the `<head>`

### Add Google Analytics

```html
<!-- Paste before </head> -->
<script async src="https://www.googletagmanager.com/gtag/js?id=G-XXXXXXXX"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());
  gtag('config', 'G-XXXXXXXX');
</script>
```

Replace `G-XXXXXXXX` with your Measurement ID from Google Analytics.

---

## Lighthouse Targets

| Metric | Target |
|--------|--------|
| Performance | ≥ 90 |
| Accessibility | ≥ 90 |
| Best Practices | ≥ 90 |
| SEO | ≥ 90 |

Run Lighthouse in Chrome DevTools → Lighthouse tab → Generate report.

---

*Vuka — Wake Up. Get Online. Start Growing.*
