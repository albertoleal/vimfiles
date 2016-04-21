# The Vim Configuration. [![Build Status](https://travis-ci.org/luan/vimfiles.svg?branch=master)](https://travis-ci.org/luan/vimfiles)

If you're trying to use this config checkout this [cheat
sheet](https://github.com/luan/vimfiles/wiki/Luan's-Vim-Cheat-Sheet).

---

This vimfiles support both standard [vim](http://www.vim.org/) and
[neovim](https://neovim.io/), I'd encourage you to give neovim a try.

If you're using neovim follow [this
guid](https://github.com/neovim/neovim/wiki/Installing-Neovim) in order to get
it properly setup. The autocompletion plugin we use needs [python3
support](https://neovim.io/doc/user/nvim_python.html) too.

If you're using regular vim make sure to install it with lua support, on ubuntu
that's provided with the `vim-nox` package and on OSX it can be installed with
Homebrew by doing `brew install vim --with-lua`.

### Table of Contents

1. [Using This Configuration](#using-this-configuration)
1. [Installation](#installation)
  1. [Additional Dependencies](#additional-dependencies)
    1. [ctags](#ctags)
1. [Customizing](#customizing)
  1. [Changing Configuration](#changing-configuration)
  1. [Adding Plugins](#adding-plugins)
1. [Screenshots](#screenshots)

## Using This Configuration

This configuration is supposed to be used directly, **not** forked. If you intend
to keep up to date with changes made to this repo it's recommended that you
just clone this repository and customize the config using the [provided
hooks](#customizing). If you have a feature or fix to submit, feel free to fork
and send a PR.

---

## Installation

As simple as:
```bash
curl vimfiles.luan.sh/install | bash

# To override you current config:
# curl vimfiles.luan.sh/install | FORCE=1 bash
```

### Additional Dependencies

Most of the dependencies are installed automatically, assuming you have a
minimal development environment for you language. For example we download all
the tools for golang and elm automatically.  `git` is assumed to be installed
and so is `ag` or `ack`, if either of those is not, some plugins may not behave
as expected.

#### ctags

`ctags` is used to jump to function definitions, it is not strictly necessary if
you don't need that functionality, if you want to be able to jump effectively
to definitions install the correct version of ctags.

**OSX**

```bash
brew uninstall ctags
brew tap universal-ctags/universal-ctags
brew install universal-ctags --HEAD
```

**Linux**

*exuberant-ctags* from your OS is generally enough for most things, but if you
want more CSS, ruby and other goodnesses you will need to manually compile and
replace your ctags installation with: https://github.com/fishman/ctags

---

## Customizing

We load 3 extra configuration files that are **NOT** part of this repo:

* `~/.vimrc.local.before` (*to open: `,vb`*): Configuration to be set before everything else, this
  runs before any plugin or any config from this repository.
* `~/.vimrc.local` (*to open: `,vl`*): Configuration to be set after everything else, this runs
  after all other configuration is loaded and all plugins are setup.
* `~/.vimrc.local.plugins` (*to open: `,vp`*): Extra plugins to be loaded (along with maybe
  optional configuration for them). Is loaded after all the default plugins are
  installed.

A common pattern is for individuals or teams to have those 3 files checked in
to a separate [dotfiles](https://github.com/luan/dotfiles) repository and have
them be symlinked into your `$HOME` directory. Symlink them before you run the
install script and everything should work.

### Changing Configuration

You might want to change some config such as disabling autocompletion or
enabling auto save, or maybe just changing your colorscheme.  You can do so by
editing the `~/.vimrc.local` file, for example:

Changing colorscheme:
```vim
colorscheme gruvbox
```

Enabling auto save:
```vim
" will save automatically when leaving the buffer
" 0 or 1, defaults 0
let g:autosave = 1
```

Disabling neocomplete:
```vim
let g:neocomplete#enable_at_startup = 0   " disable neocomplete
let g:neocomplcache_enable_at_startup = 0 " disable the fallback version when no LUA
```

Some configuration values need to be set before loading plugins, for that we
have the `~/.vimrc.local.before`, that get's loaded before everything else, one
example usage of it is enabling fancy characters for the airline plugin:
```vim
let g:airline_powerline_fonts = 1
```

### Adding Plugins

If you have a favorite plugin you want to install but couldn't convince me to
add it as a default you can still have it be installed by just putting it in
the `~/.vimrc.local.plugins`, like such:
```vim
" Plugin to navigate between camelCase words
Plug 'bkad/CamelCaseMotion'
```

---

## Screenshots

**Default colorscheme: hybrid**

[![hybrid](https://github.com/luan/vimfiles/raw/master/screenshots/hybrid.png)](https://github.com/luan/vimfiles/raw/master/screenshots/hybrid.png)

**Alternate colorscheme: monokai**

[![monokai](https://github.com/luan/vimfiles/raw/master/screenshots/monokai.png)](https://github.com/luan/vimfiles/raw/master/screenshots/monokai.png)

