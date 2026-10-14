# Hauntings Show podcast feed

This repository is intended to publish the podcast RSS feed and, if desired,
episode audio through GitHub Pages.

## Planned public URLs

- Feed: https://feed.hauntingsshow.com/feed.xml
- Episode 1 audio: https://feed.hauntingsshow.com/261013-Hauntings-HellHouse.mp3
- Show cover art: https://feed.hauntingsshow.com/cover.jpg
- Episode 1 cover art: https://feed.hauntingsshow.com/261013-Hauntings-HellHouse-cover.jpg

## Files

- `feed.xml` — RSS 2.0 feed with Apple Podcasts-compatible iTunes metadata.
- `cover.jpg` — add the final square podcast cover art here.
- `261013-Hauntings-HellHouse.mp3` — Episode 1 (Hell House) audio.
- `261013-Hauntings-HellHouse-cover.jpg` — Episode 1 (Hell House) cover art.
- `.nojekyll` — disables Jekyll processing for this static site.

## Before submitting the feed to directories

1. Replace every `REPLACE...` placeholder in `feed.xml`.
2. Add `cover.jpg`. Use square JPG or PNG artwork, ideally 3000 × 3000 px
   (Apple accepts 1400 × 1400 through 3000 × 3000 px for RSS artwork).
3. Add the episode MP3 and update the enclosure's `length` to the exact file
   size in bytes. Keep the URL exactly aligned with the uploaded filename.
   Add the episode's cover art as `{episode-name}-cover.jpg`, where
   `{episode-name}` is the MP3 filename without `.mp3`, with the same size
   requirements as `cover.jpg`.
4. Replace the example publication date with the real date/time in RFC 2822
   format, including timezone.
5. Generate stable unique IDs for the show and episode, then do not change them
   after publication.
6. Ensure the feed and audio are publicly accessible over HTTPS.
7. Validate the XML and test the published feed and MP3 URL before submitting.

**Important:** This is a starter template, not a submission-ready feed. The
draft episode's enclosure length and several metadata fields are placeholders.
Podcast directories may reject it until those values and the actual audio and
artwork are in place.

## Enable GitHub Pages

In the repository, open **Settings → Pages**. Under **Build and deployment**,
choose **Deploy from a branch**, select `main` and `/(root)`, then save.
After GitHub Pages finishes deploying, the feed should be available at
`https://feed.hauntingsshow.com/feed.xml`.

## Custom domain

The site is served from `feed.hauntingsshow.com` (the `CNAME` file tells
GitHub Pages which domain to use). It needs one DNS record at the domain
registrar:

| Type  | Name | Value                    |
|-------|------|--------------------------|
| CNAME | feed | hauntings-show.github.io |

`hauntingsshow.com` and `www.hauntingsshow.com` are separate: they redirect to
the show's info page at https://www.ruiz-knott.com/hauntings. Don't point them
at GitHub Pages.

**The feed URL `https://feed.hauntingsshow.com/feed.xml` must never change.**
To move hosting later, serve the same path from the new host and repoint the
`feed` CNAME record. Audio and image URLs can change freely; just update them
in `feed.xml`.

## Editing the feed

Edit `feed.xml` directly in GitHub or locally with Git. When adding an episode,
add a new `<item>` near the top of the channel's episode list (newest first).
Use a unique, stable `<guid>` for each episode. Do not change an episode's GUID
after publication, even if you correct its title or description.

Each episode has its own cover art, set with an `<itunes:image>` tag inside its
`<item>`, for example:

```xml
<itunes:image href="https://feed.hauntingsshow.com/261013-Hauntings-HellHouse-cover.jpg"/>
```

Apps that don't support episode art show the show's `cover.jpg` instead.
