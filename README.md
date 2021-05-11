# percona-doc-docker

Docker images that include dependencies for building Sphinx- and MkDocs-based [Percona](https://www.percona.com/software/documentation/) documentation.

- `mkdocs`: An Ubuntu-based image for building MkDocs/Markdown documentation.
- `sphinx`: Based on the official [Sphinx](https://hub.docker.com/r/sphinxdoc/sphinx) `sphinxdoc/sphinx` image.
- `sphinx-latexpdf`: Based on the official [Sphinx](https://hub.docker.com/r/sphinxdoc/sphinx-latexpdf) `sphinxdoc/sphinx-latexpdf` image.

## Usage

### MkDocs projects

Perform a build (`mkdocs build`):

```sh
docker run --rm -v $(pwd):/docs perconalab/pmm-doc-md
```

Run the live preview local server (`mkdocs serve`):

```sh
docker run --rm -p 8000:8000 -v $(pwd):/docs perconalab/pmm-doc-md mkdocs serve -a 0.0.0.0:8000
```

Open your browser at <http://localhost:8000>

Create PDF:

```sh
docker run --rm -v $(pwd):/docs -e ENABLE_PDF_EXPORT=1 perconalab/pmm-doc-md mkdocs build -t material
```

([Read more](https://github.com/percona/pmm-doc/blob/main/README.md))

### Sphinx projects

For HTML:

```sh
docker run --rm -v $(pwd):/docs perconalab/percona-doc-sphinx make clean html
```

For PDF:

```sh
docker run --rm -v $(pwd):/docs perconalab/percona-doc-sphinx-latexpdf make latexpdf
```

Both assume a `./Makefile` and Sphinx source files in `./source`.

## Contents

MkDocs packages and plugins:

- [mkdocs](https://www.mkdocs.org/) - MkDocs itself.
- [mkdocs-macros-plugin](https://pypi.org/project/mkdocs-macros-plugin/) - Various useful macros.
- [mkdocs-exclude](https://pypi.org/project/mkdocs-exclude/) - For excluding files from MkDocs processing.
- [markdown-include](https://pypi.org/project/markdown-include/) - For including .md files in others.
- [mkdocs-material](https://pypi.org/project/mkdocs-material/) - Base theme.
- [mkdocs-with-pdf](https://pypi.org/project/mkdocs-with-pdf/) - Builds PDF.
- [plantuml-markdown](https://github.com/mikitex70/plantuml-markdown) - For [PlantUML](https://plantuml.com/) diagrams.
- [mkdocs-git-revision-date-plugin](https://github.com/zhaoterryy/mkdocs-git-revision-date-plugin) - For 'date last changed' page information.
- [mkdocs-material-extensions](https://pypi.org/project/mkdocs-material-extensions/) - For icons.
- [mkdocs-bootstrap-tables-plugin](https://github.com/byrnereese/mkdocs-bootstrap-tables-plugin) - Adds a bootstrap class to tables making them render better.
- [mkdocs-enumerate-headings-plugin](https://pypi.org/project/mkdocs-enumerate-headings-plugin/) For numbered headings.
- [mkdocs-section-index](https://github.com/oprypin/mkdocs-section-index) - Add links to section nodes.
- [mike](https://github.com/jimporter/mike) - Tool for building and managing versions.
- [lightgallery](https://github.com/g-provost/lightgallery-markdown) - For zooming images.

Additional Fonts:

- [Chivo](https://fonts.google.com/specimen/Chivo) - To match Percona.com website theme.

### Sphinx image

Sphinx extensions:

- [sphinx-copybutton](https://sphinx-copybutton.readthedocs.io/) Adds a copy button to code blocks.
- [sphinx-gitstamp](https://pypi.org/project/sphinx-gitstamp/) Git datestamp.
- [sphinx-tabs](https://pypi.org/project/sphinx-tabs/) Allows for tabbed content blocks.
- [sphinx_markdown_builder](https://pypi.org/project/sphinx-markdown-builder/) Writes Markdown files from rst sources.
- [sphinx_markdown_parser](https://pypi.org/project/sphinx-markdown-parser/) Allows for Markdown files in a Sphinx/rst project.
- [sphinxcontrib-srclinks](https://pypi.org/project/sphinxcontrib-srclinks/) Adds various page links (e.g. to Github) to navigation bar.
- [sphinx-reload](https://pypi.org/project/sphinx-reload/) Automatically rebuilds and serves a Sphinx project.
- [pymdown-extensions](https://facelessuser.github.io/pymdown-extensions/)
