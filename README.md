# SiriDB - Docs

This is the repository for the SiriDB documentation. It makes use of the Hugo Learn theme and Hugo.

## Prerequisites

- [Install Git](https://git-scm.com/downloads).
- [Install Go](https://golang.org/doc/install).
- [Install Hugo](https://gohugo.io/getting-started/installing/). Depending on the system, this might require Scoop, Choclatey, or other software.

## Usage

To start the website run the following commands:

**Development**:

```bash
hugo server -D # This command starts the Hugo server and watches the site directory for changes.
```

**Production**:

```bash
hugo # This command generates the static website in the public/ directory. If you do not have a site, then it gives errors about missing layout files.
```
