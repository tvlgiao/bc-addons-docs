# Setting Up Your Product Feeds

These feed boxes show live products from your Mackite stores right on your
page — new arrivals, sale items, and so on. Every time someone visits, they
see a slightly different mix of products, so the page never feels stale.

Setting it up is just copying and pasting a bit of code. No design work, no
technical skills needed.

## Before You Start

We've already filled in your store details for you, so the code below is
ready to paste as-is.

## Step 1 — Add the Setup Code Once

Paste this near the top of your page, inside the `<head>` section. You only
do this once per page.

```html
<!-- Paste this in your <head> -->
<link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/tvlgiao/papathemes-cdn/bc-products/bc-products.min.css">
<script async src="https://cdn.jsdelivr.net/gh/tvlgiao/papathemes-cdn/bc-products/bc-products.min.js"></script>
```

If we send you an update and you don't see it, add `?v=2` to the end of both web addresses (change the number each time).

## Step 2 — Add Your Feed Boxes

Paste each feed box wherever you want those products to appear. You have
**two separate stores**, so we've prepared feeds for both:

| Store | Website | Feeds |
|---|---|---|
| Boardsports | www.mackiteboarding.com | New Arrivals + On Sale |
| Toy | shop.mackite.com | New Arrivals + On Sale |

> **Important — each store has its own key.** The long `data-storefront-key`
> code is what tells a box *which store* to pull products from. The
> Boardsports boxes use the Boardsports key; the Toy boxes use the Toy key.
> They are different — don't copy one store's key into the other store's box.
> Just paste each box below exactly as-is and you're set.

### Store 1 — Boardsports (www.mackiteboarding.com)

**New Arrivals:**

```html
<bc-products
  style="--bc-h-lg: 720px; --bc-h-sm: 520px"
  data-store-url="https://www.mackiteboarding.com"
  data-storefront-key="eyJ0eXAiOiJKV1QiLCJhbGciOiJFUzI1NiJ9.eyJjaWQiOlsxXSwiY29ycyI6WyJodHRwczovL3d3dy5tYWNraXRlLmNvbSJdLCJlYXQiOjE5NDExNzQ5NjUsImlhdCI6MTc4MzQ5NDk2NywiaXNzIjoiQkMiLCJzaWQiOjMxMTU4Niwic3ViIjoianRrb2plMW9mdmNqbGhmZjcybXNlanVsbnNmZTdodCIsInN1Yl90eXBlIjoyLCJ0b2tlbl90eXBlIjoxfQ.mFcH6aViTiHlfAr7I1Rcv-VKZAv6VCztL2Sfic9v3C-GbCv33bqdpUlZJur2P_-0LqxLsKku0uySdsq2KLpfJw"
  data-type="new"
  data-store-label="Boardsports"
  data-title="New Arrivals"
  data-view-all="https://www.mackiteboarding.com/"
  data-view-all-text="View more"
  data-accent="#8a6d00"
  data-accent-dark="#e6b400"
  data-description="true">
</bc-products>
```

**On Sale:**

```html
<bc-products
  style="--bc-h-lg: 720px; --bc-h-sm: 520px"
  data-store-url="https://www.mackiteboarding.com"
  data-storefront-key="eyJ0eXAiOiJKV1QiLCJhbGciOiJFUzI1NiJ9.eyJjaWQiOlsxXSwiY29ycyI6WyJodHRwczovL3d3dy5tYWNraXRlLmNvbSJdLCJlYXQiOjE5NDExNzQ5NjUsImlhdCI6MTc4MzQ5NDk2NywiaXNzIjoiQkMiLCJzaWQiOjMxMTU4Niwic3ViIjoianRrb2plMW9mdmNqbGhmZjcybXNlanVsbnNmZTdodCIsInN1Yl90eXBlIjoyLCJ0b2tlbl90eXBlIjoxfQ.mFcH6aViTiHlfAr7I1Rcv-VKZAv6VCztL2Sfic9v3C-GbCv33bqdpUlZJur2P_-0LqxLsKku0uySdsq2KLpfJw"
  data-type="sale"
  data-category-id="556,619,622,620,227"
  data-store-label="Boardsports"
  data-title="On Sale"
  data-view-all="https://www.mackiteboarding.com/sale-kiteboarding-gear/"
  data-view-all-text="View more"
  data-accent="#8a6d00"
  data-accent-dark="#e6b400"
  data-description="true">
</bc-products>
```

