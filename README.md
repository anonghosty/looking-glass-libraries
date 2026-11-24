# Looking Glass libraries

The Python library files (wheels) of [Looking Glass](https://github.com/anonghosty/looking-glass): one release here
for each Looking Glass release from v2026.11.21.3 on, with the same tag. That release was the first whose libraries are
locked by hash; older releases do not use this repository.

**The files are not in this repository's code: they are attached to its
[Releases](https://github.com/anonghosty/looking-glass-libraries/releases).** Each release carries:

- `looking-glass-libraries-<release>.tar.gz`: the wheels for Python 3.12, 3.13 and 3.14 on x86_64 and aarch64
  (Ubuntu 24.04 and later), for the platform, the database pipeline and the documentation site;
- `looking-glass-libraries-<release>.tar.gz.sha256`: that file's SHA-256.

Inside the archive: `platform/`, `database/` and `docs/` hold the wheels, `locks/` the lock files they were checked
against when the archive was made, and `SHA256SUMS` the SHA-256 of every wheel.

## How Looking Glass uses them

Looking Glass's installer and `deploy/update_libraries.sh` take each library from PyPI first, then from this
repository, then from the copy kept on the computer. **Every file, from every source, is checked against the
`requirements.lock` files of the Looking Glass release being installed** (exact version and SHA-256): a file that does
not match is refused. Only ready-built files (wheels) are used, never source packages. Nothing here is code to run on
its own.

## Checking an archive yourself

```bash
sha256sum -c looking-glass-libraries-<release>.tar.gz.sha256
mkdir libs && tar -xzf looking-glass-libraries-<release>.tar.gz -C libs
cd libs && sha256sum -c SHA256SUMS
```

The lock files themselves are in the main repository's release, under `platform/requirements.lock` and
`database/requirements.lock`.

## A computer without internet

Unpack the release's archive into `~/looking-glass/libraries/<release>/` and run the installer: the files are checked
against the lock in the same way. The full steps are in the installation guide, under
[Where the files come from](https://github.com/anonghosty/looking-glass/blob/main/docs/INSTALLATION.md#where-the-files-come-from).
