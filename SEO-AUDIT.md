# SEO Audit — comehomerian / thenektarnetwork.com

*Audited 2026-09-03 against the current `main` deploy (Netlify project `comehomerian`, deploy state: ready). Covers: indexing status, title tags, meta descriptions, heading structure, image alt text, and URL slugs.*

## TL;DR

1. **The site is not indexed anywhere, and can't be right now.** Netlify's visitor-access gate is on (team login required — switched from the Basic-password setup noted 2026-08-28), so every visitor including Googlebot is turned away. `site:` searches confirm zero indexed pages for `comehomerian.netlify.app` and `thenektarnetwork.com`. This is *correct* for pre-launch — but it means none of the launch SEO basics exist yet either.
2. **Even with the gate off, Google would see almost nothing.** The page it receives is the bundler's loader shell: `<title>Bundled Page</title>`, no meta description, no headings, no links, no text. The real page unpacks client-side out of a 21 MB single file. That architecture is the root cause of most findings below.
3. **The only thing Google currently associates with the brand is the *old* site.** `hillsinteriordesign.com` is indexed — serving an old Showit build whose homepage title is literally "Mexica – Modern and Elegant Showit template" with generic template copy. Deciding what happens to that domain is as important as anything in the new build.
4. **Alt text is the one healthy area.** 13 of 16 images have good, specific alt text; the two empty ones on decorative bees are correct as-is. Only the header logo needs a fix.

Ownership note: HANDOFF.md assigns "SEO / content strategy" to Rian's marketing company — this doc is the baseline to hand them.

---

## 1. Is the site indexed at all?

**No — zero pages on any Nektar domain.** Verified 2026-09-03.

