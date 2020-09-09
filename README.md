# lettre.rs

This site presents lettre's features ans news. Usage docs are on [docs.rs](https://docs.rs/lettre/).

## Development

The site is built using [hugo](https://gohugo.io/).

To initialize the upstream parent theme, run:

```bash
git submodule init
git submodule update
```

Build the site with:

```bash
hugo serve
```

And to include drafts:

```bash
hugo serve --buildDrafts
```
