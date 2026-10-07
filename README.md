# lovegroove.app

The website for [Lovegroove](https://lovegroove.app) (formerly Gramophile), served by
GitHub Pages from `main` at **https://lovegroove.app**. Plain static files: no server,
build step or keys.

| Path | What it is |
|---|---|
| `/` (`index.html`) | Landing page. Shows an App Store button by itself once the app is released. |
| `/listen/` (`listen/index.html`) | The page songs shared from the app open: the song, its cover, and buttons for Apple Music, Spotify, TIDAL, YouTube Music, Deezer and Discogs. |
| `/privacy` (`privacy.html`) | Privacy policy — the URL for App Store Connect. |
| `/spotify-callback.html` | Hands Spotify's sign-in back to the app (Spotify only redirects to HTTPS pages): to `lovegroove://`, or `gramophile://` for builds from before the rename. |
| `CNAME` | The custom domain, `lovegroove.app`. |

## Domain

`lovegroove.app` is registered with Cloudflare. DNS points at GitHub Pages and must stay
**DNS only** (grey cloud) so GitHub can issue the HTTPS certificate:

- `A @` → 185.199.108.153, 185.199.109.153, 185.199.110.153, 185.199.111.153
- `AAAA @` → 2606:50c0:8000::153, 2606:50c0:8001::153, 2606:50c0:8002::153, 2606:50c0:8003::153
- `CNAME www` → pezm.github.io

Email: Cloudflare Email Routing forwards **hello@lovegroove.app** to the owner's inbox.

This repo was called `gramophile-listen`. The old address, `pezm.github.io/gramophile-listen/…`,
is kept alive by a small separate repo of that name whose pages forward to the same path and
query here; song links in the old format (`/?t=…`) then forward to `/listen/`. Links shared
before the move, and Spotify setups that registered the old callback address, still work.

## Song link format

```
https://lovegroove.app/listen/?t=Space%20Song&a=Beach%20House&al=Depression%20Cherry&i=998474199&c=GB&f=vinyl
```

| Parameter | Meaning | Required |
|---|---|---|
| `t`  | Song title | yes |
| `a`  | Artist | recommended |
| `al` | Album | optional |
| `i`  | Apple Music track id | optional; gives the exact song and cover |
| `c`  | Store country for Apple's lookup, e.g. `GB` | optional |
| `f`  | What it's playing on: `vinyl`, `cd`, `tape` | optional |
| `td` | TIDAL track id (when the sharer has TIDAL connected) | optional; TIDAL opens the exact song |

The cover and exact Apple Music song come from Apple's free iTunes lookup.

## Try it locally

```bash
python3 -m http.server 8765
```

then open <http://localhost:8765/listen/?t=Space%20Song&a=Beach%20House&i=998474199&c=GB&f=vinyl>.
