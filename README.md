# deryaipek.com

Quarto site. Source is Markdown; the build is automated.

## First-time setup

1. **Install Quarto** — <https://quarto.org/docs/get-started/> (free, cross-platform)
2. **Preview locally:** `quarto preview` — opens a browser, live-reloads on save
3. **Create the repo** on GitHub and push this folder
4. **Settings → Pages → Source: GitHub Actions**
5. **Settings → Pages → Custom domain:** `deryaipek.com`
6. **DNS at GoDaddy** — see below
7. Tick **Enforce HTTPS** once the certificate provisions (minutes to an hour)

## DNS records to add at GoDaddy

Four A records on `@` pointing at GitHub's Pages IPs, plus one CNAME:

| Type | Name | Value |
|---|---|---|
| A | @ | *GitHub Pages IP 1* |
| A | @ | *GitHub Pages IP 2* |
| A | @ | *GitHub Pages IP 3* |
| A | @ | *GitHub Pages IP 4* |
| CNAME | www | `USERNAME.github.io` |

Get the current IPs from GitHub's own docs — "Managing a custom domain for your
GitHub Pages site." Do not copy them from a blog post; they have changed before.

**Do not cancel GoDaddy Websites + Marketing until the new site loads at the
custom domain.** Verify first, then cancel.

## Day-to-day editing

Two ways, both fine:

- **In the browser** — open any `.qmd` on github.com, click the pencil, commit.
  The Action rebuilds and the site updates in a couple of minutes. Works from a
  phone.
- **Locally** — edit, `quarto preview` to check, commit, push.

## Adding things

| What | Where |
|---|---|
| Blog post | New folder in `posts/`, with `index.qmd` inside |
| Publication | Copy a `.pub` block in `research.qmd` |
| Talk | Copy a `.pub` block in `talks.qmd` |
| Case study | Copy a `.pub` block in `case-studies.qmd` |
| Dataset or tool | Copy a `.pub` block in `datasets.qmd` |
| Service offering | Copy a `.course` block in `partnerships.qmd` |
| Course | Copy a `.course` block in `teaching.qmd` |
| CV | `assets/cv/`, then uncomment the link in `cv.qmd` |
| Syllabus | `assets/syllabi/` |
| Paper PDF | `assets/papers/` — only where rights allow, see below |
| Slides | `assets/talks/` — you own these |

### PDFs and rights

**Papers:** host only what you have the right to. Most agreements permit the
*accepted manuscript* (post-review, pre-typesetting) but not the publisher's
final typeset PDF. Look the journal up on Sherpa Romeo before uploading.
Otherwise link to the DOI.

**Slides, syllabi, CV:** yours, host freely.

**Data:** small files can live in `assets/data/`. Anything larger goes to Zenodo
— it issues a DOI, which makes the dataset citable and keeps it off the 1 GB
GitHub Pages cap.

Keep every hosted PDF under ~50 MB and compress scans before committing. Git
stores every version forever. Reuse filenames on updates so old links survive.

### Partnerships page — not ready to publish

`partnerships.qmd` is drafted but should stay unpublished until you have
cleared outside-activity disclosure with Brockport and checked NY Public
Officers Law §74. Add `draft: true` to its front matter to keep it out of the
built site; the file stays in the repo. Full checklist is in the comments at the
top of that file.

## Contact form

`contact.qmd` has a form that does nothing until you connect it. A static site
has no backend. Sign up at Formspree or Web3Forms, paste the endpoint into the
form's `action` attribute, and submissions arrive by email. Free tiers are
around 50 submissions per month.

## Design notes

- **Fraunces** for headings, **Atkinson Hyperlegible** for body text (designed
  by the Braille Institute for legibility), **IBM Plex Mono** for metadata
- Palette: petrol ink `#16242B` on warm paper `#FCFBF8`, teal `#2C6E68` for
  links, brass `#B8862B` for hover and focus states
- All three faces cover Latin Extended, so `İ`, `ğ`, `ş` render correctly.
  If any diacritic looks wrong on a device, that is the fallback font — check
  the Google Fonts link in `_quarto.yml` loaded.
- Colors and type live in `styles.scss`. Change them there, not inline.

## Placeholders to replace

Search the source for `<!--` — every setup step and placeholder is commented
inline. The publication entries in `research.qmd` are structural examples, not
your real record.
