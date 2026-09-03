# renatogusani.com

Personal site for Renato Gusani: security engineer at IBM, founder of VNTA Group.

![The home page of renatogusani.com](docs/screenshot.png)

## Run it locally

Requires Ruby. Then:

```sh
bundle install
bundle exec jekyll serve
```

The site is served at <http://localhost:4000>. Use `JEKYLL_ENV=production` to
match what GitHub Pages builds, which enables HTML compression and the inlined
critical CSS.

## How it is put together

Built with [Jekyll][jekyll] and deployed by GitHub Pages from `master`.

The theme is [Hydejack][hydejack] v9.1.6, vendored into this repo rather than
pulled in as a gem, so every file can be edited directly. The design is not
Hydejack's: the overrides live in a single file, `_sass/_my-overrides.scss`,
which is imported by both `_sass/my-inline.scss` (the critical CSS inlined into
`<head>`) and `_sass/my-style.scss` (the linked stylesheet). Editing that one
file changes both.

Content is five pages at the repo root: `index.md`, `work.md`, `projects.md`,
`about.md`, `contact.md`.

`cv-reference.md` is the source of truth for every claim on the site. It is
excluded from the build. If something is not in that file, it does not belong on
a page.

## License

Site content and copy: © Renato Gusani. All rights reserved.

The Hydejack theme is © Florian Klampfer and licensed under the
[GPL-3.0](LICENSE.md). See [NOTICE.md](NOTICE.md) for third party attributions.

[jekyll]: https://jekyllrb.com/
[hydejack]: https://hydejack.com/
