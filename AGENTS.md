# AGENTS.md

This file is the agent's rulebook. For a human-readable description of the repository and its workflow, see [README.md](README.md).

## Conventions

- Chapter dirs use the form `ch<chapter>` or `ch<chapter>.<part>`, where the first integer is the chapter number and the second (after the dot) is the part number within that chapter (e.g. `ch3`, `ch3.1`, `ch10.5`). Omit the part when there is only one part.
- Page files are zero-padded 3-digit numbers: `001`, `002`, ... `999`. Stop and ask the user if overflow `999`. Page numbering is continuous across sub-parts of the same chapter (e.g. `ch1.1` has `001`, `002`; `ch1.2` continues with `003`, `004`).

## Rules

### General

- Don't guess. Ask immediately if you have any questions.
- Do not override existing files on rename. Confirm with the user before any delete or overwrite of an existing file.
- Write permission is granted only to `translated/` and the system temp folder. Ask before writing elsewhere.
- Never use `…`. Write it as `...`.

### Python usage

- Use `source .venv/bin/activate` to execute Python scripts in isolation. If you don't have a venv, create one with `uv venv --python 3.12`.

### Translation scripts (`translated/<ch>/script.md`)

- **Authoritative template** - [docs/ts-example.md](docs/ts-example.md) is the source of truth. Before any create or edit on a `translated/<ch>/script.md`, read it in full. Do not skip this step.
- MISTAKE comments like `<!-- MISTAKE: ... -->` are flags left by a previous pass. When reading a script, skip them; their content is not authoritative.

#### Text extraction

- Use `raws/<ch>` as source for text extraction if script doesn't present.
- OCR is server-side only. Stop and ask if you can't perform this.
- Use only manga/comics specific OCR.
- Don't modify text, give as it is. Insist on verbatim(don't "clean up" punctuation, dakuten, small kana, furigana).
- Manga reads right-to-left, top-to-bottom. For panels side-by-side, the right panel's content comes first.

#### Table format

- If it's a background SFX outside a bubble, it lives only in the SFX summary table at the end of the file.
- One text container (speech bubble, narration box, caption, sign, thought bubble) = one entry with one [pXXX.YYY] id. Never merge two containers, never split one container across entries.
- Use 3-digit, zero-padded ids: entries after the page (`p001.001`, `p001.002`, ...) and SFX with no page separator (`sfx001`, `sfx002`, ...).
- Duplicate the entry if the same text appears in more than one container (e.g. two characters both saying `ハァ`).
- If asked for translation, include 3 options.
- Translate into English only unless instructed otherwise.

#### Parse by template

- Fill template placeholders (`<ch>`, `<summary>`, `<...>`) from the chapter's raws. If raws are unavailable, stop and ask the user.
- Follow template format.

#### Status

- The YAML front matter `status` field declares the script's stage. Allowed values: `open` (in progress, editable) and `closed` (finished, locked from edits). If missing or undefined, treat as `open`.
