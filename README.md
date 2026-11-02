# 4 Friends website

The page for 4 Friends, the multiplayer running game: a landing page, a
support page with the feedback form, and their stylesheet. Static HTML, no
build step. Same layout as TrackPrint's
([trackprint-webpage](https://github.com/TrackPrint-Music-Posters/trackprint-webpage))
and Lectio's
([lectio-webpage](https://github.com/Lectio-Study-Planner/lectio-webpage)).

## Published at

GitHub Pages serves `main` from the repo root:
<https://4-friends-multiplayer-running-game.github.io/4-friends-webpage/>

| Page | Address | Used as |
|---|---|---|
| `index.html` | `…/4-friends-webpage/` | The landing page; later the store listings' Marketing URL |
| `support.html` | `…/4-friends-webpage/support.html` | The support page and feedback form; later the store listings' Support URL and the game's Support link |
| `support.html#send-feedback` | `…/4-friends-webpage/support.html#send-feedback` | The feedback form on its own; the landing page links here |

Once the game links to these pages, keep their addresses in one place in the
game's code. If a page is renamed or the site moves, change it there in the
same release, and keep the old address answering until the builds that use
it are gone.

## Editing

- `index.html` is the landing page, `style.css` the styles of both pages.
  Open a page in a browser to preview it; there is nothing to install. (A
  local `python3 -m http.server` in this folder serves it the way Pages
  does.)
- **The game is in development, and the page says so.** It names only what
  the game really does: four friends racing in one multiplayer match. When a
  feature ships, give it a section (an eyebrow in one of the four friends'
  colours, a headline, a line) and, once there are any, screenshots or clips
  in `images/` as WebP (`cwebp -q 86`). Replace the "In development" badges
  with the store badges when the game is out.
- The four friends' colours (`--p1` red, `--p2` blue, `--p3` green, `--p4`
  yellow) and the track's orange (`--track`) are in `style.css`'s `:root`.
  The hero's track animates each runner at its own pace; with Reduce Motion
  the runners stand on the start line.
- `icon.svg` is a placeholder icon: the track with the four runners. When
  the game has its own icon, export it as `icon-512.png`,
  `apple-touch-icon.png` (180 px) and `favicon.png` (64 px) and link them as
  TrackPrint's pages do.
- `support.html` holds the questions people ask most, the contact email and
  the feedback form. The form posts to the endpoint and contract documented
  in
  [4-friends-feedback](https://github.com/4-Friends-Multiplayer-Running-Game/4-friends-feedback),
  and the report becomes an issue in the game's private repo. It sends the
  version as `? via website`. The function only answers browsers from this
  site's origin (`https://4-friends-multiplayer-running-game.github.io`), so
  the form fails from a local preview or if the site moves to another
  domain: add the new origin to `ALLOWED_ORIGINS` in the function first.
- The footer links to the Impressum, privacy policy and terms of use in the
  public
  [4-friends-legal-docs](https://github.com/4-Friends-Multiplayer-Running-Game/4-friends-legal-docs)
  repo. If those pages move, update the links here too.
- `.nojekyll` makes Pages serve the files exactly as committed.
