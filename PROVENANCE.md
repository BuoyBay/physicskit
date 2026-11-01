# Provenance

This package is an independent implementation written for Buoy. It uses elementary
circle distance, closest-point AABB contact geometry and normal impulses; no
upstream implementation, artwork or binary is copied.

The user's supplied Xojo catalog listed
[ImpulseEngine](https://github.com/gkjpettet/ImpulseEngine), and the earlier
[repository survey](../../examples/xojo-open-source/catalog/README.md) identified
2D collision/impulse integration as useful alongside the sprite examples. That
survey found no license file in its inspected checkout and documented missing
joints upstream. This package neither grants an upstream license nor claims its
API or scene compatibility. Source inspections and pinned metadata belong to the
catalog inventory; this package was designed from the selected mathematical
subset and tested against independent analytic outcomes.

The local Buoy reference and existing compiler-checked packages established the
language/API syntax. Real compiler verification is performed by
`tests/impact_physics_verify.py`; source appearance alone is not validation.
