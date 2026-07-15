# Comic scanlation

There are two ways to work with this repository — both built for iterative, agentic use. The first is fully agentic; the second combines web interaction with agentic capabilities. Both allow you to be productive and perform at your best with increased agentic usage.

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

## Observations

Based on my experience, relying entirely on lower-tier agents is not advisable. These models tend to hallucinate text and frequently confuse container ordering. Many lack multimodal support — no computer vision, no OCR — so they attempt to handle it locally, which introduces a whole range of pitfalls.
Python compounds the problem. It's one of the worst languages I've worked with: poor documentation, broken compatibility, and bad tooling across the board.
I settled on a hybrid approach for both economy and accuracy — even top-tier models sometimes struggle with page container ordering. I use Claude's Web UI (Free) for extracting text as-is, and MiniMax M3 via Opencode Go for everything else.
