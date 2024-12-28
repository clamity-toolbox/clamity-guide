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
   source directory and cut & paste the following commands:

   ```
   git clone git@github.com:clamity-toolbox/clamity-guide
   cd clamity-guide
   python3 -m venv venv
   source venv/bin/activate
   pip install mkdocs-material
   mkdocs build
   ```

1. Start a local server. The server will watch your repo and update it
   dynmically as you edit.

   ```
   mkdocs serve
   ```

1. Go to http://localhost:8000/ in your browser.

1. To leave your python activated shell, run:
   ```
   deactivate
   ```
   To restart the server, run:
   ```
   source venv/bin/activate
   mkdocs serve
   ```

## Notes

### Early Setup

1. mkdocs new .

### References

- [Tutorial - YT](https://www.youtube.com/watch?v=Q-YA_dA8C20&t=740s)
- [Another tutorial - YT](https://www.youtube.com/watch?v=xlABhbnNrfI&t=45s)
