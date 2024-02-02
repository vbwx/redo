![Shell](https://img.shields.io/github/languages/top/vbwx/redo?style=flat)
![MIT license](https://img.shields.io/github/license/vbwx/redo?style=flat)

# redo

Instead of doing something like `find . -type d -execdir ... \;` you can run `redo` and simply enter the commands you want to have executed in the subdirectories of the working directory recursively.

## Installation

### Installation via Homebrew

If [Homebrew](https://brew.sh) is installed, you can run this command:

```sh
brew install vbwx/utils/redo
```

### Manual Installation

1. Download and extract the [latest release](https://github.com/vbwx/redo/releases/latest) of redo.
2. If desired, move the completion script(s) to the appropriate location on your system.
   - Move `completion/redo` to a directory like `/etc/bash_completion.d`.
   - Move `completion/_redo` to a directory like `/usr/share/zsh/site-functions`.
3. Move `redo` to a directory such as `/usr/bin`.

## Usage

Run `redo --help` to get a quick overview of how to use this utility.

### Synopsis

    redo [--quiet] [--strict] [--follow] [--nocd] [--arg VAR]
         [--mindepth N] [--maxdepth N] [--depth N]
         [--] [+INCLUDE_GLOB ...] [-EXCLUDE_GLOB ...]
         [DIR ...] [SCRIPT_OR_EXECUTABLE ...]

### Environment Variables

You can use the following variables in the script supplied to `redo`.
Alternatively, you can pass one of these variables (or any environment variable) to the specified script/executable/command as an argument.

- `DIR`
- `CWD`
- `COUNT`
- `INDEX`
- `DEPTH`
- `RUNS`
- `ROOT`
- `RCOUNT`
- `RINDEX`
