# h2m: a matching workbench

A command-line workbench for the last part of byte-matching a function of the
[Halo 2 decompilation](https://github.com/kirklandsig/halo2-decompiled): the
source compiles, the score is small, and the question is which spelling makes
the compiler emit retail's bytes.

It scores whole-file variants of a source file against retail without touching
the tree, explains the difference (difference classes, register map, retail-only
and ours-only instructions), remembers every variant it has scored in a ledger,
finds matched functions that show a retail pattern, and can search source
rewrites on its own. Game (LTCG) functions are scored through a reduced image in
a private scratch root.

## Use

```sh
git clone https://github.com/andrewnakas/h2m-workbench
export H2M_ROOT=/path/to/halo2-decompiled      # your checkout, set up as its docs describe
python h2m-workbench/h2m.py diff 30ed40
python h2m-workbench/h2m.py score 30ed40 my_variant.cpp
```

Everything else is in [docs/H2M_WORKBENCH.md](docs/H2M_WORKBENCH.md): the
requirements, the environment variables, every command with an example, the
three numbers of the score vector, and the game-function backend.

## What this is not

- It contains no compiler, SDK header, library, game data or retail code. You
  need your own lawfully obtained toolchain and your own `default.xbe`, exactly
  as the decompilation repository requires.
- `tools/check.py` of the decompilation tree stays the judge of what matches;
  the workbench only helps find the form.
- It was built for one tree and one compiler (MSVC 7.1); expect rough edges.

## Licence

GPL-3.0, the licence of the tree whose tools it builds on. See `LICENSE`.
