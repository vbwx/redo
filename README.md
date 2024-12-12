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

    redo [--quiet] [--strict] [--follow] [--hidden] [--nocd]
         [--mindepth N | +N] [--maxdepth N | -N] [--depth N | --N]
         [--] [+INCLUDE_GLOB ...] [-EXCLUDE_GLOB ...]
         [+] [DIR ...] [-] [SCRIPT_OR_EXECUTABLE [ARG ...]]

### Environment Variables

You can use the following variables in the script supplied to `redo`.

- `DIR`
- `CWD` (unless `--nocd` is specified)
- `COUNT`
- `INDEX`
- `DEPTH`
- `RUNS`
- `FILES`
- `SUBDIRS`
- `LEAF`
- `ROOT`
- `RCOUNT`
- `RINDEX`

### Examples

```sh
redo echo \$CWD
redo --nocd echo \$DIR  # same result
redo echo \$PWD         # absolute paths
```

```sh
redo --hidden -.git echo \$INDEX
```

```sh
redo <<< 'echo "($DEPTH) $INDEX/$COUNT: $CWD"'
```

```sh
redo echo '"$CWD ($SUBDIRS directories, $FILES files)"'
```

```sh
redo --mindepth 2 --maxdepth 3 echo \$CWD
redo +2 -3 'echo $CWD'  # same result
```

```sh
redo --quiet SetFile -a E '*.*'    # executed in subdirectories recursively
redo --quiet . SetFile -a E '*.*'  # also executed in working directory
```
