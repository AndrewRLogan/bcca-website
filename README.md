# bcca-website

Static Jekyll site for the Bassendean Community Children's Association, hosted on
GitHub Pages. GitHub Pages builds the site itself on push — the `Gemfile` here is
only so you can preview changes locally.

- Pages: `index.html`, `about.html`, `contact.html`
- Shared chrome: `_layouts/default.html`, `_includes/`
- Committee members and nav links: `_data/committee.yml`, `_data/navigation.yml`
- Styles: `assets/css/style.css`
- Custom domain: `CNAME`

## Local preview

Requires [Ruby](https://rubyinstaller.org/) (Ruby+Devkit build on Windows).

```powershell
gem install bundler
bundle install
bundle exec jekyll serve --livereload
```

Then open <http://127.0.0.1:4000/>. There is also a "Serve site locally" VS Code
task (`Terminal → Run Task`).

If `ruby -v` resolves to a Ruby bundled with some other application (for example
`C:\Program Files\ServiceNow\...`), gem installs will fail with a permission
error. Put your own Ruby first on `PATH`:

```powershell
$env:Path = "C:\Ruby40-x64\bin;$env:Path"
```

TODOs before going live: real committee names/blurbs in `_data/committee.yml`,
and the registered address in `contact.html`.

This website was built by Andrew Logan with the assistance of AI. If it's somehow some years later and you're trying to figure out something I'm available at andrewrlogan2@gmail.com - feel free to reach out.

© Bassendean Community Children's Association. Site content is not licensed for reuse.
