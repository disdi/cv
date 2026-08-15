# CV.template


Single-source CV generator: `profile.yml` is rendered through Jinja2 templates in `templates/` to produce Markdown, HTML, and PDF outputs. There is no application code — only data, templates, and a Makefile that drives `jinja2-cli` and `pandoc`. Originally a fork of [rybakit/cv.template](https://github.com/rybakit/cv.template).

## Common commands

```bash
make cv         # generate all three formats into output/
make cv-md      # markdown only
make cv-html    # html only
make cv-pdf     # pdf only (requires xelatex + pandoc)
make clean      # wipe output/
```

`CV_FILENAME` (default `cv`) controls the output basename, e.g. `make cv CV_FILENAME=Saket_Sinha_CV`.

Runtime dependencies (must be on PATH): `jinja2` (from `jinja2-cli[yaml]` — YAML is an optional extra), `jinja2_markdown`, `pandoc`, `xelatex` (texlive-xetex + recommended/extra font packages).

```bash
pipx install 'jinja2-cli[yaml]'
pipx inject jinja2-cli jinja2_markdown
# or: pip install -r requirements.txt
```

The CI workflow `.github/workflows/ci.yml` documents the exact apt + pip install line.

There are no tests, linters, or build steps beyond rendering — verification is "did `make cv` succeed and does the PDF look right".