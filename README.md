# Packages Dependency Graph

Generates a dependency graph suitable for Graphviz `dot` tool (`dotfile`) from a
Debian `Packages.gz` file. The generated graph uses `debtree`'s conventions:

- Build-Depends:           dark gold, bold
- Build-Depends-Indep:     light gold
- Pre-Depends:             purple, bold
- Depends:                 blue
- Recommends:              black
- Suggests:                black, dotted
- Conflicts:               red
- Provides:                green, inverted arrowhead

This tool is also able to generate a `dotfile` detailing `debtree`'s
conventions.

Based on Stefano Zacchiroli's `depgraph` script.

## How to install
One must `git clone` or download this repository, have a Python 3 interpreter
and install the dependencies as detailed below.

This project depends on the `python-debian` module and may use `python-apt`. As
`python-apt` is currently *very* outdated on PyPI, it is recommended to install
these dependencies using APT or a similar package management tool from your
distribution of choice.

For Debian based distributions (Ubuntu, Mint, etc) these are installed by:

```
apt install python3-debian python3-apt
```

## Usage
To write the dependency graph's `dotfile` on the *standard output*:

```
pdg g MyPackagesFile
```

A similar command will write the legend of the dependency graph on the
*standard output*:

```
pdg l MyPackagesFile
```

You may want to save the generated `dotfile` for generating the graph later. In
a POSIX shell you may simply use redirections:

```bash
pdg g MyPackagesFile > graph.dot
```

Generating the graph as an Encapsulated Postscript file (or any `dot` output
driver, if you please) as a one-liner:

```bash
pdg g MyPackagesFile | dot -Teps > my_graph.eps
```