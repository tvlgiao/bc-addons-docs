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

## Backing Up the Code (and Hosting It Yourself)

The two lines in Step 1 load a stylesheet and a script from jsDelivr — a free
public service that hosts files like these for a very large number of
websites.

**Is that slower than hosting them yourself?** No. jsDelivr keeps copies in
data centers around the world and serves each visitor from the one closest to
them. And because so many sites already use it, a lot of visitors' browsers
have already connected to jsDelivr before they ever reach your page. Your own
server would not be faster. Hosting the files yourself is about control, not
speed.

**Can you keep your own copy?** Yes. Here's how, and what changes if you use
it.

### Making your backup

There are two files:

```
https://cdn.jsdelivr.net/gh/tvlgiao/papathemes-cdn/bc-products/bc-products.min.css
https://cdn.jsdelivr.net/gh/tvlgiao/papathemes-cdn/bc-products/bc-products.min.js
```

For each one:

1. Paste the address into your browser and press Enter. You'll see a wall of
   text — that is the file itself.
2. Choose **File > Save As** from your browser's menu (Ctrl+S on Windows,
   Cmd+S on a Mac). If you're clicking a link to the file instead,
   right-click the link and choose **Save link as**.
3. Keep the file names exactly as they are: `bc-products.min.css` and
   `bc-products.min.js`.

That's the whole backup — two files.

There are also two optional files at the same addresses with `.map` on the end
(`bc-products.min.css.map` and `bc-products.min.js.map`). They only help a
developer trace a problem back to the original code — your feeds work fine
without them. Save them the same way if you'd like the complete set.

### Switching to your own copy

You don't need to do this now — only if you ever want to. Upload the two files
somewhere on your own site, then change **only the two web addresses** in the
Step 1 code.

Before:

```html
<link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/tvlgiao/papathemes-cdn/bc-products/bc-products.min.css">
<script async src="https://cdn.jsdelivr.net/gh/tvlgiao/papathemes-cdn/bc-products/bc-products.min.js"></script>
```

After (if you uploaded them into a folder called `bc-products` on your site):

```html
<link rel="stylesheet" href="https://www.mackite.com/bc-products/bc-products.min.css">
<script async src="https://www.mackite.com/bc-products/bc-products.min.js"></script>
```

Nothing else on the page changes. Every `<bc-products>` box stays exactly as
it is — same keys, same settings, same everything. Your `data-storefront-key`
codes belong to your BigCommerce stores, not to us, so they work the same no
matter where the script is hosted.

### The trade-off, honestly

You stop getting updates automatically. Right now, if we fix or improve
something, jsDelivr picks it up and your page gets it on its own. With your
own copy, your page keeps running the version you downloaded until you
download a newer one and upload it in its place. That's the real cost:
control instead of automatic updates.

Plenty of people keep the jsDelivr version running day to day and simply keep
the backup on hand. That's a perfectly good middle ground.

### Why a backup is genuinely enough

These are plain, ordinary CSS and JavaScript files. There is no license check,
nothing that phones home, no server of ours involved, and no key that expires.
Once you have the two files saved, they keep working — regardless of what
happens to PapaThemes, or to jsDelivr, or to anyone else. Point your page at
your own copies and the feeds keep pulling products from your BigCommerce
stores exactly as they do today.

## If Something Looks Wrong

- **No products showing?** Make sure you pasted BOTH the setup code (Step 1)
  and at least one feed box (Step 2).
- **It only works on your live website** (www.mackite.com), not when you open
  the file on your own computer.
- **Still stuck?** Send us a message and we'll check your settings.

If you'd like your own copy of the setup files to keep on hand, see [Backing Up
the Code (and Hosting It Yourself)](#backing-up-the-code-and-hosting-it-yourself).

---

Questions? Reply to your PapaThemes email and we'll help. Developers can read
the full technical guide in `docs/bc-products-guide.md`.
