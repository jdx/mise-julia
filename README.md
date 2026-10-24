# mise-julia

A [Julia](https://julialang.org) plugin for [mise](https://mise.jdx.dev), using the
asdf plugin interface. Forked from [rkyleg/asdf-julia](https://github.com/rkyleg/asdf-julia).

## Install

```bash
mise plugins install julia https://github.com/jdx/mise-julia.git
```

## Usage

```bash
mise ls-remote julia          # list all versions (plus `nightly`)
mise use -g julia@latest      # install and activate the latest stable release
mise use julia@1.10           # pin a version for the current project
mise install julia@nightly    # install the latest nightly build
```

Note that `mise` resolves `julia` through its registry, which may point at a
different backend. To force this plugin, use `asdf:julia@<version>`.

## How it works

- `bin/list-all` reads the official release index at
  <https://julialang-s3.julialang.org/bin/versions.json>, so it needs no
  GitHub API token and is not rate limited.
- `bin/install` downloads the official `.tar.gz` binary for your OS and
  architecture from `julialang-s3.julialang.org` (or the nightlies bucket) and
  unpacks it into the mise install directory. This includes macOS. On Apple Silicon,
  native `aarch64` builds are used from 1.7.0-beta3 onwards, and older versions
  fall back to the `x64` build (Rosetta). Very old macOS releases (0.x) that
  were only published as `.dmg` images get mounted, and `julia` is copied out of
  the app bundle.

### Acknowledgments
- [rkyleg](https://github.com/rkyleg) (original asdf-julia)
- [lasspe](https://github.com/lassepe)
- [hickey](https://github.com/hickey)
- [misnyo-ci](https://github.com/misnyo-ci)
- [sheeldotme](https://github.com/sheeldotme)
- [kimriouxparadis](https://github.com/kimriouxparadis)
- [dhanak](https://github.com/dhanak)
- [christopher-dG](https://github.com/christopher-dG)
- [spellcard199](https://github.com/spellcard199)
- [DimitarVanguelov](https://github.com/DimitarVanguelov)
- [razvanazamfirei](https://github.com/razvanazamfirei)
- [mehalter](https://github.com/mehalter)
- [DilumAluthge](https://github.com/DilumAluthge)
