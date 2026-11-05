# AI Property Search deck

This repository is a slide deck (a product proposal for Connected Investors), published with GitHub Pages:
https://dmitroavramenko.github.io/ai-property-search/

People request changes by mentioning `@claude` in a GitHub issue. Your job: make exactly the requested change to the slides, commit it, and reply briefly.

## Files

- `project/deck.json` - deck index. `order` = slide ids in display order (slide N = `order[N-1]`). `title`, `sections`, `faces` (Google Fonts).
- `project/slides/<id>.html` - one slide per file: exactly ONE `<section id="<id>" ...>` element, nothing before or after it. The file name equals the section id.
- `project-uk/` - the Ukrainian version: same structure (`deck.json` + `slides/<id>.html`), same ids, same order. Shown at `https://dmitroavramenko.github.io/ai-property-search/?lang=uk`.
- `assets/` - images. Reference them as `assets/<name>.jpg`.
- `index.html` - the viewer. Do not edit it unless explicitly asked.
- `.github/workflows/` - never edit.

## Two languages: keep EN and UA identical

- Every change (text, numbers, adding/removing/reordering slides, layout) must be made in BOTH `project/` (English) and `project-uk/` (Ukrainian), unless the request explicitly says only one language.
- Ukrainian text: natural Ukrainian, AI = "ШІ". Keep in English: Connected Investors, AI Property Search, product UI labels (Single Family, Bedrooms 3-4, Est. Value), brand names (Zillow, Trulia, Redfin, BuyAbility), BRRRR, ROI, cash flow, cash-on-cash, off-market, PoC.
- In `project-uk/` headings use `font-family:Roboto, Heebo, Arial, sans-serif` (Heebo has no Cyrillic). Ukrainian is ~15-20% longer: if a title wraps badly, shorten it.

## How people refer to slides

"Slide 5" means the 5th id in `project/deck.json` `order` (1-based). Open that file. Every content slide also shows its number in the footer (bottom right).

## Slide format (strict subset)

- Fixed 1920x1080 canvas. All styling is inline `style=""`. No `<style>`, no classes, no `<script>`, no `margin`, no `z-index`, no `em`/`rem`/`vw`/`var()`. Lengths in px.
- `<section>` always has a `background`. Layout with `display:flex` / `display:grid`, `padding`, `gap`, `align-items`, `justify-content`. A `<div>` without `display` is a flex column.
- `position:absolute` pins an element to the slide (give pinned text a `width`). Content must stay inside 128px margins; footer row sits at `bottom:56px`.
- Allowed elements: `h1 h2 h3 p ul ol li br b i u a span div img table tr th td svg hr aside`, plus `<x-icon name="...">`, `<x-shape kind="...">`.
- `x-icon` names (exact): Activity Book Chart Chat Check CheckCircle Clock Cloud Code Database Globe GraduationCap Home Key Lightbulb Lightning Link Lock PaperPlane Play Search Settings Star ThumbsUp Tool Trust Users Verified Warning Wrench.
- `x-shape` kinds: rect rounded ellipse diamond arrow-right arrow-left arrow-up arrow-down line.
- Font sizes never below 24px. Text wraps only at spaces: about 0.6 x font-size px per character. Inner area is 1664x824 px (1664x792 when the slide has a footer); if text does not fit, shorten it or split the slide rather than shrinking type.
- `<aside>` = speaker notes, last child of the section, plain text.

## Design system (keep it consistent)

- Fonts: headings `font-family:Heebo, Arial, sans-serif` (weight 700-800), body `font-family:'IBM Plex Sans', Arial, sans-serif`.
- Type scale: 120-160 (cover), 72 (slide titles, h2, weight 800, letter-spacing -1px), 44/34/32 (card titles), 28-30 (body), 24 (labels, footer).
- Colors: dark `#111613`, dark card `#1b231e`, light bg `#f5f7f3`, card `#fcfdfb`, border `#e1e6de`, text `#262b28`, muted `#5d655f`, muted on dark `#a9b8ae`, text on dark `#f2f5f0`.
- Accents: green `#68de1f` (on dark), green text on light `#0f7a24`, turquoise `#0fc6db`, CTA yellow `#ffb70e` with dark text `#241a02`.
- Brand gradient: `linear-gradient(120deg, #68de1f 0%, #3bd27f 50%, #1bc9c2 100%)`. Gradient text: `background:<gradient>;background-clip:text;-webkit-text-fill-color:transparent`.
- Eyebrow above each title: 24px, weight 600, `letter-spacing:3px`, uppercase, green.
- Copy a neighbouring slide's markup when adding a new slide so it matches.

## Writing rules

- Slide text: English in `project/`, Ukrainian in `project-uk/`.
- Never use the em dash character (U+2014). Use a plain hyphen `-` instead. Typographic quotes and apostrophes (“ ” ’) are fine.
- Do not invent statistics. If a number is needed and not given, use a bracketed placeholder like `[$__]`.
- Change only what was asked. Do not restyle or rewrite other slides.

## Adding, removing, reordering slides

- Add: create `project/slides/<new-id>.html` (id: letters, digits, `-`, `_`) and insert the id into `order`.
- Remove: delete the file and remove the id from `order`; fix `sections` if a section `start` pointed to it.
- After any add/remove/reorder, update the footer page numbers (`01`, `02`, ...) on every slide whose position changed. Cover (slide 1) and full-bleed statement slides have no footer.

## Finishing

- Commit with a short message describing the change (for example: `Slide 5: shorten title`).
- Reply in the issue in the same language the person wrote in: 1-3 lines on what changed, plus the links `https://dmitroavramenko.github.io/ai-property-search/#<slide number>` and `https://dmitroavramenko.github.io/ai-property-search/?lang=uk#<slide number>`. Mention that the site updates about a minute after the change.
