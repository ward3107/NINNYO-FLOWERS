# NINNYO FLOWERS — production landing page

Static Hebrew RTL landing page, ready for Vercel.

**Live:** https://ninnyo.vercel.app/

## Included
- Mobile-first responsive layout
- Dark / Light theme (remembers the visitor's choice)
- Editorial-botanical type system (Frank Ruhl Libre + Heebo + Cormorant Garamond, Hebrew-first)
- WhatsApp ordering flow
- Friday delivery offer and quick order form
- Call + Waze + Instagram + TikTok + Email actions
- Native Share button (`navigator.share`) with copy-link fallback
- Floating Back-to-top arrow after scrolling
- Sticky mobile action bar
- Responsive images (`srcset`/`sizes` with thumbnails) + explicit dimensions to avoid layout shift
- Preloaded hero image and preconnected fonts for a fast first paint
- SEO: canonical URL, Open Graph / Twitter cards, and `Florist` JSON-LD structured data
- Branded share image (`og-image.png`, 1200×630) so the logo shows in WhatsApp / social link previews
- Accessibility: skip-to-content link, visible focus states, reduced-motion support
- No backend; order form data is not stored

## Local preview
Open `index.html` directly, or serve the folder:

```bash
python3 -m http.server 8000   # then visit http://localhost:8000
```

## Deploy to Vercel
1. Upload the **contents of this folder** to a GitHub repository. `index.html` must be at the repository root.
2. In Vercel choose **Add New → Project**.
3. Import the repository.
4. Framework Preset: **Other**.
5. Build Command: leave empty.
6. Output Directory: leave empty or use `.`.
7. Click **Deploy**.

After deployment, the Share button will share the public Vercel URL automatically.

## Share previews (WhatsApp / social)
Link previews use the Open Graph tags in `index.html`, whose `og:image` points
to `https://ninnyo.vercel.app/api/og` — a tiny serverless function
(`api/og.js`) that returns the branded card (`og-image.png`) with a clean
`HTTP 200`.

Why a function instead of the static `og-image.png`: Vercel's CDN adds HTTP
Range support to static files, so crawlers that send a `Range` header (Facebook,
and especially WhatsApp) get a `206 Partial Content` response — which WhatsApp
rejects for preview images, so the logo never renders. The function ignores
Range and always returns `200`. The raw card is still available at
`/og-image.png` for direct/manual use.

If you move to a custom domain, update the `og:image`, `og:url`, `canonical`
and JSON-LD `url` values to match. WhatsApp/Facebook cache previews
aggressively — after a change, re-scrape in the
[Facebook Sharing Debugger](https://developers.facebook.com/tools/debug/)
(twice — the first scrape only queues the image), and for WhatsApp share the
URL once with a query suffix (e.g. `?v=2`) to bypass its cache.