### Store 2 — Toy (shop.mackite.com)

**New Arrivals:**

```html
<bc-products
  style="--bc-h-lg: 720px; --bc-h-sm: 520px"
  data-store-url="https://shop.mackite.com"
  data-storefront-key="eyJ0eXAiOiJKV1QiLCJhbGciOiJFUzI1NiJ9.eyJjaWQiOlsxXSwiY29ycyI6WyJodHRwczovL3d3dy5tYWNraXRlLmNvbSJdLCJlYXQiOjE5NDExNzQ5NjUsImlhdCI6MTc4MzQ5NDk2NSwiaXNzIjoiQkMiLCJzaWQiOjMyNzU4MCwic3ViIjoiMWVyOW5xenB3NDk0a2g0N2xheTZnMHhwaTd6a2ZlcyIsInN1Yl90eXBlIjoyLCJ0b2tlbl90eXBlIjoxfQ.nGRESya-a5lCh2qGPRjzyO4NdhBsw9i2IsJQory-q9ijKzU-EIrBKOLeH_7sJZF89fYalxZoiIp4aCAeEuQILQ"
  data-type="new"
  data-store-label="Toy"
  data-title="New Arrivals"
  data-view-all="https://shop.mackite.com/"
  data-view-all-text="View more"
  data-accent="#6d28d9"
  data-accent-dark="#b794f6"
  data-description="true">
</bc-products>
```

**On Sale:**

```html
<bc-products
  style="--bc-h-lg: 720px; --bc-h-sm: 520px"
  data-store-url="https://shop.mackite.com"
  data-storefront-key="eyJ0eXAiOiJKV1QiLCJhbGciOiJFUzI1NiJ9.eyJjaWQiOlsxXSwiY29ycyI6WyJodHRwczovL3d3dy5tYWNraXRlLmNvbSJdLCJlYXQiOjE5NDExNzQ5NjUsImlhdCI6MTc4MzQ5NDk2NSwiaXNzIjoiQkMiLCJzaWQiOjMyNzU4MCwic3ViIjoiMWVyOW5xenB3NDk0a2g0N2xheTZnMHhwaTd6a2ZlcyIsInN1Yl90eXBlIjoyLCJ0b2tlbl90eXBlIjoxfQ.nGRESya-a5lCh2qGPRjzyO4NdhBsw9i2IsJQory-q9ijKzU-EIrBKOLeH_7sJZF89fYalxZoiIp4aCAeEuQILQ"
  data-type="sale"
  data-category-id="42"
  data-store-label="Toy"
  data-title="On Sale"
  data-view-all="https://shop.mackite.com/sale/"
  data-view-all-text="View more"
  data-accent="#6d28d9"
  data-accent-dark="#b794f6"
  data-description="true">
</bc-products>
```

## Step 3 — Save and Check

Save your page and open it on your live website. Your products appear in a
few seconds.

## Simple Things You Can Change (Optional)

| Want to change... | Edit this |
|---|---|
| The heading text | `data-title="On Sale"` — swap in your own words |
| How tall the box is | The number in `style="--bc-h-lg: 720px"` — bigger number = taller. The default shows about 2 rows |
| Which sale categories show | The numbers in `data-category-id="..."` — each store's On Sale box has its own category ID numbers (Boardsports and Toy are different) |
| Show/hide the short product description | `data-description="true"` shows a short description under each price. Change it to `"false"` (or remove the line) to hide descriptions |

## If Something Looks Wrong

- **No products showing?** Make sure you pasted BOTH the setup code (Step 1)
  and at least one feed box (Step 2).
- **It only works on your live website** (www.mackite.com), not when you open
  the file on your own computer.
- **Still stuck?** Send us a message and we'll check your settings.

---

Questions? Reply to your PapaThemes email and we'll help. Developers can read
the full technical guide in `docs/bc-products-guide.md`.
