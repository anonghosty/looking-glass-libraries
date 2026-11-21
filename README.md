# Looking Glass libraries

The Python library files (wheels) of each [Looking Glass](https://github.com/anonghosty/looking-glass) release, for
Ubuntu 24.04 and later (Python 3.12, 3.13, 3.14; x86_64 and aarch64). Each release here carries
`looking-glass-libraries-<version>.tar.gz` with `SHA256SUMS`.

The installers use these files only when PyPI cannot give a matching file, and check every file against the
`requirements.lock` files in the main repository before installing it: a file that does not match is refused,
whichever source it came from. Nothing here is code to run on its own.
