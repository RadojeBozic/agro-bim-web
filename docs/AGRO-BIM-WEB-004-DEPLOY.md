# Agro BiM — staging deployment

- Build: `npm.cmd run build`
- Publish directory: `dist/`
- Suggested staging host: `agrobim-preview.express-web.express`
- Production domain: `https://agro-bim.com/`

## Before deployment

1. Point the staging DNS record at the selected hosting service and allow time for DNS propagation.
2. Require HTTPS and redirect HTTP to HTTPS.
3. Keep the production canonical URL unchanged on staging.
4. Prefer HTTP Basic Auth on staging. Otherwise configure an `X-Robots-Tag: noindex, nofollow` response header at the host. Do not add `noindex` to the production build.

## Verification

- Confirm the homepage, images, favicon, `robots.txt`, and `sitemap-index.xml` return `200`.
- Check navigation, anchor links, phone/email links, Instagram, and Agro BiM Digital.
- Test at mobile, tablet, and desktop widths.
- Verify the canonical and social metadata still reference `https://agro-bim.com/`.
- Confirm HTTPS has no mixed-content warnings.

## Rollback

Keep the previously deployed `dist/` artifact or hosting release available and restore it if verification fails. DNS rollback should be the last resort because propagation is not immediate.
