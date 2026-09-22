# Editing this site

One file: `index.html`. No build step, no dependencies. Edit it, then publish:

```bash
cd ~/stuff/matanmill304.github.io && git add -A && git commit -m "what you changed" && git push
```

Live in a minute or two (occasionally up to five — GitHub Pages is not always quick).

**To see changes as you type**, ask Claude to start the `github-page` preview: it reloads on every
save. Or run a plain server and refresh by hand:

```bash
cd ~/stuff/matanmill304.github.io && python3 -m http.server 4321
```

**Or edit on GitHub directly:** open `index.html` on github.com, press the pencil, edit, and
"Commit changes". Pick one way and stick to it — editing both places at once makes them conflict.

---

## 1. The header

Near the top of `<body>`:

```html
<h1>Matan Millionschik</h1>
<p class="role">Founder, Engineer and Product Manager.</p>
<p class="bio">I work on things that help me and the people around me. …</p>
<p class="where">Tel Aviv · Israel</p>
```

Change the text between the tags. The name also appears in `<title>` and in the two `meta`
descriptions at the top of the file — those are what Google and link previews show, so update them
too if you change the name or the line about what you do.

## 2. A project

Every project is one block. Search the file for `PROJECT:` to jump between them.

```html
<!-- PROJECT: Personal Finance Agent -->
<details class="proj">
  <summary>
    <img class="thumb" src="img/thumb-finance.png" alt="">
    <div>
      <div class="p-top"><span class="p-name">Personal Finance Agent</span></div>
      <div class="p-sum">The one line people read before opening it.</div>
      <div class="p-meta">AI · TypeScript · React · Supabase</div>
    </div>
    <span class="chev">▸</span>
  </summary>
  <div class="p-body">
    <p>The full description, shown after clicking.</p>
    <ul class="feat"><li>A feature</li></ul>
    <p class="mob">Designed for the phone — best opened on mobile. …</p>
    <div class="p-links">
      <a class="primary" href="https://…" target="_blank" rel="noopener">Open the app</a>
      <a href="https://…" target="_blank" rel="noopener">Another link</a>
    </div>
  </div>
</details>
```

| Part | What it is |
|---|---|
| `thumb` | The picture on the left. See §4. |
| `p-name` | The title. |
| `p-sum` | **The summary** — one or two lines. It is all people see until they click. |
| `p-meta` | Topic and tools, separated by ` · `. Topics (AI, Machine Learning) go first. |
| `chev` | The ▸ that rotates when the project opens. Leave it alone. |
| `p-body` | Everything shown after clicking. |

Inside `p-body` you can use:

| Markup | Gives you |
|---|---|
| `<p>…</p>` | a paragraph. `<strong>…</strong>` inside it darkens a phrase. |
| `<ul class="feat"><li>…</li></ul>` | the short dashed feature list |
| `<p class="mob">…</p>` | the small note with the phone icon |
| `<p class="paused">…</p>` | a small grey note, no icon |
| `<div class="p-links">…</div>` | the row of pill buttons. Add `class="primary"` to the main one. |

Everything starts closed. Adding `open` — `<details class="proj" open>` — makes one start
expanded.

## 3. Reordering projects

The order on the page is the order of the blocks in the file. Cut a whole block, from its
`<!-- PROJECT:` line to its closing `</details>`, and paste it where you want it.

## 4. Thumbnails

In `img/`, all shaped 16:10 (wide), and shown 152px across:

| File | Project |
|---|---|
| `thumb-finance.png` | Personal Finance Agent |
| `thumb-weight.png` | Weight Tracking App |
| `speech-attribution.png` | Synthetic Speech Attribution — Fig. 1 from the paper |
| `thumb-travel.jpg` | Travel App for Thailand |
| `vit.svg`, `audio-events.svg` | the two research projects (drawn illustrations) |

To replace one, save a new image in `img/` and change the `src` in both places it appears in that
project. Anything at least 320px wide and roughly 16:10 works; other shapes get cropped to fit.
Square app icons look best centred on a background of their own colour rather than cropped — ask
Claude to do that, as was done for the finance and weight icons.

## 5. Changing the font

Two places, and they must agree:

1. The `<link>` in `<head>` marked `FONT —`.
2. `--sans` in the `:root` block.

| Font | Reads as |
|---|---|
| `Instrument Sans` | current: modern, slightly compact, neutral |
| `Schibsted Grotesk` | a touch warmer, rounder |
| `Plus Jakarta Sans` | friendlier, wider |
| `Geist` | flatter and more technical |

`--mono` (IBM Plex Mono) is used for PROJECTS, the location, the tech line and the buttons.

## 6. Colours

All in `:root`, each with a dark-mode twin in the `@media (prefers-color-scheme:dark)` block just
below it. **Change both**, or dark mode drifts.

| Token | Used for |
|---|---|
| `--paper` / `--surface` | page background / thumbnails, buttons |
| `--ink` / `--ink-2` / `--ink-3` | headings / body text / quiet text like the tech line |
| `--rule` / `--rule-2` | borders / the faint lines between projects |
| `--ship` | the teal accent: hover colour, and the "Open the app" button |

## 7. Your photo and the tab icon

- `me.jpg` — the round photo. If it is missing, the photo simply disappears and the layout closes
  up, so the page never breaks. Replace it with a new square `me.jpg` and push.
- `favicon-32.png`, `favicon-16.png`, `apple-touch-icon.png` — the browser tab icon, and the icon
  if someone saves the page to a phone home screen.

## 8. Contact buttons

The `<ul class="links">` block in the header. The email address is assembled by the small script
at the bottom of the file, so scrapers have to work for it — to change it, edit `var u` and
`var d` in that script, not the visible text.

## One thing to avoid

**Do not put `-->` inside an HTML comment.** Comments cannot contain it: it ends the comment early
and spills the rest of the comment onto the page as visible text. This has happened on this site
once already.
