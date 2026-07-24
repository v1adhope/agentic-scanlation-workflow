# Comics scanlation

There are two ways to work with this repository — both built for iterative, agentic use. The first is fully agentic; the second combines web interaction with agentic capabilities. Both allow you to be productive and perform at your best with increased agentic usage.

## Where to read

- [MangaDex](https://mangadex.org/#link_for_your_title_here)

## Workflow

`raws/` → `translated/` → `precleaned/` → `cleaned/` → `released/`

| Directory | Purpose |
| ------------- | -------------------------------------------------------------------------------------------------------------------------------- |
| `raws/` | Original pages downloaded from the internet, kept untouched and never modified. |
| `translated/` | Translation scripts holding the original extracted text alongside a set of translation options for each container. |
| `precleaned/` | AI-cleaned copies of the raws with compression artifacts, banding, and moiré fixed up so the images are easier to work with. |
| `cleaned/` | Hands-on editing of the precleaned pages in an image editor such as Photoshop, GIMP, or Krita, with redraw, retouch, and typeset of the translated text. |
| `released/` | Final exported PNGs, ready to publish. |
| `assets/` | Supporting material such as cover art, end-page credits, image metadata, and import sheets used during editing. |
| `docs/` | Reference docs and templates that drive the agent workflow. |
| `untracked/` | Folder exists in the repo, but its contents are git-ignored — a local-only working area. |

## Metrics

Per-chapter upload metrics recorded after each release.

| Chapter | Rating | Follows | Comments | Day | Upload timestamp |
| ------- | ------ | ------- | -------- | --- | --------------------- |
| ch1 | 8.4 | 37 | 6 | Wed | 2026-04-08T11:22:00+00:00 |
| ch2 | 8.6 | 483 | 11 | Fri | 2026-04-17T02:07:00+00:00 |
| ch3 | 8.2 | 1271 | 20 | Wed | 2026-04-22T19:56:00+00:00 |
| ch4 | 8.8 | 1701 | 29 | Wed | 2026-04-29T13:36:00+00:00 |
| ch5 | 8.5 | 2489 | 31 | Wed | 2026-05-06T11:44:00+00:00 |
| ch6 | 8.7 | 3063 | 44 | Mon | 2026-05-11T05:24:00+00:00 |
| ch7 | 8.9 | 3495 | 54 | Tue | 2026-05-19T11:46:00+00:00 |

## Observations

Based on my experience, relying entirely on lower-tier agents is not advisable. These models tend to hallucinate text and frequently confuse container ordering. Many lack multimodal support — no computer vision, no OCR — so they attempt to handle it locally, which introduces a whole range of pitfalls.
Python compounds the problem. It's one of the worst languages I've worked with: poor documentation, broken compatibility, and bad tooling across the board.
I settled on a hybrid approach for both economy and accuracy — even top-tier models sometimes struggle with page container ordering. I use Claude's Web UI (Free) for extracting text as-is, and MiniMax M3 via Opencode Go for everything else.
