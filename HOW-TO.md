# How to change The Cafe Between

Everything here can be done on github.com in a browser, from any computer.
After every change (a "commit"), GitHub rebuilds the site. Wait a minute or
two, then refresh the live page. To follow a rebuild, open the **Actions** tab:
a green tick means it's live, a red cross means something broke (see the end).

Live site: https://anastasiiakhmara-commits.github.io/cafe-between/

---

## Where things are

| Folder / file        | What it is                                                    |
|----------------------|---------------------------------------------------------------|
| `_october/`          | The October stories, one `.md` file per story                  |
| `images/`            | Illustrations                                                  |
| `styles/main.css`    | ALL the looks: colours, fonts, sizes, frames. The playground.  |
| `_config.yml`        | Site title, tagline, author, collection names                  |
| `index.html`         | The landing page                                               |
| `_layouts/`          | Page templates (story page, contents page, shared header/footer) |
| `_includes/`         | Small reusable bits (the illustration frame, story openings)   |

Folders starting with `_` don't appear on the site themselves; Jekyll uses
them to build the pages.

---

## Add a story

1. Go into `_october/` → **Add file → Create new file**.
2. Name it with lowercase words and hyphens, ending in `.md`. The name
   becomes the web address: `the-horror.md` → `/october/the-horror.html`.
3. Start the file with this block, exactly with the three dashes:

   ```
   ---
   title: The Horror
   order: 5
   image: the-horror.jpg
   image_alt: "A short description of the drawing, for screen readers"
   ---
   ```

   - `order` is the position in the collection (see "Reorder" below).
   - No illustration yet? Delete the `image` and `image_alt` lines. A
     placeholder frame appears instead.

4. Paste the story under the block. **Leave an empty line between
   paragraphs.** A single line break is NOT a new paragraph.
5. **Commit changes.** The contents page, the numbering and the
   Previous/Next links all update by themselves.

Typography notes:
- Use curly quotes ‘ ’ for dialogue, like the other stories.
- For a scene break inside a story, put this on its own line, with empty
  lines around it: `<hr class="scene-break">`
- `*word*` makes *italics*.

## Reorder stories / put one in between

Each story's `order:` number decides its place. They don't need to be
consecutive, only in the right sequence. To slot a story between 2 and 3,
give it `order: 2.5`. Or renumber them all; either works. Addresses don't
change when the order does.

## Add or replace an illustration

1. Prepare the image first. It should be portrait, about **1400 px tall**,
   JPG, **under ~500 KB**. Free tool: https://squoosh.app, which runs in
   the browser.
2. In `images/` → **Add file → Upload files**, then commit.
3. In the story's `.md` file, set `image:` to the exact file name
   (it's case-sensitive: `The-Horror.JPG` ≠ `the-horror.jpg`).

Replacing a drawing: upload a file with the same name and it overwrites
the old one.

## Fix a typo

Open the story file → pencil icon (✎) → edit → **Commit changes**.

## Change colours, fonts, sizes

Everything is in `styles/main.css`, with a comment above each section.
- Colours: section 2. There are two sets: light mode, and dark mode
  (written twice; keep both copies identical).
- Fonts: section 1 has two ready-to-paste alternatives.

## Change the title, tagline, collection name or subtitle

`_config.yml`: `title`, `description` (the tagline), and under
`collections → october`: `title`, `subtitle`, `note`.

## Start a new collection later (e.g. winter)

1. In `_config.yml`, copy the whole `october:` block under `collections`,
   rename it `winter:` and change its permalink to `/winter/:name.html`.
   Also copy the `defaults` block and change `type: october` to `type: winter`.
2. Create the folder `_winter/` with stories in it, same format as above.
3. Create `winter/index.html` containing only:
   ```
   ---
   layout: collection
   title: Winter Stories
   stories: winter
   ---
   ```
4. Add a link to it on the landing page (`index.html`, the COLLECTIONS part).

(Or just ask Claude to do it.)

## Keep unfinished stories out of here

This repository is public: anyone can read every file in it, even files
the site doesn't show. Keep drafts somewhere else until they're ready.

## If the site breaks (red cross in Actions)

Usually it's a typo in the block between the `---` lines. Check:
- the three dashes are there, top and bottom;
- `title:` has a space after the colon;
- text with a colon in it is in quotes: `image_alt: "Night: the forest"`.

Fix it and commit again. The previous version of the site stays live
until a build succeeds, so readers never see a broken page.
