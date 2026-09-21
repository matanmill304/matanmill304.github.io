# Editing this site

One file: `index.html`. No build step, no Jekyll, no dependencies. Edit it, commit, push — it is
live in about a minute.

```bash
cd ~/stuff/matanmill304.github.io
# edit index.html
git add -A && git commit -m "what you changed" && git push
```

To see it before pushing, open the file in a browser, or:

```bash
cd ~/stuff/matanmill304.github.io && python3 -m http.server 4321
```

then go to http://localhost:4321 — reload after each save.

---

## 1. Changing project text

Every project is one block that looks like this. Search `index.html` for
`<!-- PROJECT:` to jump between them.

```html
<!-- PROJECT: Wallet -->
<details class="proj" open>
  <summary>
    <span class="p-name"><span class="chev">▸</span> Wallet <span class="tag ship">Shipped</span></span>
    <span class="p-meta">2026 — · React, TypeScript, Supabase</span>
    <span class="p-sum">The short line people read before clicking.</span>
  </summary>
  <div class="p-body">
    <p>The long explanation, only visible once opened.</p>
  </div>
</details>
```

| Part | What it is |
|---|---|
| `p-name` | The project title. Leave the `chev` span alone — it is the ▸ that rotates. |
| `tag` | The small label. `ship` = teal, `res` = blue. Change the word inside freely. |
| `p-meta` | Right-hand line: year, stack, venue. Keep it short, it is one line. |
| `p-sum` | **The summary.** Two or three lines maximum — this is what gets scanned. |
| `p-body` | Everything shown after clicking. |

## 2. Reordering projects

The order on the page is simply the order of the `<details>` blocks in the file. Cut one block
(from `<!-- PROJECT:` to its closing `</details>`) and paste it where you want it.

`open` on the first block makes it start expanded. Move that word to a different block, or delete
it so everything starts closed.

## 3. Inside the long explanation

Only four things are used, so it stays easy to keep consistent:

```html
<p>A paragraph. <strong>Bold</strong> for a phrase worth catching the eye.</p>

<ul class="hard">                        <!-- the dashed list -->
  <li><b>Lead-in.</b> Then the explanation.</li>
</ul>

<div class="figs">                       <!-- the row of numbers -->
  <div class="fig"><span class="n">~1,770</span><span class="k">transactions</span></div>
</div>

<div class="note">A boxed aside.</div>

<a class="go" href="https://...">Link text →</a>
```

`<code>3.5907</code>` gives you the monospace treatment for a figure or a filename.

**Pusimusi still needs its real description** — it currently says so out loud on the page. Replace
the `p-sum` and the `p-body` paragraph and it is done.

## 4. Changing the font

Two places, and they must agree:

1. The `<link>` in `<head>` marked `FONT —`.
2. `--sans` in the `:root` block.

Alternatives that need no other change — swap the family name in both places:

| Font | Reads as |
|---|---|
| `Instrument Sans` | current: modern, slightly compact, neutral |
| `Schibsted Grotesk` | a touch warmer, rounder |
| `Plus Jakarta Sans` | friendlier, wider |
| `Geist` | flatter and more technical |
| `Newsreader` | a serif — bookish, what this page had first |

`--mono` (IBM Plex Mono) is used for labels, years and figures. Leave it unless you want the
technical parts to feel different too.

## 5. Colours

All in `:root`, and each has a dark-mode counterpart in the
`@media (prefers-color-scheme:dark)` block below it. **Change both** or dark mode will drift.

| Token | Used for |
|---|---|
| `--paper` / `--surface` | page background / cards and chips |
| `--ink` / `--ink-2` / `--ink-3` | headings / body / quiet meta text |
| `--rule` / `--rule-2` | borders / the fainter dividers between projects |
| `--ship` | the teal accent: links, hover, the Shipped tag |
| `--research` | the blue accent for research tags |

## 6. Your photo and the favicon

- `me.jpg` — the round photo at the top. If the file is missing the photo just disappears and the
  layout closes up, so the page is never broken by it.
- `favicon.svg` and `apple-touch-icon.png` — the browser tab icon and the icon if someone saves
  the page to a phone home screen.

To replace the photo: drop a new `me.jpg` in this folder and push. Square images work best; it is
cropped to a circle.

## 7. Contact details

In the `<ul class="links">` block near the top. The email is assembled by the small script at the
bottom of the file rather than written in the HTML, so scrapers have to work for it — if you change
the address, change it in the script (`var u` and `var d`), not in the visible text.
