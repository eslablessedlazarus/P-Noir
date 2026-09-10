# P$ NOIR / Prime Atelier

A dark-luxury streetwear landing page: hero, product grid, brand story, CEO
section, newsletter signup, and a working shopping cart. Pure HTML/CSS/JS —
no build step, no dependencies.

## Files

```
index.html   All page markup and section content
style.css    All styling (colors/fonts as CSS variables at the top)
script.js    Cart, checkout stub, newsletter stub, smooth scroll
```

Open `index.html` in a browser to preview. No server required for the demo,
though you'll want one for the real newsletter/checkout endpoints below.

## Placeholders to replace

Search the project for `[Placeholder: ...]` and `[Placeholder ...]` — every
instance marks something to swap out before launch:

- **Product images & copy** — `index.html`, inside `.product-card` elements.
  Each card has `data-id`, `data-name`, and `data-price` attributes the cart
  reads from, so update those alongside the visible text/price.
- **"The Atelier" section** — brand-story headline, body copy, and the three
  stat callouts.
- **CEO section** — name, title, bio, portrait image, signature, and social
  links.
- **Footer** — tagline, legal page links (Shipping & Returns, Privacy Policy).
- **Newsletter section** — incentive copy.

All placeholder images currently point to `via.placeholder.com` — replace
with real product/portrait photography before launch.

## Colors & fonts

Edit the CSS variables at the top of `style.css`:

```css
:root {
  --bg-dark: #0a0a0a;
  --accent-blue: #1e50ff;
  --accent-red: #e50914;
  --accent-gold: #c9a86a;
  --font-heading: 'Cinzel', serif;
  --font-body: 'Montserrat', sans-serif;
}
```

## Cart & checkout (payment-ready, not yet connected)

The cart is fully functional on the front end: adding items, adjusting
quantity, removing items, and the running subtotal all work and persist to
`localStorage`. What's *not* wired up is an actual payment charge — that
requires a backend, because secret API keys can never live in front-end
JavaScript.

To connect a real payment provider:

1. Open `script.js` and find `PAYMENT_CONFIG` near the top.
2. Stand up a small backend endpoint (Node/Express, a serverless function,
   etc.) that takes the cart, creates a Checkout Session with your provider
   using your **secret** key, and returns `{ "url": "<redirect url>" }`.
3. Set `PAYMENT_CONFIG.checkoutEndpoint` to that endpoint's URL.
4. Set `PAYMENT_CONFIG.publishableKey` if your provider's client SDK needs
   one (Stripe does; not all providers do).

Once `checkoutEndpoint` returns a real URL, the "Proceed to Checkout" button
will redirect there automatically — no other front-end changes needed.

## Newsletter signup

The form in the `#contact` section currently just logs the submitted email
to the console. Connect it to a real provider (Mailchimp, Klaviyo, your own
backend) inside the newsletter handler in `script.js`, marked with a `TODO`.

## Known gaps to close before launch

- No real checkout backend yet (see above).
- No real email provider connected yet (see above).
- Legal pages (Shipping & Returns, Privacy Policy) are placeholder links
  with no destination.
- No favicon set.
