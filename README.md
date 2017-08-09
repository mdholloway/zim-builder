# zim-builder

Tools for building ZIM files for use in the official Wikipedia apps.

Clone with `git clone --recursive` to pick up submodule(s).

Presumes a working [mwoffliner](https://github.com/openzim/mwoffliner) installation. See installation instructions there.

## Setup

Move or copy `config.example` to `config` and update with your email address and personal or organizational
name. The script will not run before performing this step.

## Usage

`build_zim` is a wrapper script around mwoffliner that takes the following options:

```
--lang [required]: the language code of the wiki from which to gather articles
--type [required]: the type of compilation to create. One of '5k', '50k', 'med', or 'core'
--novid [optional]: omits audio and video content, resulting in a much smaller ZIM file
--nopic [optional]: omits pictures in addition to audio and video, resulting in an even smaller ZIM file
```

Example usage: `$ ./build_zim --lang=en --type=core --nopic --novid`

The requested ZIM compilation will be created in the `/out` subdirectory of the file type subdirectory
(e.g., in `core/out/` given the above example).

