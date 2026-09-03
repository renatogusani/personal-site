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

### Clients

There is no separate `vnta-site` repository: `Vantaneant-International-Ltd/vnta`
is the vnta.xyz site, and its `static/CNAME` confirms it.

BUILDT and EZGO Autoworks are listed under VNTA on the Work page. Their names,
one-line descriptions and URLs are taken from VNTA's own site
(`Vantaneant-International-Ltd/vnta`, `src/routes/+page.svelte`), which lists
them publicly. Nothing comes from the client portal in that repo, which holds
confidential material.

Their repositories are private and cannot be reached from a session scoped to
another owner, so neither has a mark.

### Source of truth

`cv-reference.md` backs every claim on the site. It is excluded from the build.
If something is not in that file, it does not belong on a page.

## Where the project images came from

Each card is a screenshot of that site's own current build: clone the repo,
`npm ci && npm run build`, serve the output, capture at a 1200x630 viewport at
2x. Not the repositories' stored `og` images, which were out of date.

| Card | Built from | Route captured |
|:--|:--|:--|
| `vendr.jpg` | `Vantaneant-International-Ltd/vendr`, SvelteKit | `/?preview=live` |
| `eirvox.jpg` | `Vantaneant-International-Ltd/eirvox`, Vite + Svelte | `/#/coming-soon` |
| `maisonseul.jpg` | `Vantaneant-International-Ltd/maisonseul`, SvelteKit | `/` |
| `spacexplorer.jpg` | `renatogusani/SpaceXplorer`, Jekyll | `/` |

Two gates are bypassed deliberately, using each app's own mechanism rather
than a patch:

- Vendr defaults to `PUBLIC_SITE_MODE=coming_soon`. Its page component accepts
  `?preview=live`, which renders `LiveHome` instead of the teaser.
- Éirvox will not boot without Supabase credentials, but it exposes
  `/#/coming-soon` as an always-reachable gate page that renders without them.

Vendr's consent notice (`aside.cb`) is hidden for the capture. It is chrome,
not design.

Webfonts: this environment has no outbound network, so Google Fonts cannot
load. Vendr, Maison Seul and SpaceXplorer do not use any. Éirvox asks for three,
so they are served from the same origin under the exact family names the site
requests, and the capture matches the live page:

| Site asks for | Served |
|:--|:--|
| JetBrains Mono | the real thing, from the local font set |
| Inter Tight | Inter, which Tight is a narrower cut of |
| Newsreader (italic) | Crimson Pro italic, a stand-in |

### Marks

`img/marks/` holds the small square marks used on the home page rows and above
each role on Work, displayed at 26px.

| Mark | Source |
|:--|:--|
| `eirvox` | `eirvox` `public/favicon-192.png`, the real favicon: fox orange on transparent |
| `vendr`, `spacexplorer` | each repository's own `favicon.svg` |
| `vnta` | `vnta` `static/wordmark.svg` |
| `ibm` | the `@iconify-json/logos` set, on IBM blue |
| `dell` | the `simple-icons` package, on Dell blue |

Use a project's real favicon. Nothing reconstructed unless there is no
alternative. Three things worth recording:

- **Éirvox keeps its transparency.** Its own `index.html` says the mark is
  "the fox in fox orange on transparent, so it reads on a light tab bar and on
  a dark one". Do not put it on a tile.
- **Maison Seul has no mark.** It has no real favicon. The circle and dot in
  its repo is a legacy asset and is not used here. It gets no mark rather than
  a wrong one, and it has no wordmark to fall back on.
- **VNTA uses its wordmark, not its symbol.** The sunburst's thin rays do not
  hold at 26px. The wordmark does.
- **IBM and Dell have no reachable official favicon**, so the authentic logo
  path is set in white on the brand's own blue. They link nowhere: the home
  page rows point at `/work/#ibm` instead.

Brown Thomas Arnotts has no mark, and no official asset was available.


### Glyphs

Rows with no brand of their own take a line glyph from `_includes/glyph.html`
instead: `work`, `projects`, `about`, `mail`, `github`, `linkedin`, `document`.
Grey and unfilled, so a navigation row never competes with a real app icon
beside it. Same split as iOS Settings, where app rows carry icons and system
rows carry glyphs.


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
