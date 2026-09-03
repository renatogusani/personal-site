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
| `_includes/nav.html` | Top navigation, driven by `nav:` in `_config.yml`. |
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

Dark only. Pure black ground, one raised surface for grouped rows, hairline
separators, a single blue accent, system font stack, no webfonts and no
JavaScript beyond the two lines that keep the copyright year honest.

Every text colour in `main.scss` is annotated with its contrast ratio and clears
WCAG AA. CI does not check that, so if you change the palette, check it.

### Source of truth

`cv-reference.md` backs every claim on the site. It is excluded from the build.
If something is not in that file, it does not belong on a page.

## License

© Renato Gusani. All rights reserved.

Earlier versions of this site were built on the Hydejack theme. No Hydejack code
remains.

## CI

`.github/workflows/build.yml` runs on every push to `master` and every pull
request. It fails on any Jekyll warning, any internal link that does not
resolve, and student-era copy reappearing in the output.
