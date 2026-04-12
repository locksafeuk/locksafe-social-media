# LockSafe – Social Media Feeds Integration Guide

**Prepared:** 12 April 2026  
**For:** LockSafe.uk (www.locksafe.uk)  
**Companion file:** `social_media_feeds_integration.html` (open in a browser to see live demos)

---

## Quick Summary

| Platform | Free Official Embed? | Difficulty | Recommended Approach |
|---|---|---|---|
| Facebook | ✅ Yes – Page Plugin | Easy | iframe embed |
| Twitter / X | ✅ Yes – Embedded Timeline | Easy | `<a>` tag + script |
| LinkedIn | ⚠️ Follow button only | Medium | Third-party widget (Elfsight / Curator.io) |
| Google Reviews | ❌ No official widget | Medium | Third-party widget or manual cards |

---

## Understanding Your Website

Based on our analysis, **LockSafe.uk is a custom-built, single-page landing site** — it does not use WordPress, Wix, Squarespace, or another CMS. This means:

- You (or your developer) will need to **edit the HTML source code** directly.
- There are no drag-and-drop "widget" panels. You paste code snippets into the HTML file.
- If you have a developer or agency managing the site, simply **send them this guide and the companion HTML file** — they'll know what to do.

### Where to Place Social Feeds on LockSafe.uk

Given the site's conversion-focused design, we recommend a **layered approach**:

| Location | What to Add | Why |
|---|---|---|
| **Footer** (bottom of every page) | Social media follow icons (Facebook, X, LinkedIn, Google) | Non-intrusive; lets visitors follow you without disrupting the "Get Help" flow |
| **Customer Reviews section** | Google Reviews widget (replaces or supplements the static reviews) | Adds live social proof; builds trust automatically |
| **New "Community" or "Blog" page** | Full Facebook + Twitter feeds | Keeps the main landing page clean; gives returning visitors fresh content |

> **⚠️ Important:** Do NOT add bulky social feeds directly onto the main hero/CTA area. The current design is optimised for emergency conversions — keep it lean.

---

## Platform 1: Facebook Page Feed

### What You Need
- A **Facebook Business Page** (e.g. `facebook.com/LockSafeUK`)
- The page must be **published** (not unpublished or in draft)

### Step-by-Step

#### Step 1 – Open the Facebook Page Plugin Tool
Go to: **https://developers.facebook.com/docs/plugins/page-plugin/**

#### Step 2 – Configure the Widget
Fill in the fields:

| Field | Value |
|---|---|
| Facebook Page URL | `https://www.facebook.com/LockSafeUK` (use your actual page URL) |
| Tabs | `timeline` (or `timeline, events, messages`) |
| Width | `340` (adjust to fit your layout, max 500) |
| Height | `500` |
| Use Small Header | ✅ Yes |
| Adapt to plugin container width | ✅ Yes |
| Hide Cover Photo | Your choice |
| Show Friend's Faces | ✅ Yes |

#### Step 3 – Get the Code
Click **"Get Code"**. Facebook gives you two options:
- **JavaScript SDK** – a `<div>` tag + a script block
- **iFrame** – a single `<iframe>` tag (simpler, recommended)

**We recommend the iFrame method** for simplicity.

#### Step 4 – Paste Into Your Website
Copy the iframe code and paste it into your HTML where you want the feed to appear.

```html
<iframe
  src="https://www.facebook.com/plugins/page.php?href=https%3A%2F%2Fwww.facebook.com%2FLockSafeUK&tabs=timeline&width=340&height=500&small_header=true&adapt_container_width=true&hide_cover=false&show_facepile=true"
  width="340"
  height="500"
  style="border:none;overflow:hidden;max-width:100%;"
  scrolling="no"
  frameborder="0"
  allowfullscreen="true"
  allow="autoplay; clipboard-write; encrypted-media; picture-in-picture; web-share"
  loading="lazy">
</iframe>
```

> **Replace** `LockSafeUK` with your actual Facebook page name/slug.

