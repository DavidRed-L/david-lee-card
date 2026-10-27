# AI-GUIDE.md — 李宏霖 David Lee 數位名片

Instructions for an AI assistant asked to update this name card. Read this whole file before editing.

## Project facts

- Static site, no build step. GitHub Pages serves the `main` branch root.
- Repo: `yubawang/david-lee-card` — live URL: `https://yubawang.github.io/david-lee-card/`
- Owner of the card: 李宏霖 (David Lee), 地政士 (Taiwan land administration agent).
- Language: Taiwanese Traditional Chinese (`zh-Hant-TW`). Never use Simplified Chinese.
- `index.html`: the card. One fixed SVG artboard (`viewBox="0 0 941 1672"`). Tailwind (Play CDN, pinned `3.4.17`) styles only `<body>` / `<main>`.
- `style.css`: SVG text styles (`.name`, `.name-en`, `.tagline`, `.link-text`, `.link-text.zh`, `.link-line`).
- `guide.html`: human guide for David (Traditional Chinese). `README.md`: short overview.

## Links (all in `index.html`, inside `<g class="link-list">`)

| # | Label | `href` now | Status |
|---|---|---|---|
| 1 | INSTAGRAM | `https://www.instagram.com/david041721/` | final |
| 2 | FACEBOOK | `https://www.facebook.com/li.hong.lin.129117` | final |
| 3 | LINE | `https://www.youtube.com/watch?v=dQw4w9WgXcQ` | **TEMP** (Rick Roll) |
| 4 | 個人網站 | `https://www.youtube.com/watch?v=VClI7NywlYA` | **TEMP** |
| 5 | 電子郵件 | `mailto:yubawang@gmail.com` | **TEMP** |

Each TEMP link has an HTML comment `<!-- TEMP: ... -->` directly above its `<a>`.

## How to swap a TEMP link

1. Find the exact old `href` string from the table and replace only the value inside the quotes.
2. LINE: expect `https://line.me/ti/p/<id>` or `https://line.me/R/ti/p/@<id>` (official account). Validate it starts with `https://line.me/`.
3. Website: must be a full `https://` URL.
4. Email: keep the `mailto:` prefix; value must look like `name@domain`.
5. Once a link is real, delete its `<!-- TEMP ... -->` comment and update the table here, the swap table in `guide.html`, and the TEMP table in `README.md`.
6. Keep `target="_blank" rel="noopener noreferrer"` on external links (not on `mailto:`).

## Layout rules (do not break)

- Links are spaced 128 SVG units apart: text `y` = 852, 980, 1108, 1236, 1364; each underline sits at text `y + 40`.
- Content must stay inside the inner frame (`y` 178–1488). Adding a 6th link: use 112 spacing starting at 828 (like the original 6-link layout) and shift all five.
- Letter-spaced text is centered at `x = 470.5 + letter-spacing / 2` (Latin links `x="477"`, Chinese links `x="478.5"`). Keep that rule for new labels.
- Underline length roughly matches label width, centered on 470.5 (e.g. `x1="346" x2="595"`).
- Keep exactly 3 border lines. Keep the light ivory + gold palette.
- `#goldLine` uses `gradientUnits="userSpaceOnUse"`; an objectBoundingBox gradient renders nothing on a flat horizontal line.

## Profile photo

Square image named exactly `profile.jpg` in the repo root. The inline script shows it if it loads; otherwise the 「李」 monogram shows. No code change needed.

## Verify after editing

- Open the page at phone width (~390px) and desktop width; all 5 labels and underlines visible, nothing clipped horizontally.
- Click each link; confirm it goes to the new destination.
- `grep -n 'TEMP' index.html` lists only links that are still placeholders.
- After pushing to `main`, Pages updates in about 1–2 minutes.
