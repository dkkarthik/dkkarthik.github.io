# Karthik Dantu's website

Personal academic website built with the al-folio v1 starter and the pinned `al_folio_core` theme gem. Navigation contains About, Projects, Publications, and News.

## Content

- `_pages/about.md`: biography, profile, affiliations, and homepage links.
- `_data/socials.yml`: email and social profiles.
- `_projects/*.md`: the five project pages, images, paper links, and funding acknowledgments.
- `_pages/projects.md`: project overview using al-folio's project cards.
- `_bibliography/papers.bib`: 71 publication records: all 65 records from `../lab-website/redesign`, merged with the existing references. Twenty-two short references were enriched with complete lab citations; six additional references were retained. See `docs/publications-import.md` for provenance and matching decisions.
- `_news/*.md`: five announcements. The original site supplied years only, so the News page groups by year without fabricated month/day dates.
- `assets/img/`: profile, funding, and project media.

## Local development

Use Ruby 4.0.7 (the tested version) and Node 22 or newer:

```sh
bundle config set --local path vendor/bundle
bundle install
npm ci
bundle exec jekyll serve
```

Visit <http://localhost:4000/>. This is a root GitHub Pages site, so `baseurl` is empty rather than the starter demo's `/al-folio`.

On this Mac, Homebrew Ruby is available at `/opt/homebrew/opt/ruby/bin`. Put it first on `PATH` if the shell selects the older Ruby 3.1 installation. Dependencies installed during migration are in `vendor/bundle`.

## Validation

```sh
npm run lint:prettier
npm run lint:style-contract
bundle exec al-folio upgrade audit --no-fail
bundle exec al-folio upgrade overrides audit
bundle exec jekyll build
```

The style-contract check follows the upstream starter checks, with the upstream demo-test file requirements replaced by this site's four required page files. The site intentionally overrides `assets/css/main.scss` to append UB branding after the upstream theme imports. The override is reviewed and recorded in `.al-folio-overrides.yml`; `_layouts/bib.liquid` adds a conditional Publicity line below the publication buttons. Both overrides are recorded in `.al-folio-overrides.yml`; other layouts, includes, and JavaScript remain gem-owned.

## Deployment

`.github/workflows/deploy.yml` validates and builds pushes to `master`/`main`, then publishes `_site` to `gh-pages`, matching the existing GitHub Pages configuration. Pull requests build without deploying. The migration branch does not automatically deploy.

## Starter provenance

Downloaded from <https://github.com/alshedivat/al-folio> at commit `f2a2765c8a9413f6ec703fc02070fbe6becf1572`. Followed the upstream `AGENTS.md`, ownership boundaries, [Codex bootstrap skill](https://github.com/alshedivat/al-folio/blob/f2a2765c8a9413f6ec703fc02070fbe6becf1572/.agents/skills/al-folio-bootstrap/SKILL.md), and [migration skill](https://github.com/alshedivat/al-folio/blob/f2a2765c8a9413f6ec703fc02070fbe6becf1572/.agents/skills/al-folio-v1-migration/SKILL.md).

The upstream bootstrap validation was adapted to this site's root URL. Runtime gems and paired configuration/plugin wiring are retained; unused blog, CV, newsletter, archives, and demo features are disabled. Upstream reference documentation is in `docs/`.

## UB branding

- Colors: UB Blue `#005BBB` and Hayes Hall White `#FFFFFF`, with Harriman Blue `#002F56` for hover accents. See [UB color guidance](https://engineering.buffalo.edu/home/internal/communications/identity-brand.html).
- Typography: `Sofia Pro, Arial, sans-serif`. Sofia Pro is used when installed on a visitor's computer; otherwise the site uses [UB's approved Arial substitute](https://www.buffalo.edu/brand/creative/typography/font-substitutes.html). Licensed Sofia Pro web-font files are not bundled with this site.
- Logo: the original [DRONES Lab logo](https://droneslab.github.io/assets/media/drones-lab-logo.png), stored locally without recoloring or altering its proportions.
- Appearance: light-only, including for visitors who previously selected dark mode. The four navigation tabs are unchanged.
- Customization: edit the site-owned branding section at the bottom of `assets/css/main.scss`. When updating the theme, review upstream changes with `bundle exec al-folio upgrade overrides diff assets/css/main.scss`.

Publication media coverage is maintained in `_data/publicity.yml`, keyed by the BibTeX entry ID. Entries without coverage do not show a Publicity label. Award links are maintained in `_data/publication_awards.yml`; awards appear on a separate line below publicity, with a fallback to the BibTeX `award` field when no structured links are provided.

News entries use a bold month and two-digit year prefix, such as `**[Sep 26]**` for September 2026. Do not include the day of the month.
