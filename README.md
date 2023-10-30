# Issue with installation of typesense-docsearch-css package

This repository reproduces an [issue with the installation of the `typesense-docsearch-css` package when using Pnpm cache](https://github.com/typesense/typesense-docsearch.js/issues/12).

## Context

The repository contains:

* A `package.json` file with a dependency on the `typesense-docsearch-css@0.4.0` package.
* A github workflow that installs the repository dependencies, with Pnpm cache enabled.

## Versions

* typesense-docsearch-css: 0.4.0
* Node.js: 18.x
* Pnpm: 8.6.0
* Workflow runner: `ubuntu-latest`

## Expected behavior

The installation of the NPM dependencies should succeed every time the workflow is run.

## Actual behavior

The first time the workflow is run, the installation of the dependencies succeeds. __The second time the workflow is run, [the installation of the `typesense-docsearch-css` package fails](https://github.com/javierbrea/typesense-docsearch-css-issue/actions/runs/6689006668/job/18171899929) with the following error__:

```txt
ERR_PNPM_UNEXPECTED_PKG_CONTENT_IN_STORE  Package name mismatch found while reading {"integrity":"sha512-hVTJC1Rg2BnNB4kl2Qi4GcgjFmPZY8YGu0aJ5V6iM6vK62yvtE7jObnAc1maYOp33NWFVLPgl/9PlBfWBlN0Dw==","registry":"https://registry.npmjs.org/","tarball":"https://registry.npmjs.org/typesense-docsearch-css/-/typesense-docsearch-css-0.4.0.tgz"} from the store. This means that the lockfile is broken. Expected package: typesense-docsearch-css@0.4.0. Actual package in the store by the given integrity: typesense-docsearch-css@0.3.0.
Error: Process completed with exit code 1.
```

## How to reproduce the issue

1. Fork this repository
2. Run the workflow
3. Run the workflow again