#### Troubleshooting
- **Widget shows blank?** Make sure your page is published and not restricted by country/age.
- **Widget too wide/narrow?** Adjust the `width` parameter (min 180, max 500).
- **Posts not showing?** The page must have public posts; check your page's privacy settings.

---

## Platform 2: Twitter / X Timeline

### What You Need
- A **Twitter/X account** (e.g. `@LockSafeUK`)
- The account must be **public** (not protected)

### Step-by-Step

#### Step 1 – Open the Twitter Publish Tool
Go to: **https://publish.twitter.com**

#### Step 2 – Enter Your Profile URL
Paste your Twitter profile URL:
```
https://twitter.com/LockSafeUK
```
Press Enter.

#### Step 3 – Choose "Embedded Timeline"
Twitter will show two options — choose **"Embedded Timeline"** (the left option).

#### Step 4 – Customise (Optional)
Click **"Set customisation options"** to adjust:

| Option | Recommended Value |
|---|---|
| Height | `500` (pixels) |
| Width | Leave blank (auto-fills container) |
| Theme | `Light` (matches LockSafe's design) |
| Language | `English` |

#### Step 5 – Copy the Code
Click **"Copy Code"**. You'll get something like:

```html
<a class="twitter-timeline"
   data-height="500"
   data-theme="light"
   data-chrome="noheader nofooter noborders"
   href="https://twitter.com/LockSafeUK">
   Tweets by @LockSafeUK
</a>
<script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>
```

#### Step 6 – Paste Into Your Website
- Paste the `<a>` tag wherever you want the timeline to appear.
- Paste the `<script>` tag **once** on the page (ideally near the bottom, before `</body>`).

> **Replace** `LockSafeUK` with your actual X/Twitter handle.

#### Customisation Options (data-chrome)
You can add these values to `data-chrome` to adjust appearance:
- `noheader` – removes the header
- `nofooter` – removes the footer
- `noborders` – removes borders
- `transparent` – transparent background
- `noscrollbar` – hides scrollbar

Combine with spaces: `data-chrome="noheader nofooter noborders"`

#### Troubleshooting
- **"Nothing to see here"?** Your account may have no recent tweets, or it's protected.
- **Widget not loading?** Check that the `widgets.js` script is included and not blocked by ad blockers.

---

## Platform 3: LinkedIn Company Feed

### What You Need
- A **LinkedIn Company Page** (e.g. `linkedin.com/company/locksafe`)
- Admin access to the page

### The Situation
LinkedIn does **NOT** offer a free embedded timeline/feed widget like Facebook or Twitter. Your options are:

### Option A: LinkedIn Follow Button (Free, Official) ✅

This adds a small "Follow" button that encourages visitors to follow your LinkedIn page.

#### Step 1 – Add the LinkedIn Platform Script
Add this once in your page (ideally in the `<head>` or near the end of `<body>`):

```html
<script src="https://platform.linkedin.com/in.js" type="text/javascript">lang: en_US</script>
```

#### Step 2 – Add the Follow Button
Place this where you want the button:

```html
<script type="IN/FollowCompany" data-id="YOUR_COMPANY_ID" data-counter="bottom"></script>
```

#### How to Find Your Company ID
1. Go to your LinkedIn Company Page
2. Click **"Admin tools"** → **"Page info"** (or check the URL)
3. Your company page URL looks like: `linkedin.com/company/locksafe` — the slug is `locksafe`
4. For the numeric ID: view page source or use a LinkedIn ID lookup tool

### Option B: Third-Party Feed Widget (Recommended for Full Feed) ⭐

These services pull your LinkedIn posts and display them as a beautiful widget:

| Service | Free Plan? | Website |
|---|---|---|
| **Elfsight** | ✅ Yes (with branding) | [elfsight.com/linkedin-feed-widget](https://elfsight.com/linkedin-feed-widget/) |
| **Curator.io** | ✅ Yes (limited) | [curator.io](https://curator.io) |
| **Tagembed** | ✅ Yes (with branding) | [tagembed.com/linkedin-widget](https://tagembed.com/linkedin-widget/) |
| **Juicer** | ✅ Yes (1 feed, with branding) | [juicer.io](https://www.juicer.io) |

#### How to Set Up (Elfsight Example)
1. Go to [elfsight.com](https://elfsight.com) and create a free account
2. Choose **"LinkedIn Feed"** widget
3. Connect your LinkedIn Company Page URL
4. Customise colours, layout, number of posts
5. Click **"Add to website"** — you'll get a code snippet like:

```html
<script src="https://static.elfsight.com/platform/platform.js" async></script>
<div class="elfsight-app-XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX" data-elfsight-app-lazy></div>
```

6. Paste this code into your website HTML where you want the feed

### Option C: Manual Approach
Periodically copy key LinkedIn posts and add them as styled cards on your website. This gives full design control but requires manual updates.

---

## Platform 4: Google Business Reviews

### What You Need
- A **Google Business Profile** (claimed and verified)
- Reviews on your profile

### The Situation
Google does **NOT** provide an official embeddable reviews widget. Your options are:

### Option A: Third-Party Widget (Easiest) ⭐

| Service | Free Plan? | Website |
|---|---|---|
| **Elfsight** | ✅ Yes | [elfsight.com/google-reviews-widget](https://elfsight.com/google-reviews-widget/) |
| **EmbedSocial** | ✅ Trial | [embedsocial.com](https://embedsocial.com) |
| **Tagembed** | ✅ Yes | [tagembed.com/google-reviews-widget](https://tagembed.com/google-reviews-widget/) |
| **Widget.io** | ✅ Yes | [widget.io](https://widget.io) |

#### How to Set Up (Elfsight Example)
1. Go to [elfsight.com](https://elfsight.com) and create an account (or use an existing one)
2. Choose **"Google Reviews"** widget
3. Search for your business by name or paste your Google Maps URL
4. Customise:
   - Layout: Grid, List, Slider, or Badge
   - Minimum star rating to show (e.g. 4+ stars only)
   - Colours to match LockSafe's brand (dark blue `#0f3460`, white)
5. Copy the embed code and paste into your HTML

```html
<script src="https://static.elfsight.com/platform/platform.js" async></script>
<div class="elfsight-app-YOUR-WIDGET-ID" data-elfsight-app-lazy></div>
```

### Option B: Google Places API (Advanced)
For developers who want full control:

1. Get a **Google Cloud API key** with Places API enabled
2. Use the Place Details endpoint to fetch reviews
3. Render them with custom HTML/CSS

```javascript
// Example API call (requires server-side proxy to protect API key)
fetch(`/api/google-reviews?place_id=YOUR_PLACE_ID`)
  .then(res => res.json())
  .then(data => {
    data.reviews.forEach(review => {
      // Render each review card
    });
  });
```

> **Note:** Google's Terms of Service require that reviews link back to Google Maps. Always include a "View on Google" link.

### Option C: Manual Review Cards
Copy your best reviews from Google and display them as styled HTML cards. See the companion HTML file for ready-made card designs.

---

## Adding Footer Social Icons (Quick Win) 🏆

This is the **easiest and most impactful first step**. It takes 5 minutes and doesn't disrupt your current design.

### The Code

Paste this into your website's footer section (look for `<footer>` or the bottom section of your HTML):

```html
<div style="display:flex;justify-content:center;gap:16px;padding:24px 0;">
  <a href="https://facebook.com/YOUR_PAGE" target="_blank" rel="noopener" aria-label="Facebook"
     style="width:42px;height:42px;border-radius:50%;background:#1877F2;display:flex;align-items:center;justify-content:center;color:#fff;text-decoration:none;font-weight:700;">f</a>
  <a href="https://twitter.com/YOUR_HANDLE" target="_blank" rel="noopener" aria-label="Twitter"
     style="width:42px;height:42px;border-radius:50%;background:#000;display:flex;align-items:center;justify-content:center;color:#fff;text-decoration:none;font-weight:700;">𝕏</a>
  <a href="https://linkedin.com/company/YOUR_SLUG" target="_blank" rel="noopener" aria-label="LinkedIn"
     style="width:42px;height:42px;border-radius:50%;background:#0A66C2;display:flex;align-items:center;justify-content:center;color:#fff;text-decoration:none;font-weight:700;">in</a>
  <a href="https://g.page/YOUR_BUSINESS" target="_blank" rel="noopener" aria-label="Google"
     style="width:42px;height:42px;border-radius:50%;background:#4285F4;display:flex;align-items:center;justify-content:center;color:#fff;text-decoration:none;font-weight:700;">G</a>
</div>
```

**Replace:**
- `YOUR_PAGE` → your Facebook page name
- `YOUR_HANDLE` → your Twitter/X username
- `YOUR_SLUG` → your LinkedIn company slug
- `YOUR_BUSINESS` → your Google Business short name

---

## Recommended Implementation Order

Here's a prioritised plan — start with the easiest wins:

### Phase 1 – Immediate (30 minutes) ✅
1. **Add social media follow icons to the footer** — simple, non-disruptive, huge value
2. **Add Facebook Page Plugin** to a suitable section — free, official, easy

### Phase 2 – This Week (1–2 hours) 📋
3. **Add Twitter/X Embedded Timeline** — free, official, easy
4. **Set up Google Reviews widget** via Elfsight (free plan) — replaces static reviews with live ones

### Phase 3 – Next Sprint (2–4 hours) 🔄
5. **Set up LinkedIn feed** via Elfsight or Curator.io
6. **Consider creating a dedicated "Community" or "News" page** for the full social feeds
7. **Test everything on mobile** — all widgets should be responsive

---

## All-In-One Widget Services

If you want a single service to handle ALL your social feeds in one place, these aggregators can pull from Facebook, Twitter, LinkedIn, Google, Instagram, and more:

| Service | Platforms Supported | Free Plan | Best For |
|---|---|---|---|
| [Curator.io](https://curator.io) | All major | ✅ 1 feed | Clean, modern layouts |
| [Juicer.io](https://juicer.io) | All major | ✅ 1 feed | Simple setup |
| [Elfsight](https://elfsight.com) | All major (separate widgets) | ✅ Per widget | Most customisable |
| [Tagembed](https://tagembed.com) | All major | ✅ Limited | Budget-friendly |
| [EmbedSocial](https://embedsocial.com) | All major | Trial only | Full-featured |

> **Our recommendation for LockSafe:** Start with **Elfsight** — they have free tiers for each widget type, good customisation, and the embed code is just two lines to paste.

---

## Troubleshooting & FAQ

### Q: The Facebook widget shows a blank box?
**A:** Your Facebook Page must be published and set to public. Go to Page Settings → General → Page Visibility → "Page Published".

### Q: Twitter feed says "Nothing to see here"?
**A:** Your Twitter account may be protected (private). Go to Settings → Privacy → uncheck "Protect your Tweets".

### Q: Widgets slow down my website?
**A:** Add `loading="lazy"` to iframes. For third-party scripts, they typically load asynchronously and shouldn't block your page. If speed is critical, consider loading widgets only when the user scrolls to them.

### Q: Can I style the widgets to match LockSafe's brand?
**A:** 
- **Facebook:** Limited styling (can set small header, hide cover)
- **Twitter:** Can set light/dark theme, remove header/footer/borders
- **Elfsight widgets:** Full colour and layout customisation
- **Manual cards:** Complete design control

### Q: I don't have developer access to my website?
**A:** Send this guide and the HTML demo file to whoever manages your website. They'll have everything they need. If you use a website builder, check if it supports "Custom HTML" or "Embed Code" blocks.

### Q: How do I find my Google Business Place ID?
**A:** Go to [https://developers.google.com/maps/documentation/places/web-service/place-id-finder](https://developers.google.com/maps/documentation/places/web-service/place-id-finder), search for your business, and copy the Place ID.

---

## Files Delivered

| File | Description |
|---|---|
| `social_media_feeds_integration.html` | Interactive demo with live embeds, placeholders, and copy-paste code snippets |
| `social_media_integration_guide.md` | This guide — step-by-step instructions for every platform |
| `locksafe_website_analysis.md` | Website analysis informing these recommendations |

---

*Guide prepared for LockSafe.uk — April 2026*
