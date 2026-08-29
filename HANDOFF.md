# Rian Hills — Project Handover Doc
*This file lives in the project repo root (`HANDOFF.md`) so both Moriah and Claude Code can keep it updated as the build progresses. Update this alongside code changes — don't let it go stale.*

Status: 🟡 In progress — accounts being set up, build not yet complete

---

## 1. Accounts

| Service | What it's for | Cost | Owner login | Notes |
|---|---|---|---|---|
| Domain registrar | Owns the site's URL | ~$1–2/mo (~$12–20/yr) | *(fill in once purchased)* | ⚠️ **Unresolved:** she owns `hillsinteriordesign.com` (confirmed via her email `rian@hillsinteriordesign.com`) — unclear if she also owns a neutral umbrella domain like `rianhills.com`. Confirm before pointing DNS anywhere — a business-specific domain name doesn't naturally fit a 5-section umbrella site. Renews: *(date)* |
| GitHub | Stores the site's code | Free | org: `come-home-rian` (billing email `rian.hills@gmail.com`); pushed via Moriah's `moriah0812-star` account | Repo: https://github.com/come-home-rian/rian-hills-site (public) |
| Netlify | Hosts + auto-publishes the site | Pro ($20/mo, 3,000 credits) — upgraded 2026-08-28, needed for password protection | team `rian-comehome`, owned by `moriah0812@gmail.com` — **No 2FA enabled**, worth turning on | Project `comehomerian`, connected to the GitHub repo, deploying from `main`. **Live URL: https://comehomerian.netlify.app** (renamed from the random slug). Gated with **Basic (password) protection** — visitors get a password prompt directly on the site, no Netlify login/account needed. The password itself was set directly in the Netlify UI and isn't recorded here or anywhere Claude Code can see it — Moriah has it, share it with Rian out of band (text/email). **How to get back to the dashboard:** app.netlify.com → click the team switcher (top left, next to the Netlify logo) → select **rian-comehome** → Projects → **comehomerian**. Or go straight to https://app.netlify.com/projects/comehomerian. Rian was also added as a **Reviewer** on the team — note that role only covers commenting on Deploy Previews/branch deploys, it does *not* grant her access to the password-protected production site; the password is what actually gets her in. |
| Claude Pro | Powers Claude Code — how Rian makes edits | $20/mo | Her own account | Required before handoff is "done" |

**Total: ~$30–31/month**

---

## 2. Brand Assets

- **Logos**: Hills Interior Design, The Nektar Network, The Dopamine Designer — final files stored in `/assets/`
- **Colors** (locked, from marketing company):
  - Warm ivory `#F7F4ED`
  - Soft black `#292929`
  - Antique gold `#BD9852`
  - Honey cream `#EFE7D4`
  - Section accents: Deep berry `#7A214F` (Nektar) · Magenta/Marigold/Chartreuse/Apple green/Sapphire (Dopamine Designer)
- **Fonts**: Playfair Display (display/serif) + Jost (body/sans)
- Usage ratio: 60% foundation neutrals / 20% soft-black ink / 10% gold / 10% expressive color

---

## 3. Site Structure

⚠️ **Scope note:** the live build now has 5 sections, not the original 3. "Staging" and "Shop" were added along the way, and "Rian" (about/meet the designer) became its own section. Worth naming this growth to Rian explicitly — not a problem, just worth being visible rather than silently absorbed.

```
Homepage
├── Interiors  (Hills Interior Design)
├── Staging    (Hills Home Staging)
├── Network    (The Nektar Network)
├── Shop       (The Edit)
└── Rian       (Meet the designer)
```

Photo requirements for all sections: see `PHOTOS.md` in the repo root — maps every image slot in the code to a plain filename Rian can drop in.

---

## 4. How to Make Edits (for Rian)

