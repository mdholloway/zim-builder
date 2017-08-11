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
--date [required if type is '5k' or '50k']: YYYY-MM date of interest, e.g., 2017-07
--novid [optional]: omits audio and video content, resulting in a much smaller ZIM file
--nopic [optional]: omits pictures in addition to audio and video, resulting in an even smaller ZIM file
```

Example usage: `$ ./build_zim --lang=en --type=core --novid`

The requested ZIM compilation will be created in the `out/` directory; some cached data will be in `cac/`.

## Update article lists

If you want to refresh any list or generate new top-viewed article lists for a new language or month/year, run the corresponding scripts in `scripts/`:

```
$ ./scripts/get_articles_med
$ ./scripts/get_articles_top_viewed --lang=en --date=2017-05
```

`get_articles_top_viewed` will generate both top 5k and top 50k variants for the language and date specified.

If you want to run `get_articles_med`, you will need likely need some dependencies:

`$ sudo apt-get install libxml-simple-perl libwww-perl libgetargs-long-perl` (for Debian Jessie)
