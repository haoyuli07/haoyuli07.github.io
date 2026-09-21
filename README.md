# haoyuli07.github.io

Personal academic site. Plain Jekyll with **no plugins**, so GitHub Pages builds
it natively from the `main` branch — there is no Actions workflow and no
`gh-pages` branch to keep in sync.

## Editing content

You should almost never need to touch HTML. Everything lives in `_data/`:

| File | What it controls |
|---|---|
| `_data/publications.yml` | The publication list and the Selected / All tabs |
| `_data/news.yml` | News items, newest first |
| `_data/service.yml` | The Service section |
| `_data/photography.yml` | The `/photography/` page |
| `_config.yml` | Name, email, profile links, site description |

### Adding a publication

Append an entry to `_data/publications.yml`:

```yaml
- id: short-name
  title: "Paper Title"
  authors: [Haoyu Li, Coauthor Name]
  venue: Conference Name
  year: 2026
  selected: true                       # false = only shows under "All"
  preview: /assets/publication_preview/thing.jpg   # optional
  links:
    - name: arXiv
      url: https://arxiv.org/abs/xxxx
```

`selected: true` puts it under the **Selected** tab; `false` means it only
appears under **All**. Your own name is bolded automatically by matching
`author.name` in `_config.yml`.

Keep `_bibliography/papers.bib` updated too if you want BibTeX as the record —
it is excluded from the build and exists purely as a source of truth.

### Adding news

Prepend to `_data/news.yml`. The three newest show by default; the rest go
behind the "Older news" toggle automatically. `text` accepts inline HTML.

### Adding photos

Drop files into `assets/img/photography/` and add entries to
`_data/photography.yml`. The first entry renders large, the rest in a 2-up grid.

## Local preview

```bash
bundle install
bundle exec jekyll serve
```

## Structure

```
_config.yml              site settings and profile links
_data/                   all editable content
_layouts/default.html    the page shell
index.html               home page
photography.html         /photography/
assets/css/style.css     all styling (CSS custom properties at the top)
```

Colors and the content width are CSS variables at the top of `style.css`.