1. Open Claude Code, pointed at this project
2. Describe the change in plain English (e.g., "update the meta description on the Design page")
3. Review the change/preview
4. It auto-publishes live via Netlify within a minute of pushing
5. To undo anything: ask Claude Code to revert, or check GitHub's file history

No dashboard login required for day-to-day edits — Claude Code is the only tool needed.

---

## 5. Known Open Items

*(Keep this current — mark resolved items with ~~strikethrough~~ rather than deleting, so there's a record.)*

- [ ] **Domain clarification** — does Rian own a neutral umbrella domain (e.g. rianhills.com), or only hillsinteriordesign.com? Determines the whole site's URL structure
- [ ] Award badge claims (Kansas City / Overland Park "voted best") — verify these are real/current before launch
- [ ] **33 total photos needed** across all sections (see PHOTOS.md) — this is more than the original 6-photo shot list assumed; flag realistic timeline to Rian
- [ ] Podcast content for The Dopamine Designer / Network — pending Rian's upcoming photoshoot
- [x] ~~Site had no real URLs — every section funneled through the homepage~~ — fixed 2026-08-28. Sections are now linkable at `/design`, `/staging`, `/nektar`, `/shop`, `/rian`, `/contact` (direct visits, browser back/forward, and sharing all work correctly — verified end-to-end). **Follow-up once the domain is finalized:** update Rian's podcast show notes / Instagram bio link to point at `[domain]/nektar` instead of the bare root — that's the actual fix to the traffic-funnel problem this routing work enables.
- [x] ~~Copy voice pass~~ — homepage intro, the last rotating hero phrase, Design's closer + first point, Nektar's body + all three point notes, and Rian's headline/body/first point note rewritten to the approved voice (2026-08-28, per an external copy spec). Staging, Shop, footer lines, testimonials, and inquiry labels intentionally left untouched.
- [ ] "The Hills Method" email-capture freebie — discussed as a possible addition, not yet scoped or built
- [ ] Nektar Network payment processing — explicitly deferred, "way down the road"
- [ ] Payable-online invoicing for Hills Interior Design — "cool but not a necessity," not built
- [x] ~~No GitHub repo exists yet~~ — repo created and pushed: https://github.com/come-home-rian/rian-hills-site
- [x] ~~No Netlify site exists yet~~ — connected, deploying from `main`, live at https://comehomerian.netlify.app
- [x] ~~Rename the Netlify project~~ — renamed from `merry-cranachan-812cb5` to `comehomerian`
- [x] ~~Decide: Pro vs public visibility~~ — went with **Netlify Pro + Basic password protection** (2026-08-28), so the site stays gated pre-launch but Rian doesn't need her own Netlify account to view it
- [x] ~~Restyle the loading splash~~ — the "Unpacking..." placeholder screen (shows briefly while `index.html` loads client-side) now reads "Come Home. / with Rian" over the Nektar bee mark, on the ivory brand background, in Playfair Display + Jost — done 2026-08-28
- [x] ~~Site was not mobile-friendly~~ — fixed 2026-08-28 in two passes.
  - **Pass 1:** the design-canvas export had zero `@media` queries — 12 fixed multi-column grid layouts that never stacked, headline text up to 92px fixed, fixed 40px side gutters (21% of a 375px screen), hero/feature blocks fixed at 520–660px tall. Fixed by rewriting the values themselves to be natively responsive rather than overriding them externally — `grid-template-columns` uses `repeat(auto-fit, minmax(...))` so grids stack on their own, headline sizes use `clamp(min, vw, max)`, hero/feature heights use `clamp()` scaled to viewport width, side padding scales via `clamp(20px, 5vw, 40px)`. Deliberately avoided CSS attribute-selector overrides (`[style*="..."]` + `!important`) after discovering the framework re-serializes inline styles through the DOM — hex colors become `rgb()`, `0` becomes `0px`, quotes get stripped — which silently breaks any override matching literal source-text substrings.
  - **Pass 2 (the actual "looks like shit" report):** Pass 1 wasn't sufficient — two `display: flex` rows (the 4 award badges, and the footer's nav-links row) had no `flex-wrap`, so on a phone those two rows alone forced the *entire page's layout viewport* to ~546px wide inside a 375px screen, shrinking everything else to compensate — that's what actually looked broken, not the grid/font/height work from Pass 1. Fixed by scanning every inline `display: flex` declaration in the file and adding `flex-wrap: wrap` to every one that wasn't already `flex-direction: column` (25 total) — safe universally since wrap only activates when content doesn't fit, verified zero visual change at 1440px desktop. Verified on mobile: layout viewport now correctly matches the physical screen width (was 546px, now ~379px on a 375px screen) with zero elements wider than the viewport.
  - **Lesson for next time:** checking computed styles on the *specific elements you changed* isn't enough to confirm "mobile-friendly" — always also check `window.innerWidth` vs `visualViewport.width` and scan for any element wider than the viewport, since one missed unwrapped row can throw off the whole page's layout viewport even when everything else is correctly responsive.
  - **Pass 3 (from an actual phone screenshot, 2026-08-28):** Pass 2's viewport-width fix was correct but not sufficient either — a real-phone screenshot showed the header nav wrapping into a ragged right-justified block ("SHOP RIAN" and the CTA button both stranded alone against the right edge on their own lines) and, worse, the hero's decorative SVG piping and the "Drag a photo onto this panel" prototype caption — both absolutely positioned at the hero's bottom edge — visually overlapping the headline and body text. Root cause: the hero's stacked content (headline + phrase + body + buttons) grew taller at mobile widths than the height Pass 1 had clamped the hero down to, so the text spilled down into where those bottom-anchored decorative elements sit. Fixed by: (1) switching the header's wrapping nav row from `justify-content: flex-end` to `center` (ragged-right → clean centered lines when wrapped; zero effect on desktop, confirmed), (2) hiding the decorative SVG and the caption below 560px width via a real `@media` rule with ID selectors (not attribute-value matching, which is unreliable here — see note below), (3) raising the mobile hero-height floor from 360px to 480px for more breathing room. Verified: hero body text now stays fully inside the hero's bounds on mobile, zero overflowing elements, desktop pixel-identical (decoration still visible, hero still 660px, CTA button still right-aligned).
  - **Technical note for future CSS edits to this file:** `[style*="..."]` attribute selectors matching literal inline-style substrings are unreliable here — this framework re-serializes inline styles through the DOM (hex → `rgb()`, `0` → `0px`, quotes stripped, spacing added around `/`), so a selector that matches the source text can silently fail to match the live DOM. Prefer either (a) editing the actual values in place (what Pass 1's `clamp()`/`auto-fit` work did), or (b) adding a stable `id="..."` attribute directly in the template source and writing a real CSS rule against that id (what Pass 3 did for the hero elements) — both survive the framework's style normalization; attribute-value matching does not. Also: when inserting new CSS text into the shared `<style>` block, escape real newlines as `\n` (not just quotes) — the manifest/template is parsed in a way that chokes on literal control characters, which silently breaks the whole page (caught in testing, not shipped, but worth remembering).
  - **Pass 4 (still from real-phone feedback, 2026-08-28):** with the overlap fixed, the header itself was still consuming most of a phone's first screen — the full desktop header (76px logo, tagline, 5 nav items, CTA button) was just wrapping to 4+ stacked rows at full size instead of being redesigned for mobile, pushing the hero almost entirely below the fold. Fixed: logo icon scales via `clamp(40px, 10vw, 76px)`, the "Come home · with Rian" tagline hides below 560px (redundant once you're on the page), CTA button padding scales down, and the wrapped-row vertical gaps were tightened. Header now takes ~200px on a 375px phone instead of most of the visible screen; desktop verified unchanged (logo, tagline, padding all back to original values at 1440px).
  - **Not a code issue — flagging so it isn't chased as one:** the "Make public" floating pill visible in Moriah's phone screenshots is Netlify's own visitor-access toolbar, shown only to whoever's logged into the Netlify team on that device — it is not part of the deployed site and will not appear for Rian, clients, or any real visitor. Nothing to fix here.
  - **Pass 5 (requested further compression, 2026-08-28):** tightened everything from Pass 4 another notch — logo floor down to `clamp(30px, 8vw, 76px)`, row/column gaps between the wrapped header rows cut roughly in half, per-nav-item and CTA button padding reduced further. Header now takes ~140px on a 375px phone (down from ~200px after Pass 4, and from filling most of the screen originally). Desktop re-verified unchanged at each step (76px logo, 15px/24px button padding, same header height as before any of this work).
  - **Pass 6 (collapsible nav, 2026-08-28):** the 5 nav links now collapse below 560px width behind a single tappable "Ways home ⌄" row instead of always showing as two lines of text. Built with a pure CSS checkbox-hack (hidden `<input type="checkbox">` + `<label>` + sibling selectors) rather than adding JS state to the framework's `Component` class — no risk of colliding with its own reactivity, and it's the standard, dependency-free way to do a mobile menu toggle. Header now runs ~117px on a 375px phone before you tap anything. "Work with us" stays always visible (not hidden behind the toggle) since it's the primary conversion action. Desktop unaffected (toggle and its CSS are display:none outside the mobile breakpoint, nav always shows as before). Known minor cosmetic gap: the chevron doesn't visually flip on open (the CSS rule matches per DOM inspection but doesn't visibly rotate) — functionality (show/hide) works correctly, this is purely a nice-to-have polish item if revisited.
  - **Pass 7 (moved the toggle next to the logo, 2026-08-28):** relocated "Ways home" from its own row to sit beside "Nektar" on the logo's line, so the collapsed header only needs one row for branding+toggle instead of two. Since the checkbox is no longer a direct sibling of `#nav-items-row` (it moved up a nesting level to sit next to the logo, outside the nav+CTA wrapper), the reveal rule switched from a sibling-combinator selector to `:has()` scoped to a new `#site-header-row` id on the shared ancestor — reaches across the DOM regardless of nesting. Also removed a stray `width: 100%` on the toggle label left over from Pass 6, which had been forcing it onto its own line even with room to spare. Collapsed header now runs ~78px on a 375px phone (down from ~117px after Pass 6). Desktop re-verified unchanged (80px header height, same as before any mobile work).
  - **Pass 8 (mobile-nav sibling, 2026-08-28):** applied the exact same checkbox-hack toggle pattern to the footer's nav links (previously always shown as two wrapped lines) — "Ways home ⌄" beside "Come home.", collapsed by default below 560px.
  - **Bleed audit across every page (2026-08-28):** the same content-taller-than-clamped-container bug from the homepage hero (Pass 3) also affected the shared section-page hero — verified on Interiors and confirmed it's the same template for Staging/Network/Shop/Rian. Fixed by raising that hero's mobile height floor from 300px to 480px (was pushing "View the Portfolio" — a light-outlined button meant for the dark hero — down onto the light section below, where it was nearly invisible). Also caught and fixed: the homepage's rotating italic phrase text was never clamped in Pass 1 (it used `font: italic 400 50px` syntax, which didn't match that pass's regex), so it stayed fixed at 50px while the headline shrank to 38px — inverting the intended size hierarchy on narrow screens. Now clamps 24–50px. Swept every route (home, all 5 sections, contact) post-fix: zero errors, zero elements wider than the viewport, on both mobile and desktop.
- [x] ~~Prototype scaffolding language visible in the live footer~~ — removed 2026-08-28. "Prototype. Every grey panel is a drop target..." replaced with real footer copy; the hero's "Drag a photo onto this panel." caption removed entirely (was already hidden on mobile, now gone everywhere).
- [x] ~~Footer jar icon didn't match the homepage's~~ — the footer credit icon was a plain pale-blue outline; recolored/redrawn to match the homepage's honey-jar illustration (navy `#2F4E86` stroke, white-filled body/lid, cap texture, top+bottom ripple bands) — done 2026-08-28.
- [x] ~~One of the three rotating footer taglines needed cutting~~ — "Yes, the paint color was on purpose." removed from `FOOTER_LINES`; the other two ("Ask her about the light switch." / "No beige was harmed.") remain.
- [x] ~~Section pages showed plain text instead of a real logo~~ — Interiors/Staging now show the Hills wordmark, Network shows the Nektar wordmark, Rian shows The Dopamine Designer wordmark (all inverted white for the dark hero via `filter: brightness(0) invert(1)`), reusing the same image assets already in the manifest. Shop has no dedicated logo asset and correctly falls back to the plain text eyebrow — done 2026-08-28.
- [x] ~~Nektar page needed a "fun" moment~~ — added a clickable hive (3 bees fly a heart-shaped path into it on click, reusing the existing swarm/jar bee art) — done 2026-08-28. See the debugging note below; this took an unusual amount of trial-and-error and the lesson is worth reading before touching this block again. The ambient honey-drip animation that originally accompanied it was removed the same day — couldn't reliably position it to look like it was dripping off specific letters in the headline text (same structural constraint as the debugging note), and a loose floating drip effect wasn't worth keeping without that connection.
- [x] ~~Rian page needed more Dopamine Designer color~~ — went through two rounds. First attempt (a standalone 5-color diagonal-line flourish) was rejected as "random, does nothing for the page." Second attempt used `/design` to properly explore a direction (colors tied to real content — a palette strip by the eyebrow, per-section-colored value cards, the jar motif relocated into the closer) — approved, and the palette-strip piece was brought into the live site. Also added: a small jar icon per section page (Interiors/Staging/Shop/Rian each get their own brand-accent-colored jar; Nektar keeps its hive instead), and the primary CTA buttons on every section page now use that section's own accent color instead of one universal red — both done 2026-08-28.
- [x] ~~"Tap the hive" caption sat awkwardly above the hive on Nektar~~ — removed entirely, the hive graphic is self-explanatory as a clickable element — done 2026-08-28.
- [x] ~~Redundant section-name label on every section page~~ — a plain-text eyebrow (e.g. "SHOP") was showing twice per section: once in the hero (only visible on Shop, since it's the one section without a logo image) and once above every section's closer/bottom-CTA headline (all 5 sections, unconditionally). Both removed — nav already shows which page you're on, the label was just noise — done 2026-08-28.
- [x] ~~Full click-handler audit of every button/CTA on the site~~ — done 2026-08-28. Confirmed HANDOFF's Section 6 dead-CTA list is complete (no other buttons are silently dead) and turned it into tracked issues: [#21](https://github.com/come-home-rian/rian-hills-site/issues/21) (the 5 dead secondary CTAs), [#22](https://github.com/come-home-rian/rian-hills-site/issues/22) (Shop's Amazon/LTK links), [#23](https://github.com/come-home-rian/rian-hills-site/issues/23) (social links decision); beefed up [#10](https://github.com/come-home-rian/rian-hills-site/issues/10)'s body with the specific contact-method blocker, and left a wiring note on [#16](https://github.com/come-home-rian/rian-hills-site/issues/16) for swapping "Listen to Rian" to real podcast links once recorded.
- [x] ~~Homepage's bottom-left decorative line art (`#hero-deco-svg`) was missing on mobile~~ — it was never deleted, just intentionally hidden below 560px width during the Pass 3 mobile fix (see above) because it overlapped the hero text. Brought back 2026-08-29: shrunk (240×210 → 126×110), moved from bottom-left to bottom-right, and dropped to 0.4 opacity, so it shows as a subtle flourish behind the empty part of the hero image without ever crossing the text column — verified with no overlap at both 375px and 320px widths. Desktop position/size untouched.
- [x] ~~Porcelain jars around the site weren't interactive (except the footer one)~~ — done 2026-08-29. Every jar now sends a bee flying out on click and then navigates home. The 4 per-section jar motifs (Interiors/Staging/Shop/Rian) got a new click handler + a small bee; first pass just flew it to a fixed offset and faded, but the actual ask was for the bee to fly literally to that page's own "← Go home" link at the top of the hero — fixed by giving both elements a `ref` and computing the real flight distance between them (`getBoundingClientRect`, same technique the footer jar already used to target the hive), then navigating home once it lands. The existing footer jar (with its own bee-to-hive animation) now also routes home once that sequence finishes, instead of just resetting in place.
- [ ] **Turn on 2FA** for `moriah0812@gmail.com` on Netlify — currently flagged "No 2FA" on the team members list. Worth doing now that there's a payment method on file for a real client-facing account.
- [ ] **Scenario-specific contact modals + Netlify Forms** — tracked as GitHub issue [#20](https://github.com/come-home-rian/rian-hills-site/issues/20), not part of this pass. The Contact page's 5 inquiry cards have no click handler at all.
- [ ] `index.html` is a self-contained, self-unpacking export from the Claude Design canvas project (~23MB, includes an embedded ~16MB video) — works as a static file with no build step, but that's a large single file for a git repo. Worth moving the video to external hosting (e.g. a CDN or Netlify Large Media) before launch.
- [ ] The canonical, editable source of this design is the Claude Design canvas project: `https://claude.ai/design/p/f02b789d-595f-4839-bb6e-9641cb5e0514`. This session couldn't authenticate to that MCP (`/design-login` needs an interactive terminal), so `index.html` was reconstructed by unpacking the locally-downloaded bundle export rather than pulling live source. Re-sync from the design project once design-login is available.
- [ ] **Debugging note — a specific spot in the Nektar closer block silently corrupts the whole page (2026-08-28).** Adding *any* new child element with an `id`, `title`, or `sc-camel-on-click` attribute directly inside the closer block's centered content div (the one holding `{{ cur.name }}` / `{{ cur.closer }}` / `{{ cur.cta }}`) breaks template rendering for the **entire site**, not just that section — every route goes blank below the header, with no console error. Verified this is not about `sc-if`, not about SVG content, not about which click handler — isolated it down to those three specific attributes at that specific nesting depth, one at a time. Plain `<div>` children with only a `style` attribute are fine there (that's how the honey drips work). The hive/bee click target had to be moved to a sibling position (right after the existing `cur.isDesign` block, same nesting depth as `isSection`'s other direct children) where identical markup with `id`+`title`+`sc-camel-on-click` renders perfectly. If you need interactive content specifically inside that closer div in the future: don't — build it at the sibling position instead, or reach for the same CSS-checkbox-hack pattern used for the header/footer nav toggles (native `<input type="checkbox">` + `<label>`, no `id` needed if you scope via a class + `:has()` on an ancestor) rather than `sc-camel-on-click`. Always verify with `document.getElementById('dc-root').innerHTML.length` before and after any change here — a healthy page is ~60,000 characters; a page broken by this bug renders ~53,500 (missing everything past the header) with zero visible error.

---

## 6. Hyperlink Wiring — page by page

*(Added 2026-08-28, from a full pass through the site's actual routing code.)* The site is a single-page app — all nav (header, footer, hero buttons, every section's primary CTA) already works via internal client-side routing. Across the **entire site** there are only 3 real `<a href>` links: two Google Fonts preconnects and the "Designed by MoOps" footer credit. Everything below has **no click handler at all** — it looks clickable but does nothing.

**Every section page (Interiors / Staging / Network / Shop / Rian)** — same gap repeats 5×: the *secondary* CTA button next to the working primary one is dead.

| Section | Dead secondary CTA | What's needed |
|---|---|---|
| Interiors | "View the portfolio" | A portfolio/gallery page (needs photos first), or route to Contact as a stopgap |
| Staging | "See before + after" | A before/after gallery, or stopgap to Contact |
| Network | "Explore Nektar Notes" | A written-content page for Nektar Notes, or stopgap to Contact |
| Shop | "Shop by room" | A shop filter/page, or stopgap to Contact |
| Rian | "Invite Rian to speak" | Route to Contact with speaking context, or a dedicated speaker one-sheet if she has one |

**Contact page** — all 5 inquiry cards ("Interior project," "Staging a property," "Media or speaking," "Brand partnership," "Something else") have zero click handler. This is the #1 conversion bug on the site — nobody can currently reach Rian through it. **Needed:** a real destination — a form endpoint, an email address, a phone number, or all three. The copy implies inquiries route differently by type ("we'll route it to the right place") — need to know what "the right place" actually is per category, or whether one inbox with different subject lines is fine.

**Shop section** — explicit in the copy itself: *"Amazon and LTK: The buying happens on the storefronts. Links pending, send the two URLs and they go live."* **Needed: Rian's Amazon storefront URL and her LTK (LikeToKnow.it) URL.** Not yet provided as of 2026-08-28 — checked the repo, HANDOFF, and site code, they aren't captured anywhere.

**Network/Nektar section** — "Listen to Rian" currently just navigates internally. Once the podcast is recorded (already an open item above), swap in real Spotify/Apple Podcasts/YouTube links. Not blocking now.

**Social links** — none exist anywhere on the site (no Instagram/Facebook/TikTok, checked). Open question for Rian: does she want social links in the header/footer? If yes, need the handles/URLs.

**Footer/global** — no `mailto:`/`tel:` anywhere. Same root cause as the Contact page gap — one real contact method fixes both.

**Bottom line — what's actually needed from Moriah/Rian:**
1. A working contact method (form and/or email and/or phone) — biggest single unblock
2. Amazon + LTK storefront URLs for Shop
3. Decision: do the 5 dead secondary CTAs get real destination pages later, or route to Contact for now as a stopgap
4. Yes/no on social links, and handles if yes

---

## 7. Transfer Checklist (when handing this off to Rian for good)

None of this has been done yet — everything currently lives under Moriah's accounts. When it's time to actually hand over ownership:

- [ ] **Rian gets her own GitHub account** (if she doesn't have one), then gets invited to the `come-home-rian` org as **Owner**. Once she's accepted, Moriah is removed from the org (or downgraded to a collaborator role if still doing maintenance work).
- [ ] **Rian gets her own Netlify account.** Use the **Transfer project** button (Project configuration → Project details) to move `comehomerian` from the `rian-comehome` team to her own team. Check at transfer time whether the Pro subscription/billing moves with the project or needs to be re-set-up on her side — this affects her ongoing $20/mo cost, confirm in Netlify's docs before assuming either way.
- [ ] **Domain** — needs to be resolved first (see the open item above) and registered/owned under Rian's own registrar login, not Moriah's.
- [ ] **Claude Pro** — she needs her own subscription before day-to-day edits (Section 4) work without Moriah in the loop.
- [ ] Once all four are on her accounts, remove the password protection (or keep it, her call) and consider this handoff complete.

---

## 8. Support / Who to Contact

- **Structural/build/technical issues** → Moriah Coleman
- **SEO / content strategy** → Rian's marketing company
- **Day-to-day content edits** → Rian, via Claude Code (see Section 4)

---

*Last updated: 2026-08-28 — Netlify project renamed to `comehomerian`, upgraded to Pro, and gated with password protection (not team-login); loading splash restyled with the Nektar bee mark and "Come Home. / with Rian"; added a Transfer Checklist section for eventual handoff to Rian's own accounts.*