| Domain | Google index | Current state |
|---|---|---|
| `comehomerian.netlify.app` | **0 pages** | Live but gated (Netlify access control: team login required, sitewide) |
| `thenektarnetwork.com` | **0 pages** | Now attached as the **primary domain** on the Netlify project; same gate applies |
| `nektarnetwork.com` / `.store` | **0 pages** | 301 rules exist in `_redirects` → `/nektar` and `/shop`; only take effect if the domains are added as Netlify aliases (verify — DNS work is issue #12) |
| `hillsinteriordesign.com` | **Indexed** | Old Showit site with template-default titles/copy ("Mexica – Modern and Elegant Showit template", generic "luxury design team" About page) |

Why zero: the access gate answers every request (including `robots.txt` and Googlebot) with a login wall, which guarantees non-indexing. On top of that:

- **No `robots.txt`** in the repo — nothing tells crawlers what to do once the gate lifts.
- **No `sitemap.xml`** — and no way for Google to discover the section URLs otherwise, since the page contains no crawlable internal links (navigation is JS `onClick`, not `<a href>`).
- **No Google Search Console / Bing Webmaster setup** mentioned anywhere in HANDOFF or the repo.
- **`/*  /index.html  200` catch-all** in `_redirects` means *any* URL (including typos) returns HTTP 200 with the same page — a soft-404 factory once the site is live.
- The old-site situation cuts both ways: `hillsinteriordesign.com` has age and (some) authority. Redirecting it into the new site's `/design` section at launch transfers that; leaving it serving template filler actively hurts brand searches for "Hills Interior Design."

## 2. Title tags

**One title for the whole site, and it's the export default:**

```html
<title>Bundled Page</title>
```

That's what shows in the browser tab today, what Google would display as the clickable headline, and what a share preview falls back to. `document.title` is never updated — not on load, not on route change — so all seven routes share it.

Suggested per-route titles (from the site's own copy; pair with the matching description below):

| Route | Suggested title |
|---|---|
| `/` | Rian Hills — Interior Design, Staging & The Nektar Network |
| `/design` | Hills Interior Design — Kansas City & Overland Park |
| `/staging` | Hills Home Staging — Kansas City & Overland Park |
| `/nektar` | The Nektar Network — Come Home with Rian Hills |
| `/shop` | Shop Rian's Edit — The Dopamine Designer |
| `/rian` | Rian Hills — The Dopamine Designer |
| `/contact` | Work With Us — Rian Hills |

Cheapest immediate fix: hand-edit the outer shell's `<title>` (line 5 of `index.html`) to the `/` title, and set `document.title` inside the app's `go(route)` handler for the rest. Real per-route titles in the served HTML need prerendering (see §7).

## 3. Meta descriptions

**None. Anywhere.** Also missing from the `<head>`: canonical URL, Open Graph tags (`og:title` / `og:description` / `og:image`), Twitter card, favicon, and `lang` on `<html>` (both the outer and inner documents are bare `<html>`). A text or iMessage/Slack share of the site today renders with no image, no description, and "Bundled Page" as the headline.

Suggested descriptions (~150 chars, from existing copy):

| Route | Suggested meta description |
|---|---|
| `/` | Award-winning interior design and home staging in Kansas City and Overland Park, the Come Home podcast, and Rian's curated shop. Come home to a life that feels like you. |
| `/design` | Full-service interiors by 2025's Interior Designer of the Year (Kansas City & Overland Park). Rooms that hold up on an ordinary Tuesday — designed for how you want to feel. |
| `/staging` | Strategic, story-led home staging for occupied and vacant properties in Kansas City and Overland Park. Make buyers feel at home before they live there. |
| `/nektar` | Honest conversations about identity, healing, the body, and the spaces we inhabit. Long conversations, no rush to get anywhere. Let's heal, honey. |
| `/shop` | Shop by feeling, not just by room. Rian's curated edit of the things she actually buys, on Amazon and LTK. |
| `/rian` | Designer, storyteller, and creator. The Dopamine Designer is the point of view behind all of it: design for how you want to feel. |
| `/contact` | Tell us what you're building — an interior project, a property to stage, a media or speaking request, or something we haven't thought of yet. |

## 4. Heading structure

**Zero `<h1>`–`<h6>` elements in the entire page** (and no `role="heading"` ARIA equivalents). Every headline — "Come home," "Rooms that hold up on an ordinary Tuesday," "Four ways in" — is a styled `<div>` or `<span>`. Visually perfect, structurally invisible: search engines get no topic hierarchy, and screen-reader users get no landmarks to jump between.

Mapping the existing copy onto a proper outline (markup change only — CSS classes keep the look identical):

| Route | Should be H1 | Should be H2s |
|---|---|---|
| `/` (home) | "Come home *(+ rotating phrase)*" | "Four ways in. Choose where you are", the four gateway card headlines, "What clients say" |
| `/design` | "Rooms that hold up on an ordinary Tuesday." | The three points: "Full-service interiors", "Why it feels so distinctly yours", "Built to last past the reveal" |
| `/staging` | "Make them feel at home before they live there." | "Scope and turnaround", "Property types", "What we need from you" |
| `/nektar` | "Come home." | "Episodes" + other point titles |
| `/shop` | "Shop by feeling, not just by room." | Feeling-category titles |
| `/rian` | "The woman behind the rooms, the stories and the way home." | Award/press subsections |
| `/contact` | "Tell us what you're building." | — |

Section names ("Hills Interior Design", "The Nektar Network") work well as eyebrow text above the H1 rather than as the H1 itself.

## 5. Image alt text

**The healthiest area of the audit.** 16 `<img>` elements in the rendered page:

- ✅ **12 with specific, descriptive alt** — "Hills Interior Design", "The Dopamine Designer", "The Nektar Network", and the four award badges ("Kansas City 2025, voted best in Interior Design", "Overland Park 2025, voted best in Interior Decorator", etc., each appearing twice).
- ✅ **2 decorative bees** (`assets/bee-peony.png`, `assets/bee-wing.png`) with `alt=""` — empty alt is the *correct* treatment for decorative images; leave them.
- ✅ **1 dynamic** (`alt="{{ cur.name }}"` on the section logo) — resolves to the section name at runtime; fine.
- ⚠️ **1 to fix: the header logo** (the clickable go-home block) has `alt=""`. It's the site's primary logo and a functional link target — give it `alt="The Nektar Network — home"` (or the final brand name).

Caveats that blunt the good alt work: all images except the two bees are base64 blobs addressed by UUID served as `blob:` URLs — **none can appear in Google Images** (no stable URL, no meaningful filename). And the ~15 MB hero **video** is embedded in the HTML with no transcript, captions, or poster — invisible to search and heavy for users (HANDOFF item to move it to external hosting already exists; that also fixes this).

## 6. URL slugs

Routes are handled client-side (`history.pushState`; `_redirects` maps everything to `index.html`):

| URL | Nav label | Notes |
|---|---|---|
| `/` | Home | |
| `/design` | Interiors | Slug ≠ nav label; consider `/interiors` for consistency (or rename nav) |
| `/staging` | Staging | ✓ clean |
| `/nektar` | Network | Slug ≠ nav label; fine if "Nektar" is the brand being built |
| `/shop` | Shop | ✓ clean |
| `/rian` | Rian | ✓ clean |
| `/contact` | Work with us | Reachable via footer/CTAs |

Plus the vanity-domain 301s in `_redirects` (good pattern, correct `301!` syntax): `nektarnetwork.com/* → /nektar`, `nektarnetwork.store/* → /shop`.

The slugs themselves are short, readable, and lowercase — nothing wrong with them as slugs. The problems are around them: (a) every route serves the identical document with identical (empty) metadata, so to Google the seven URLs are one page; (b) the catch-all rewrite makes `/anything-at-all` return 200; (c) no `<a href>` anywhere points at these routes, so a crawler has no way to discover them without a sitemap.

## 7. Root cause: the self-unpacking bundle

`index.html` is a 21.4 MB self-contained export (Claude Design canvas): a loader shell whose `<head>` says "Bundled Page," with the real page stored as a JSON string in a `<script type="__bundler/template">` block and every font/image/video embedded as base64, reassembled in the browser via JavaScript. What a crawler receives before JS runs is: no title worth having, no description, no text, no headings, no links.

Google *can* execute JavaScript, but this is a worst-case for its renderer: a 21 MB HTML payload (~15 MB of it one embedded video), content that only exists after a client-side unpack, `blob:` media, and one shared document for seven routes. Treat "Google will render it eventually" as not a plan.

Realistic fix path, in order of effort:

1. **Now (no architecture change):** hand-patch the outer shell's `<head>` — real title, meta description, canonical (`https://thenektarnetwork.com/`), `lang="en"`, favicon, og/twitter tags with a real share image. Also add `robots.txt` + `sitemap.xml` as plain files (they bypass the SPA rewrite as long as they exist in the deploy).
2. **At launch (already tracked in HANDOFF):** move the video (and ideally the photos) out of the bundle into `/assets/` with real filenames — cuts the page from ~21 MB to well under 1 MB and makes images indexable.
3. **Post-launch, when the marketing company engages:** prerender the seven routes to static HTML (per-route titles, descriptions, real headings, real `<a href>` nav). That's the step that makes §2–§4 fully real rather than JS-patched.

---

## Checklist

### Now, while the site is still gated
- [ ] Replace `<title>Bundled Page</title>` with the real home title (§2)
- [ ] Add meta description, canonical, `lang="en"`, favicon, and og:/twitter tags to the outer `<head>` (§3)
- [ ] Set `document.title` per route in the app's `go()` handler (§2)
- [ ] Give the header logo real alt text (§5)
- [ ] Add `robots.txt` (allow all + `Sitemap:` line)
- [ ] Add `sitemap.xml` listing the 7 routes on `https://thenektarnetwork.com`
- [ ] Decide `hillsinteriordesign.com`'s fate: 301 into `/design` at launch (recommended — transfers its existing index equity) vs. keep as a separate site; either way, stop serving the Showit template copy
- [ ] Move the embedded video to external hosting (existing HANDOFF item; biggest single page-weight win)

### At launch (when the gate comes off)
- [ ] Turn off Netlify visitor access control — indexing is impossible until this happens
- [ ] Verify `nektarnetwork.com` / `nektarnetwork.store` (and `hillsinteriordesign.com` if redirecting) are attached as domain aliases in Netlify so the `_redirects` vanity rules actually fire
- [ ] Set up Google Search Console + Bing Webmaster Tools for `thenektarnetwork.com`; submit the sitemap
- [ ] Add `LocalBusiness`/`ProfessionalService` structured data (Kansas City + Overland Park service area, the 2025 awards, founder Rian Hills)

### Post-launch / hand to the marketing company
- [ ] Watch GSC's Page Indexing + "Crawled – currently not indexed" reports; if rendering fails, escalate the prerender work (§7.3)
- [ ] Prerender per-route HTML: unique titles/descriptions (§2–3), real heading hierarchy (§4), crawlable `<a href>` navigation
- [ ] Add a transcript or episode notes for the podcast video/audio content
- [ ] Confirm the footer credit link to `moopsanswers.com` is intentional (it's the page's only outbound link)

---

*Method: static analysis of `index.html` (outer shell + unpacked `__bundler/template` inner document), `_redirects`, and repo contents; Netlify project settings via the Netlify API (access controls, domains, deploy state); `site:` queries against Google for all four domains. The gate blocks direct fetching of the live pages, so live-response headers weren't inspectable — re-verify `robots.txt`/`sitemap.xml` serve correctly once the gate lifts.*
