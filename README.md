# renatogusani.com

Personal site for Renato Gusani: security engineer at IBM, founder of VNTA Group.

![The home page of renatogusani.com](docs/screenshot.png)

## Run it locally

Requires Ruby. Then:

```sh
bundle install
bundle exec jekyll serve
```

Served at <http://localhost:4000>.

## How it is put together

Jekyll, deployed by GitHub Pages from `master`. There is no theme. The whole
front end is:

| File | What it does |
|:--|:--|
| `_layouts/default.html` | The only layout. Every page uses it. |
| `_includes/topbar.html` | The back bar on every page except home. |
| `_includes/socials.html` | Email, GitHub and LinkedIn icons on the home page. |
| `_includes/schema.html` | Person and WebSite structured data, home page only. |
| `_includes/cards.html` | Project cards with a preview image. Takes an `items` array. |
| `_includes/group.html` | The grouped row list. Takes a `rows` array. |
| `_includes/footer.html` | Footer and the dynamic copyright year. |
| `assets/css/main.scss` | The only stylesheet. Palette, type and components. |

Content is five pages at the repo root: `index.md`, `work.md`, `projects.md`,
`about.md`, `contact.md`.

### Grouped rows

Lists are rendered as iOS style grouped rows rather than prose. Define them in a
page's front matter and pass them to the include:

```yaml
now:
  - name: IBM Security
    meta: "Security Engineer, Randori · since January 2024"
    url: /work/#ibm
  - name: SpaceXplorer
    meta: "SpaceX and NASA APOD APIs · 2023"
    url: https://spacexplorer.info
    ext: true          # external, gets the outbound icon instead of a chevron
```

```liquid
{% include group.html rows=page.now %}
```

`name` is required. `meta`, `url` and `ext` are optional. A row without a `url`
renders as plain text with no chevron.

### Design

Dark only, on Apple's elevated dark greys rather than pure black: a lifted
near black ground with one raised surface for grouped rows, hairline separators,
a single blue accent, system font stack, no webfonts and no JavaScript beyond
the two lines that keep the copyright year honest.

Navigation follows the iOS root and detail pattern. The home page is the root
screen: name, one grey line, then everything else as a tappable list. Every
other page sits one level below it and carries a single back link, so there is
no nav bar to maintain.

Every text colour in `main.scss` is annotated with its contrast ratio and clears
WCAG AA. CI does not check that, so if you change the palette, check it.

### Source of truth

`cv-reference.md` backs every claim on the site. It is excluded from the build.
If something is not in that file, it does not belong on a page.

## Where the brand assets came from

The project card images and the small row marks are each venture's own
artwork, pulled from their repositories rather than recreated:

| Asset | Source |
|:--|:--|
| `img/projects/vendr.jpg` | `Vantaneant-International-Ltd/vendr` `static/og.png` |
| `img/projects/eirvox.jpg` | `Vantaneant-International-Ltd/eirvox` `public/og-image.png` |
| `img/projects/spacexplorer.jpg` | `renatogusani/SpaceXplorer` `images/og-card.png` |
| `img/marks/*.png` | each repo's `favicon.svg`, plus Éirvox `public/brand/symbol.png` |

`img/projects/maisonseul.jpg` is the exception. That repo ships no preview
card, so it is composed here from Maison Seul's own wordmark, descriptor
("house of absence"), mark and palette (`#0b0907` on `#e9e0d2`), all read out
of `Vantaneant-International-Ltd/maisonseul`. Replace it if a real card
appears upstream.

All four are 1200x630, served as JPEG at 2x for a card about 600px wide.

## SEO

`jekyll-seo-tag` handles titles, descriptions, canonical URLs, OpenGraph and the
Twitter card. On top of that:

- `_includes/schema.html` emits Person and WebSite JSON-LD on the home page,
  with `sameAs` pointing at LinkedIn, GitHub and SpaceXplorer. This is what
  connects the domain to those profiles in Google's eyes.
- `assets/img/og.png` is the 1200x630 preview card, applied to every page
  through `defaults` in `_config.yml`. Regenerate it if the role changes.
- Page `title` in front matter is search facing only. The visible heading comes
  from the markdown `#`, so titles can be written for a search result without
  affecting the page.
- `jekyll-sitemap` writes `sitemap.xml` and `robots.txt`.
- `redirect_from` in page front matter points the 2022 site's URLs at their
  replacements: `/resume/`, `/certs/` and `/awards/` go to About, `/volunteering/`
  to Work, and the eleven old coursework URLs to Projects. Theme leftovers like
  `/forms-by-example/` and `/CHANGELOG/` are left to 404 on purpose, because
  redirecting genuinely removed pages to the home page reads as a soft 404.

Search engines cache aggressively. A deploy does not change what is already
indexed, and a stale snippet is not a site bug. Use URL Inspection in Search
Console to force Google. Brave runs its own index with no submission tool, so
it refreshes on its own schedule.

Submit the sitemap once at
[Google Search Console](https://search.google.com/search-console): add
`https://renatogusani.com/sitemap.xml` under Sitemaps.

## Icons

`assets/icons/icon.svg` is the primary favicon, a vector R on the site's ground
colour. `favicon.ico` is the raster fallback at 16, 32 and 48. The PNGs are
full bleed squares because the manifest declares them maskable, so the platform
applies the rounding.

## License

© Renato Gusani. All rights reserved.

Earlier versions of this site were built on the Hydejack theme. No Hydejack code
remains.

## CI

`.github/workflows/build.yml` runs on every push to `master` and every pull
request. It fails on any Jekyll warning, any internal link that does not
resolve, and student-era copy reappearing in the output.
