# Provenance

This package is an independent implementation written for Buoy. It uses elementary
circle distance, closest-point AABB contact geometry and normal impulses; no
upstream implementation, artwork or binary is copied.

The package was inspired by the 2D collision and impulse problem space of
[ImpulseEngine](https://github.com/gkjpettet/ImpulseEngine). It implements its
own mathematical subset and does not claim upstream API or scene compatibility
or grant a license to upstream material.

The local Buoy reference and existing compiler-checked packages established the
language/API syntax. Compiler checking and native execution remain necessary when changing these contracts.
