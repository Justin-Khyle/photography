# Justin Khyle Photography

Static portfolio site. No build step: just `index.html` (plus a `photos/` folder once you add images).

## Adding your photos
1. Create a `photos/` folder next to `index.html` and put your JPGs in it (resize to ~2000px on the long edge, quality ~80, to keep the page fast).
2. In `index.html`, find the `SITE` config near the bottom. For each photo, add `src` and remove `sample`:
   ```js
   { title: "Ocean Beach, last light", place: "San Francisco", cat: "Landscape",
     src: "photos/ocean-beach.jpg", exif: "X-T5 · 23mm · f/8 · 1/250s · ISO 160" },
   ```
   Add `tall: true` for portrait-orientation shots, and `featured: true` for your best shots — those are what the Home tab shows. Every photo still appears under its own category.
3. Once every photo has a `src`, you can delete the `PALETTES` / `sampleImage` block.

## Top photos
Set `SITE.heroes` — one photo per tab (`Home`, `Street`, `Landscape`, `Portrait`). Clicking a tab cross-fades the top photo and scrolls back up. Wide (landscape) shots work best.

## Image sizes
Each photo comes in three versions in `photos/`:
- `name-800.jpg` and `name-1600.jpg` (long edge), for grids and phones
- `name-full.jpg`, the original resolution at high quality

The page picks automatically: the grid and carousel use the smallest file that's sharp on the visitor's screen, and the full-screen viewer swaps in `-full` on large or high-density displays (not when Data Saver is on). When you add a photo, create all three.

## Categories
Edit `categories` in `SITE`. Each photo's `cat` must match one of them.

## Social links
Edit `SITE.socials` — each entry has a label, handle, and URL. They show in the Contact section and footer.

## Link previews
The `<head>` has preview tags for iMessage, Instagram, LinkedIn, etc. Two things to update once hosted:
1. Change `https://justin-khyle.github.io/photography/` in the `og:url` and `og:image` tags to the site's real address.
2. Add `photos/preview.jpg` (1200×630, one of your best wide shots).

## Pages
The site is one `index.html` with four pages, switched by the link's `#`:
- `#home` (default): a slideshow of the photos listed in `SITE.homeSlides` (each shows ~3 seconds, then fades; `"hero"` means the canyon road photo; change `SLIDE_MS` in the script for a different speed), plus Instagram and YouTube
- `#work`: the Selected collage (the photos listed in `SITE.selected`, in that order), then an index of three cards (Street, Landscape, Portrait). Each card's cover is `photos/card-<tab>.jpg`, a smaller copy of that tab's top photo; clicking opens `#street`, `#landscape` or `#portrait` with the banner, tabs and carousel
- `#about` and `#contact`

The browser's back button moves between pages and tabs.

## Tab links
Each tab has its own link: `#street`, `#landscape`, `#portrait` (e.g. `.../photography/#portrait`). The back button moves between tabs.

## Contact form
Sends through Formspree (form ID `meaajvno`). Messages go to the email on that Formspree account.

## Hosting on GitHub Pages
- Option A: new repo (e.g. `photography`) → push these files → Settings → Pages → deploy from `main`. URL: `justin-khyle.github.io/photography`.
- Option B: put it in a `photography/` folder inside your existing `justin-khyle.github.io` repo.

## Turning on booking and prints later
`SITE.features = { booking: false, shop: false }`. Setting either to `true` adds the nav link and shows its section (`#book`, `#shop`). Those sections are placeholders; fill them with a booking embed or your own backend when ready.
