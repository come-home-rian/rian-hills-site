# Rian Hills — Project Handover Doc
*This file lives in the project repo root (`HANDOFF.md`) so both Moriah and Claude Code can keep it updated as the build progresses. Update this alongside code changes — don't let it go stale.*

Status: 🟡 In progress — accounts being set up, build not yet complete

---

## 1. Accounts

| Service | What it's for | Cost | Owner login | Notes |
|---|---|---|---|---|
| Domain registrar | Owns the site's URL | ~$1–2/mo (~$12–20/yr) | *(fill in once purchased)* | ⚠️ **Unresolved:** she owns `hillsinteriordesign.com` (confirmed via her email `rian@hillsinteriordesign.com`) — unclear if she also owns a neutral umbrella domain like `rianhills.com`. Confirm before pointing DNS anywhere — a business-specific domain name doesn't naturally fit a 5-section umbrella site. Renews: *(date)* |
| GitHub | Stores the site's code | Free | org: `come-home-rian` (billing email `rian.hills@gmail.com`); pushed via Moriah's `moriah0812-star` account | Repo: https://github.com/come-home-rian/rian-hills-site (public) |
| Netlify | Hosts + auto-publishes the site | Free tier currently (Pro is $20/mo, see note) | team `rian-comehome`, owned by `moriah0812@gmail.com` — **No 2FA enabled**, worth turning on | Project `comehomerian`, connected to the GitHub repo, deploying from `main`. Live URL (still the random slug, not yet renamed): https://merry-cranachan-812cb5.netlify.app — ⚠️ currently gated behind **Team protection** (Production visibility: Private, Deploy Preview visibility: Private), so only Netlify-logged-in team members can view it. Team members: 1 (Moriah only). Adding Rian as a team member requires upgrading to **Netlify Pro ($20/mo, 3,000 credits)** — a payment method is already on file (Mastercard ending 5848) but nothing has been charged; this upgrade has NOT been made. Free alternative: flip the project to **public** visibility (Project details → Visitor access) so anyone with the link can view without a Netlify login — no cost, but no login gate either. |
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
- [ ] "The Hills Method" email-capture freebie — discussed as a possible addition, not yet scoped or built
- [ ] Nektar Network payment processing — explicitly deferred, "way down the road"
- [ ] Payable-online invoicing for Hills Interior Design — "cool but not a necessity," not built
- [x] ~~No GitHub repo exists yet~~ — repo created and pushed: https://github.com/come-home-rian/rian-hills-site
- [x] ~~No Netlify site exists yet~~ — connected and deploying from `main`: https://merry-cranachan-812cb5.netlify.app
- [ ] **Decide: pay for Netlify Pro to add Rian as a team member, or make the project public.** Right now the live URL is Private/team-only — nobody outside Moriah's Netlify login can see it, including Rian. See row above for the tradeoff.
- [ ] **Rename the Netlify project** — it's still the auto-generated `comehomerian` / `merry-cranachan-812cb5.netlify.app` slug. Rename before sharing the link with anyone (Project details → Change project name).
- [ ] **Turn on 2FA** for `moriah0812@gmail.com` on Netlify — currently flagged "No 2FA" on the team members list. Low effort, worth doing before this becomes a real client-facing account with a payment method on file.
- [ ] `index.html` is a self-contained, self-unpacking export from the Claude Design canvas project (~23MB, includes an embedded ~16MB video) — works as a static file with no build step, but that's a large single file for a git repo. Worth moving the video to external hosting (e.g. a CDN or Netlify Large Media) before launch.
- [ ] The canonical, editable source of this design is the Claude Design canvas project: `https://claude.ai/design/p/f02b789d-595f-4839-bb6e-9641cb5e0514`. This session couldn't authenticate to that MCP (`/design-login` needs an interactive terminal), so `index.html` was reconstructed by unpacking the locally-downloaded bundle export rather than pulling live source. Re-sync from the design project once design-login is available.

---

## 6. Support / Who to Contact

- **Structural/build/technical issues** → Moriah Coleman
- **SEO / content strategy** → Rian's marketing company
- **Day-to-day content edits** → Rian, via Claude Code (see Section 4)

---

*Last updated: 2026-08-28 — GitHub repo pushed; Netlify project `comehomerian` connected and deploying from `main`, currently Private/team-gated pending the Pro-vs-public decision above.*
