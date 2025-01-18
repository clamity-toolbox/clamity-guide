# clamity-guide

Clamity User's Guide

The deployed User's Guide hosted on Github Pages is
[here](https://clamity-guide.clamity.com/).

## Sandbox Setup

1. Make sure you have python version 3 in your search path.

   ```
   python3 --version
   ```

1. Install and setup your sandbox. This will leave you in an activated python
   shell for your newly created python virtual environment. Change to your
   preferred source directory and cut & paste the following commands:

   ```
   git clone git@github.com:clamity-toolbox/clamity-guide
   cd clamity-guide
   python3 -m venv venv
   source venv/bin/activate
   pip install mkdocs-material
   mkdocs build
   mkdocs serve
   ```

1. Go to http://localhost:8000/ in your browser.

1. When you exit `mkdocs serve` (break), and want to to leave your python
   activated shell, run:

   ```
   deactivate
   ```

1. To restart the server from a non-activated shell, run:
   ```
   source venv/bin/activate
   mkdocs serve
   ```

## Generated Documentation

Some of the documentation, the command man pages for instance, are generated.
From the root of the repo, run:

```
./bin/update-docs
```

## CI/CD

This [CI Github Actions workflow](.github/workflows/ci.yml) invoked on changes
to the `main` branch runs the **mkdocs** command to generate the static site,
committing it to the `gh_pages` branch. Github Pages, in turn, is configured to
deploy that branch to https://user-guide.clamity.com. It usually takes anywhere
from a few to 5 minutes for changes to post.

## Notes

### Early Setup

1. mkdocs new .

### References

- [Tutorial - YT](https://www.youtube.com/watch?v=Q-YA_dA8C20&t=740s)
- [Another tutorial - YT](https://www.youtube.com/watch?v=xlABhbnNrfI&t=45s)
