# Bazarek Deals

A public deals shop that runs on GitHub Pages. Prices are in PLN, and payment goes through Stripe Payment Links.

## How to add a product

1. **Make a Stripe Payment Link.** In the Stripe Dashboard, go to Payment Links, then New. Set the price in PLN and turn on "Collect customers' addresses" so you know where to ship. Copy the link. It starts with `https://buy.stripe.com/`.
2. **Upload the photo.** Open the `images` folder on GitHub and choose Add file, then Upload files. Use square photos, about 800 × 800 px, under 300 KB.
3. **Add the product to `products.json`.** Open the file, click the pencil icon and add a block like the one below. Separate products with commas. Then click Commit changes.

```json
[
  {
    "id": "led-night-light",
    "title": "Magnetic LED night light, USB-C rechargeable",
    "price": 24.99,
    "was": 59.99,
    "category": "Home",
    "description": "Motion sensor, 3 brightness levels, sticks to any metal surface.",
    "image": "led-night-light.jpg",
    "stripe_link": "https://buy.stripe.com/xxxxxxxx",
    "shop": "Bazarek Deals",
    "added": "2026-10-08"
  }
]
```

| Field | Required | Notes |
|---|---|---|
| `id` | yes | Short, unique, lowercase, with dashes. Used for sharable links like `…/#led-night-light`. |
| `title` | yes | Shown on the card and in Google results. |
| `price` | yes | In złoty. Use a dot for decimals: `24.99`. |
| `was` | no | Old price. Adds a red `-58%` badge. Products at 50% off or more appear in Lightning deals. |
| `category` | yes | One of: Home, Gadgets, Fashion, Beauty, Kitchen, Toys, Sports, Other. |
| `description` | no | Plain text. |
| `image` | no | A file name from the `images` folder, or a full `https://` image URL. |
| `stripe_link` | yes | Must start with `https://buy.stripe.com/`. Without it, the Buy button stays hidden. |
| `shop` | no | Seller name. Useful if friends sell through your site. |
| `added` | no | Date as `YYYY-MM-DD`. Items from the last 7 days get a NEW badge. |

The site updates about a minute after you commit.

**Check your edits:** one missing comma breaks the whole list, and the page then says "Products couldn't load". Paste the file into https://jsonlint.com to find the mistake.

## Letting friends sell

Add them as collaborators under Settings, then Collaborators. Each friend makes their own Stripe link, so the money goes straight to them. Their products go in the same `products.json`, with their name in `shop`.

## Getting found on Google

1. Open https://search.google.com/search-console and add your site URL as a URL prefix property.
2. Verify ownership with the HTML file method by uploading Google's file to this repository.
3. Submit `sitemap.xml` under Sitemaps.

Google usually indexes a new site within a few days to a few weeks.

## Before you start selling (Poland)

Selling regularly counts as running a business. Check whether you can use *działalność nierejestrowana* (unregistered activity, allowed under an income limit) or need to register a business. Add a shop policy page covering returns (14 days for online purchases in the EU), your contact details and privacy. Stripe will also ask you to verify your identity before it pays out.
