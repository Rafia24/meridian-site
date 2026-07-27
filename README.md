# Meridian — Global Stays, Real Estate & Mobility Platform

A zero-cost, single-page website + installable PWA covering all 7 verticals: Stays, Real Estate, Property Management (with a live revenue calculator), Tours, Flights, Luxury Automobiles, and a Dhaka local hub — with working lead forms that route straight to WhatsApp.

## Files

| File | Purpose |
|---|---|
| `index.html` | The entire site — structure, styling, and behavior in one file |
| `manifest.json` | PWA config (name, icons, colors) — lets phones "Add to Home Screen" |
| `sw.js` | Service worker — caches the app shell for offline/instant loading |
| `icon-192.png`, `icon-512.png` | App icons (placeholder monogram — swap for your real logo) |
| `email-templates.md` | 3 ready-to-send B2B cold outreach templates |

## 1. Before you launch — edit `CONFIG`

Open `index.html`, find the `CONFIG` block near the bottom (inside the `<script>` tag), and fill in:

```js
const CONFIG = {
  brandName: "Meridian",
  whatsappNumber: "8801XXXXXXXXX",   // your real WhatsApp number, country code, no + or spaces
  contactEmail: "hello@yourdomain.com",
  formspreeId: ""                    // optional, see step 3
};
```

Every lead form on the site (Real Estate, Host Onboarding, Automobiles) and the Dhaka "Book on WhatsApp" button all read from this one block.

## 2. Rename the brand (optional)

The working name used throughout is **Meridian**. To rename:
- Find & replace `Meridian` across `index.html` and `manifest.json`.
- Update the footer email address and copyright line.
- Regenerate `icon-192.png` / `icon-512.png` with your real logo (any square PNG works — a designer tool like Canva's free tier is fine).

## 3. (Optional) Capture leads by email too

Right now, every form submission opens WhatsApp with a pre-filled message — that's the primary, zero-setup channel. If you also want submissions emailed to you:

1. Go to [formspree.io](https://formspree.io) and create a free account (50 submissions/month free).
2. Create a form, copy its ID (looks like `xyzabc123`).
3. Paste it into `CONFIG.formspreeId` in `index.html`.

Leads are also saved to the browser's local storage on whichever device the visitor used (`localStorage['meridian_leads']`) as a fallback — this is device-local, not a real database, so don't rely on it long-term.

## 4. Deploy for free

Any of these work with $0 hosting cost:

**Netlify (easiest)**
1. Go to [app.netlify.com/drop](https://app.netlify.com/drop)
2. Drag the whole project folder in
3. You get a live URL immediately; add a custom domain later in Site Settings

**Vercel**
1. Push this folder to a GitHub repo
2. Import it at [vercel.com/new](https://vercel.com/new)
3. Deploy — no build step needed, it's static files

**Cloudflare Pages**
1. Same idea — connect a GitHub repo or drag-and-drop the folder at [pages.cloudflare.com](https://pages.cloudflare.com)

All three give free SSL and a global CDN automatically.

## 5. Connect real affiliate programs

The listings shown (Dubai apartments, Paris studios, tour prices, etc.) are placeholder content so the layout has something to show. Replace them with real widgets/links once you're approved for these programs — all have free sign-up:

- **Stays:** [Travelpayouts](https://www.travelpayouts.com), Booking.com Affiliate, Agoda Affiliate
- **Real estate:** AmberStudent, Nestpick (apply as a referral partner)
- **Tours:** [Viator Partner Program](https://www.viator.com/partner), [GetYourGuide Partner Hub](https://partner.getyourguide.com)
- **Flights:** [Travelpayouts](https://www.travelpayouts.com) (covers WayAway, Aviasales), Skyscanner Affiliate
- **Cars:** Rentalcars Affiliate, Auto Europe Affiliate

Each affiliate network gives you a unique tracking link or widget embed code — drop those into the corresponding section of `index.html` in place of the placeholder cards.

## 6. Outreach

Use `email-templates.md` for your first cold emails to property managers, real estate developers, and luxury car agencies. Personalize the first line every time — generic mail merges get filtered.

For sending infrastructure at scale, tools like Instantly.ai or Smartlead have low-cost tiers and handle domain warm-up, which matters for deliverability.

## Notes on what's real vs. placeholder

- ✅ **Real and working now:** layout, all 7 sections, WhatsApp-routed lead forms, revenue calculator, rule-based chat widget, PWA install support, offline caching.
- ⚠️ **Needs your input to go live:** your WhatsApp number, real affiliate links/widgets, real property/tour/car listings, your own icons.
- 🚫 **Not included (needs a real account, can't be faked):** a full AI chatbot (Tidio/Crisp) — the current chat widget is a lightweight rule-based FAQ that already routes to WhatsApp, which works with zero setup. If you want a true AI chatbot later, sign up for Tidio or Crisp's free tier and paste their embed script before the closing `</body>` tag.
