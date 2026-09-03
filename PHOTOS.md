# Photo shot list — Come Home with Rian

This is the full list of real photos the site needs (33 total). Every hero
image on the live site right now is a placeholder until these are in.

## How to send them

1. Name each photo file **exactly** as shown in the "File name" column below
   (keep the extension flexible — `.jpg`, `.jpeg`, `.png`, or `.webp` are all
   fine, just don't change the part before the dot).
2. Go to the repo on GitHub: `assets/photos/`
3. Click **Add file → Upload files**, drag in your photos, and commit.

That's it — the file name alone tells us which page and which spot on the
page each photo belongs to, so there's no need to describe them separately
or match them up by hand. Send them in batches as they're ready; you don't
need all 33 at once.

## Homepage

| File name | What it is |
|---|---|
| `v3-hero.jpg` | Main homepage hero background — the first image visitors see |
| `v3-interiors-feature.jpg` | Featured Interiors photo in the homepage section teaser |
| `v3-nektar-feature.jpg` | Featured photo for The Nektar Network teaser on the homepage |
| `v3-rian-portrait.jpg` | Portrait of Rian, featured on the homepage |
| `v3-path-design.jpg` | Small thumbnail on the homepage card that links to Interiors |
| `v3-path-staging.jpg` | Small thumbnail on the homepage card that links to Staging |
| `v3-path-nektar.jpg` | Small thumbnail on the homepage card that links to Network |
| `v3-path-shop.jpg` | Small thumbnail on the homepage card that links to Shop |
| `v3-path-rian.jpg` | Small thumbnail on the homepage card that links to the Rian page |

## Interiors (Hills Interior Design) page

| File name | What it is |
|---|---|
| `v3-design-hero.jpg` | Big hero background photo at the top of the page |
| `v3-design-a.jpg` | Secondary photo, position A |
| `v3-design-b.jpg` | Secondary photo, position B |
| `v3-design-c.jpg` | Secondary photo, position C |

## Staging (Hills Home Staging) page

| File name | What it is |
|---|---|
| `v3-staging-hero.jpg` | Big hero background photo at the top of the page |
| `v3-staging-a.jpg` | Secondary photo, position A |
| `v3-staging-b.jpg` | Secondary photo, position B |
| `v3-staging-c.jpg` | Secondary photo, position C |

## Network (The Nektar Network) page

| File name | What it is |
|---|---|
| `v3-nektar-hero.jpg` | Big hero background photo at the top of the page |
| `v3-nektar-a.jpg` | Secondary photo, position A |
| `v3-nektar-b.jpg` | Secondary photo, position B |
| `v3-nektar-c.jpg` | Secondary photo, position C |

## Shop page

| File name | What it is |
|---|---|
| `v3-shop-hero.jpg` | Big hero background photo at the top of the page |
| `v3-shop-a.jpg` | Secondary photo, position A |
| `v3-shop-b.jpg` | Secondary photo, position B |
| `v3-shop-c.jpg` | Secondary photo, position C |
| `v3-edit-1.jpg` | "Shop by feeling" card — Grounded ("the lamp that fixes a dark corner") |
| `v3-edit-2.jpg` | "Shop by feeling" card — Collected ("books, boxes and the things on top") |
| `v3-edit-3.jpg` | "Shop by feeling" card — Calm ("bedding I have actually slept in") |
| `v3-edit-4.jpg` | "Shop by feeling" card — Energized ("color you can commit to in one object") |

## Rian (Meet the designer) page

| File name | What it is |
|---|---|
| `v3-rian-hero.jpg` | Big hero background photo at the top of the page |
| `v3-rian-a.jpg` | Secondary photo, position A |
| `v3-rian-b.jpg` | Secondary photo, position B |
| `v3-rian-c.jpg` | Secondary photo, position C |

## Video

The site currently has one background video (used behind the hero on both
the homepage and the Interiors page). It lives at
`assets/videos/hero-video.mp4` and is linked into the page like a normal
file (as of 2026-09-03 — it used to be built into the page itself). File
size still matters for visitors on slow connections, so keep replacements
as small as they can be while looking good.

**If you have a replacement for the existing video:**
Upload it to `assets/videos/` on GitHub (same Add file → Upload files flow
as photos) named exactly `hero-video.mp4` — replacing that file is all it
takes; the new video goes live on the next deploy automatically. If your
replacement is a different format (e.g. `.mov`), flag it in
[issue #14](https://github.com/come-home-rian/rian-hills-site/issues/14)
or a new issue so it gets converted and wired in.

**If you want a brand-new video for a page or section that doesn't exist
yet:** same folder, any clear file name, plus a note (in a GitHub issue is
easiest) on where you picture it going. There's no fixed slot for it yet,
so a short description of placement matters more here than for the shot
list above.

**Size:** keep it under roughly 15–20MB if you can (compressed, 1080p,
H.264 MP4 is the sweet spot) — the existing video is already close to that
and is a big chunk of the site's overall weight. GitHub also hard-blocks
any single file over 100MB, so if your raw footage is larger than that,
compress it first (or ask and we'll handle the compression from raw
footage — just say so on the issue rather than uploading something
GitHub will reject).

## Not on this list

Logos and award badges are already in the repo (`/assets`) — nothing needed
there. See [issue #15](https://github.com/come-home-rian/rian-hills-site/issues/15)
for the one open item on those (confirming the award wording is still
current).
