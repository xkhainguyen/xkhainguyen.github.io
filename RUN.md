# MY MODIFICATIONS

## Build locally

```bash
bundle exec jekyll serve --lsi
```

## Change overall size

In `_base.scss`, add

```html
HTML {
  font-size: 14px;
}
```

## Change size of news posts

In `_base.scss`,

```html
table {
  td, th {
    color: var(--global-text-color);
  }
  td {
    font-size: 1.0rem;
  }
}
```

## Make publication preview bigger

In `bib.html`, modify

```html
<div class="col-sm-3 {% if entry.preview %}preview{% else %}abbr{% endif %}">
```

## 