# yt-embed-relay

A one-file page that embeds a YouTube video from a normal https origin.

YouTube rejects embeds that arrive without an HTTP Referer ("Error 153 / Video player
configuration error"). Apps that render HTML from a custom URL scheme — for example
AnkiMobile, which loads cards from `ankifile://` — send no Referer, so a direct
`youtube.com/embed/...` iframe fails there. Embedding this page instead works around it:

```html
<iframe src="https://jhonmaker-gonsu.github.io/yt-embed-relay/yt.html?v=VIDEO_ID&start=324&end=330"
        allow="autoplay; encrypted-media; picture-in-picture; fullscreen" allowfullscreen></iframe>
```

Parameters: `v` (11-character video id, required), `start` / `end` (seconds, optional).
