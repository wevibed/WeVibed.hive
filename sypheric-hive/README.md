# Sypheric Hive — Cloudflare Pages storefront

A static, mobile-responsive streetwear storefront featuring the animated clothing rail, interactive product discovery, product detail view, catalogue browsing, and WhatsApp enquiry/order flow.

## Product-data integrity

The current storefront is delivered as a self-contained HTML application at `public/index.html`. Its existing demo catalogue and product interactions are preserved as supplied in the approved preview. The catalogue contains illustrative/demo product data; confirm actual stock, prices, variants, and product photography with the shop before treating them as live inventory.

The rail and catalogue use the same product data in the page. Do not create a second hardcoded rail catalogue when extending the site. For genuine front/back inspection, add verified back-view images to the relevant product records; the interface must not fabricate missing product angles.

## Deploy to Cloudflare Pages

### Option A — GitHub-connected deployment

1. Push this repository to GitHub.
2. In Cloudflare Dashboard, open **Workers & Pages → Create → Pages → Connect to Git**.
3. Select this repository.
4. Set the build configuration:
   - Framework preset: **None**
   - Build command: `npm run build`
   - Build output directory: `dist`
   - Root directory: `/`
5. Deploy.

### Option B — Wrangler CLI

Requirements: Node.js 20+ and a Cloudflare account authenticated with Wrangler.

```bash
npm install
npx wrangler login
npm run build
npx wrangler pages project create sypheric-hive
npx wrangler pages deploy dist --project-name=sypheric-hive
```

If the Pages project already exists, skip `pages project create`.

## Local preview

```bash
npm install
npm run build
npx wrangler pages dev dist
```

Then open the local URL printed by Wrangler.

## WhatsApp configuration

The storefront currently uses Zimbabwe WhatsApp number `263790321412` (displayed as `+263 790 321 412`). Search `public/index.html` for that number if the shop's contact number changes. Keep it in international format without the leading local zero.

## Important notes

- This is a static storefront; no Worker API, database, customer accounts, or online payment gateway is included or required for this deployment.
- Product enquiries/orders are handed off to WhatsApp.
- No environment variables are required for the current build.
- Do not describe demo products/prices as verified stock until the business confirms them.
