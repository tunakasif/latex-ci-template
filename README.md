![Logo](./.github/logo.svg)

<p align="center">
  <a href="https://github.com/tunakasif/latex-ci-template/actions/workflows/release.yml"><img alt="Build status" src="https://github.com/tunakasif/latex-ci-template/actions/workflows/release.yml/badge.svg"/></a>
  <a href="https://github.com/tunakasif/latex-ci-template/blob/main/LICENSE"><img alt="GitHub license" src="https://img.shields.io/github/license/tunakasif/latex-ci-template"></a>
</p>

# LaTeX-CI Template

Template for writing CI enabled LaTeX documents. According to the version number provided with a [git-tag](https://git-scm.com/book/en/v2/Git-Basics-Tagging), state of the LaTeX project and its PDF output are saved as release assets.

## Usage

Make changes to the LaTeX documents, and provide [git-tags](https://git-scm.com/book/en/v2/Git-Basics-Tagging) to the commits where you see fit, with annotations regarding the version as in the form of `v*` (e.g. v1.0.2). A PDF file will automatically be generated from the tags. In the wake of PDF generation, it will be used as an additional asset for the automatic release based on the provided tag. This template is written in a self-evident manner, hence for demonstration, checkout the [Releases](https://github.com/tunakasif/latex-ci-template/releases) page.

## Dependencies for GitHub Actions

Automation of LaTeX project build and tag-based releases is achieved with [GitHub Actions](https://github.com/features/actions). The workflow configuration is achieved with [`release.yml`](./.github/workflows/release.yml) file. The workflow dependencies are listed as follows:

- [actions/checkout](https://github.com/actions/checkout)
- [xu-cheng/latex-action](https://github.com/xu-cheng/latex-action)
- [softprops/action-gh-release](https://github.com/softprops/action-gh-release)

## LaTeX Document Hierarchy

The sample LaTeX document hierarchy is in the form below. It is a minimal demonstration of multi-file LaTeX project with images and bibliography.

```stdout
.
└── src
    ├── images
    │   └── space.jpg
    ├── bibliography.bib
    ├── main.tex
    └── my_table.tex
```

As expected, building process depends on the document hierarchy. This template is designed for the base case provided in [xu-cheng/latex-action](https://github.com/xu-cheng/latex-action) such that we have a single `root_file: main.tex`, and we are compiling with default settings of [xu-cheng/latex-action](https://github.com/xu-cheng/latex-action). The provided hierarchy can be changed easily, however [`release.yml`](./.github/workflows/release.yml) needs to be changed, accordingly. Since [xu-cheng/latex-action](https://github.com/xu-cheng/latex-action) provides a rich documentation, this aspect should not be problematic.

Finally, the [softprops/action-gh-release](https://github.com/softprops/action-gh-release) action creates a release based on the provided tag, and adds the generated `main.pdf` from workspace directory to the assets of release. If a hierarchy change is on the table, then the release aspect of [`release.yml`](./.github/workflows/release.yml) needs to be altered, accordingly.
