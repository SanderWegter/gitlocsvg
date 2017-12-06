# gitlocsvg

git repository "lines of code" evolution graph as vector graphic
(SVG).

This is a rewrite and extension
of [git-loc](https://github.com/ITikhonov/git-loc). Some concepts were
reused, but the code is written from scratch.

Features in common with the original project:

* create a graph of the "lines of code" evolution of a git repository
  as vector graphic (SVG)
* show adds, deletes and the total number of "lines of code"
* options file to configure the output per repository or in the users
  home directory
* mouseover tooltips with additional information

Changes with respect to the original project:

* always create SVG as output, no textual representation or list
* use the commit time stamps on the x-axis, not just one commit per
  tick
* axis labels, automatic scaling to represent the selected time range
* configurable time range
* configurable colors
* merge commits into time slices to maintain readability for many
  commits on a small time scale
* option to exclude files from being counted based on file name
  instead of a commit message regex

## Usage

```
./gitlocsvg /path/to/repository > graph.svg
```

## Example

See `example.svg` / `example.htm` in this repository or via rawgit:
* (https://rawgit.com/crokkon/gitlocsvg/master/example.svg)
* (https://rawgit.com/crokkon/gitlocsvg/master/example.htm)

## Configuration

Configuration is done via `.gitlocsvgrc` file, either in the user home
directory or in the repository root directory.
Example:
```
[plotrange]
# number of weeks back from now to print. unset or "0" gives the full history
weeks: 12

[colors]
# define colors as "rgb(R, G, B)" with R, G, B between 0 and 255
adds: rgb(0,255,0)
dels: rgb(0, 0, 255)
locline: rgb(255, 0, 0)
axis: rgb(0, 0, 0)
grid: rgb(199, 200, 200)

[exclude]
# exclude files in the repository by regex. multiple lines are allowed here.
# Following lines must be indented.
files: ^img/
       ^doc/
       .pyc$
```
