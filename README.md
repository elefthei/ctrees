# Choice Trees
[![Docker CI](https://github.com/vellvm/ctrees/workflows/Docker%20CI/badge.svg?branch=dev)](https://github.com/vellvm/ctrees/actions?query=workflow:"Docker%20CI")
[![Nix](https://github.com/vellvm/ctrees/actions/workflows/nix-build.yml/badge.svg)](https://github.com/vellvm/ctrees/actions/workflows/nix-build.yml)

We develop a cousin of Interaction Trees, dubbed _Choice Trees_, with native support for non-determinism.

## Meta

- Author(s):
  - Nicolas Chappe
  - Paul He
  - Ludovic Henrio
  - Eleftherios Ioannidis
  - Yannick Zakowski
  - Steve Zdancewic
- License: MIT License
- Compatible Rocq versions: 9.2
- Additional dependencies:
  - dune
  - [Extlib](https://github.com/coq-community/coq-ext-lib)
  - [InteractionTrees](https://github.com/DeepSpec/InteractionTrees)
  - [Equations](https://github.com/mattam82/Coq-Equations)
  - [Coinduction](https://github.com/damien-pous/coinduction)
  - [RelationAlgebra](https://github.com/damien-pous/relation-algebra)
- Rocq namespace: `CTree`

## Related papers

- https://hal.science/hal-05154458
- https://dl.acm.org/doi/10.1145/3571254 (old)

## Building instructions

### Obtaining the project

```sh
git clone https://github.com/vellvm/ctrees
cd ctrees
```

### Installing dependencies and building

From the checkout:

```sh
opam repository add rocq-released https://rocq-prover.org/opam/released --switch default
opam install --switch default --working-dir --deps-only .
opam exec --switch default -- dune build
```

Skip the repository-addition command if `rocq-released` is already configured.
The official `rocq-coinduction.1.22` release provides `Coinduction.all` and the
tower API used by CTree.

## Universe checking

Universe checking remains enabled throughout the library. The former
inconsistency came from monomorphic universe instances that identified event
and branch indices with the higher universes needed by nested choice trees,
state transformers, and interpreters. These declarations now keep their
universe levels independent and polymorphic.


