# J.R. Mattson | Maker Portfolio

**Live site: https://jamesmattson.github.io/Portfolio/**

A selection of design and fabrication work from Fully and Trillium Pacific: product development, CNC machining, furniture, architectural millwork, signage, and shop tooling.

Contact: [james.mattson@gmail.com](mailto:james.mattson@gmail.com) · [LinkedIn](https://www.linkedin.com/in/j-r-mattson-95495b193/)

## How it's built

A static single-page site with no framework and no build step. Plain HTML, CSS, and JavaScript, hosted on GitHub Pages.

- **Masonry grid.** A small JavaScript function places each photo in the shortest column. Photo dimensions are stored ahead of time, so the layout doesn't shift as images load.
- **Filter console.** Tags are grouped into Company, Process, Material, and Item Type and shown as stamped labels. You can combine filters.
- **Lightbox.** Uses the native `<dialog>` element, with the photo on one side and its details on the other.
- **Light and dark themes.** Follows the system setting, with a manual toggle.

## Repository layout

| Path | Purpose |
|---|---|
| `index.html` | The site |
| `data.js` | Every photo's title, company, description, and tags. The array order is the display order. |
| `images/thumb/`, `images/full/` | Web-sized images: 800px for the grid, 2000px for the lightbox |
| `tools/tag.html` | Local editor for titles, tags, descriptions, order, and deletions. Writes `data.js`. |
| `tools/sync.py` | Builds the web images from the original photos and merges new ones into `data.js` |
| `docs/design.md` | Design brief |

## Updating

```
python tools/sync.py     # add new photos; archive the originals of deleted ones
git add -A && git commit -m "Update portfolio" && git push
```

`sync.py` needs Python 3 and Pillow (`pip install pillow`). The full-resolution originals are not stored in this repository.
