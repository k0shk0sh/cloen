# cloen

`git clone` wrapper. Clones a repository, cds into it, and opens it in `$EDITOR`|`$GUI_EDITOR`.

Set GITHUB_USERNAME environment variable in your .bashrc, .zshrc or equivalent.
Example, `export GITHUB_USERNAME="username"`

![](https://i.imgur.com/1EPYZF2.gif)

## Install

### npm

`npm i cloen -g`

### Manual

Take `bin/cloen` binary and put it somewhere that's in your `$PATH`.

## Synopsis

`$ cloen [options] <repo-url|username/repo-name|own-repo-name>`

## Options

#### -n

Don't use full name. Default is on. Normally, repositories clone into their
repository name with `<author>--<repo-name>` format. Like `$ cloen kutsan/dotfiles`
clones into `kutsan--dotfiles` directory. If this option specified, it clones into
`dotfiles` folder without dashes.

#### -o

Open editor, after clone finished. Default is off. If $GUI_EDITOR or $EDITOR globally
specified, then repository will open in it, as \$GUI_EDITOR primacy. Otherwise, `vim`
will be used as default.

#### -e <editor>

Open with selected editor, after clone finished. No need extra `-o` flag. Note that,
editor executable must be under your \$PATH and it must accept directory with its
first argument.

#### -h --help

Show help screen.

## Examples

    $ cloen <repo-name>
      .. git clone git@github.com:<GITHUB_USERNAME>/<repo-name>.git <repo-name>
      .. cd <username>--<repo-name>

    $ cloen -o <username>/<repo-name>
      .. git clone git@github.com:<username>/<repo-name>.git <repo-name>
      .. cd <username>--<repo-name>
      .. \$EDITOR .

    $ cloen git@github.com:<username>/<repo-name>.git (or HTTP(S) link)
      .. git clone git@github.com:<username>/<repo-name>.git <repo-name>
      .. cd <username>--<repo-name>

    $ cloen -ne emacs <username>/<repo-name>
      .. git clone git@github.com:<username>/<repo-name>.git <username>--<repo-name>
      .. cd <repo-name>
      .. emacs .
