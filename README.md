# ventures-media

A **public, read-only static file host** for generated images.

It exists for one reason: some APIs fetch media from a URL instead of accepting an
upload — Instagram's Content Publishing API cURLs `image_url` from a public
server, and a bulk listing import needs a direct-download URL per image. The
repositories that *generate* these images are private, so their raw URLs are not
publicly reachable. The generated files those APIs must fetch are served from
here instead, over GitHub Pages.

Base URL: **https://fakepersonvm.github.io/ventures-media/**

## What is in here

- **Generated image files only**, plus this README and the two files Pages needs.
  Nothing else: no source, no scripts, no documents, no data.
- Top-level directories are **namespaces**, one per consumer of the host.
- **Paths are stable.** A file published at a path keeps that path, because live
  posts and listings point at it. Regenerating a batch overwrites bytes in place
  rather than moving them.
- `healthcheck/probe.jpg` is a fixed probe file for reachability checks. It never
  moves and its bytes never change.

## Two things that are load-bearing

- `.nojekyll` must exist. Without it, GitHub Pages runs its Jekyll step, which
  silently drops every path with a leading underscore — and some namespaces use
  them.
- GitHub Pages serves `.jpg` as `Content-Type: image/jpeg`, which is what the
  fetching APIs require. Do not rename files to extensions Pages does not map.

## Housekeeping

Everything here is machine-written by an automated job and nothing here is a
source of truth; the originals live elsewhere. Not accepting issues or pull
requests. No analytics, no cookies, no scripts are served from this host.
