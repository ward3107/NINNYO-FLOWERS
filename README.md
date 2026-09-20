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
Link previews use the Open Graph tags in `index.html`, which reference an
absolute image URL on the production domain (`https://ninnyo.vercel.app/og-image.png`).
If you move to a custom domain, update the `og:image`, `og:url`, `canonical`
and JSON-LD `url` values to match. WhatsApp caches previews aggressively — to
force a refresh after a change, share the URL with a query suffix
(e.g. `?v=2`) or run it through the
[Facebook Sharing Debugger](https://developers.facebook.com/tools/debug/).
