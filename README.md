# panel'd: teacher setup

## What's in this folder
- `index.html` is the whole app in one file. It has no outside dependencies and its fonts are built in.
- `library.json` lists the page images students can pick from (the "Class library" tab).
- `pages/` holds your page images. `pages/demo/` is sample art you can delete.

## Put it online (GitHub Pages)
1. Upload this whole folder to a GitHub repo, then go to **Settings → Pages → Deploy from branch**.
2. To put it in Google Sites, use **Insert → Embed → By URL** and paste your GitHub Pages link.
   Don't use "Embed code". The class library loads `library.json` from the same address, so it only works when you embed by URL.

## Add a book's pages
Put the JPGs in a folder, for example `pages/persepolis/01-the-veil/p001.jpg` through `p008.jpg`.
Then describe the folder in `library.json`:

```json
{ "title": "The Veil", "folder": "pages/persepolis/01-the-veil/",
  "prefix": "p", "count": 8, "start": 1, "pad": 3, "ext": ".jpg", "firstPage": 3 }
```
- `firstPage` is the **book's** page number for the first image, so citations auto-fill with real page numbers.
- If your files don't follow a numbered pattern, list them yourself:
  `"pages": [{"src":"pages/x/cover.jpg","page":1}, "pages/x/next.jpg"]`
- A chapter with `"count": 0` shows no library pages, so students upload their own.
- Set `"preset": "persepolis"` for Persepolis prompts. Any other value uses the general graphic-novel prompts.

## Handy links
- `index.html?book=persepolis&chapter=The%20Veil` fills in the book and chapter on the setup screen.
- `index.html?lib=other-library.json` loads a different library file.

## Student work
Work autosaves on the device. Students hand in work with **Export → Download PDF**. To keep a copy they can reopen on any device, they use **Save → Save progress file** (a `.paneld` file).

## Study types
On the setup screen, students choose one of four study types: **Comic / Graphic Novel**, **Novel — Chapter Study**, **Page / Passage Annotation**, or **Political Cartoon**.
- A link ending in `?type=annot` (or `novelch`, `cartoon`, `comic`) opens with that type already selected.
- To put novel pages or cartoons in the class library, add `"kind": "novel"` or `"kind": "cartoon"` to the book entry in `library.json`. Cartoon labels can be words instead of page numbers:

```json
{ "id": "ush-cartoons", "title": "USH Political Cartoons", "kind": "cartoon",
  "chapters": [ { "title": "11.5 Industrialization", "pages": [
    { "src": "pages/cartoons/bosses-of-the-senate.jpg", "page": "Bosses of the Senate" } ] } ] }
```
