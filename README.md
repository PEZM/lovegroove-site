# Gramophile — listen page

The page a song shared from [Gramophile](https://apps.apple.com/app/id6817066973) links to.
It shows the song and its cover and opens it on Apple Music, TIDAL (exact
song when the link carries its id) and Deezer (looked up on the page), the
Spotify app's search, and YouTube Music, and links to the record on Discogs.

Live at **https://pezm.github.io/gramophile-listen/** (GitHub Pages, from `main`).

## Link format

```
https://pezm.github.io/gramophile-listen/?t=Space%20Song&a=Beach%20House&al=Depression%20Cherry&i=998474199&c=GB&f=vinyl
```

| Parameter | Meaning | Required |
|---|---|---|
| `t`  | Song title | yes |
| `a`  | Artist | recommended |
| `al` | Album | optional |
| `i`  | Apple Music track id | optional; gives the exact song and cover |
| `c`  | Store country for Apple's lookup, e.g. `GB` | optional |
| `f`  | What it's playing on: `vinyl`, `cd`, `tape` | optional |
| `td` | TIDAL track id (added when the sharer has TIDAL connected) | optional; TIDAL opens the exact song |

A single static file: no server, build step or keys. The cover and exact Apple
Music song come from Apple's free iTunes lookup. Once Gramophile is on the App
Store, a "Get Gramophile" button appears by itself.

## Try it locally

```bash
python3 -m http.server 8765
```

then open <http://localhost:8765/?t=Space%20Song&a=Beach%20House&i=998474199&c=GB&f=vinyl>.
