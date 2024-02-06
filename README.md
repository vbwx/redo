![Shell](https://img.shields.io/github/languages/top/vbwx/redo?style=flat)
![MIT license](https://img.shields.io/github/license/vbwx/redo?style=flat)

# redo

Instead of doing something like `find . -type d -execdir ... \;` you can run `redo` with the command you want to have executed recursively in the subdirectories of the working directory.

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

    redo [--quiet] [--strict] [--follow] [--nocd]
         [--mindepth N] [--maxdepth N] [--depth N]
         [--] [+INCLUDE_GLOB ...] [-EXCLUDE_GLOB ...]
         [+] [DIR ...] [-] [SCRIPT_OR_EXECUTABLE [ARG ...]]

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

### Examples

```sh
redo echo \$CWD
redo --nocd echo \$DIR  # same result
redo echo \$PWD  # absolute paths
```

```sh
redo +.\* +\* -.git echo \$INDEX
```

```sh
redo <<< 'echo "($DEPTH) $INDEX/$COUNT: $CWD"'
```

```sh
redo --mindepth 2 --maxdepth 3 echo \$CWD
```

```sh
redo --quiet SetFile -a E '*.*'  # executed in subdirectories recursively
redo --quiet . SetFile -a E '*.*'  # also executed in working directory
```
