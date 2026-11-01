---
title: "physicskit API contracts"
summary: "Usage and behavioral contracts for physicskit."
category: "Reference"
symbols: ["PhysicsCircle", "PhysicsBox", "PhysicsWorld"]
related: ["index.md", "getting-started.md", "typed-api.md"]
---

# PhysicsKit 0.1.0

Pure Buoy fixed-step circle simulation with circle/circle impulses and immovable
axis-aligned box contacts. `Import physicskit` works from the sealed package.
There are no native dependencies or coupling to SpriteKit. A caller can use each
circle's position to update a sprite independently of rendering.

## API

- `PhysicsCircle(x, y, radius, mass = 1, restitution = 1)` has immutable radius,
  mass and restitution. Mass zero is immovable. Read `X`, `Y`, `VelocityX`,
  `VelocityY`, `Radius`, `Mass`, `InverseMass`, and `Restitution`.
- `circle.SetPosition(x, y)` and `SetVelocity(x, y)` validate both arguments
  before changing state. Static circles accept only zero velocity.
- `PhysicsBox(left, top, right, bottom, restitution = 1)` is an immutable,
  immovable AABB with getters for those five values.
- `PhysicsWorld(delta = 1/60, iterations = 4)` owns ordered arrays of references.
  Use `AddCircle`, `AddBox`, `SetGravity`, `Step`, `Clear`, `CircleCount`,
  `BoxCount`, and `FixedDelta`. Adding the same circle twice to one world rejects.

Each `Step()` advances exactly the fixed delta with semi-implicit Euler
(`velocity += gravity * delta`, then `position += velocity * delta`). The caller
schedules steps; there is no elapsed-time accumulator or implicit catch-up.
Contacts are resolved by circle insertion order, then box insertion order,
repeated for the configured number of iterations. The contact coefficient is
`Min(materialA.Restitution, materialB.Restitution)`. Separating contacts receive
position correction but no bounce impulse.

Circle overlap is corrected in proportion to inverse mass. Coincident circle
centers choose the positive X normal. A circle inside a box exits via the nearest
face; ties select left, top, right, bottom in that order. Box corners use the
actual circle-to-closest-point normal, rather than expanding the box to a square.

A step runs on private staged circle copies, then commits only after every
integration and contact operation succeeds. A numerical/range error leaves all
original circle positions and velocities unchanged. The world retains strong
references until `Clear` or destruction. Callers retain access to their circles;
there is no concurrent mutation support, and sharing a circle across active
worlds should be avoided. Deterministic order means repeatability for an
identical sequence on one platform, not bit-identical floating-point results
across architectures.

## Bounds

Positions and box edges: `-1e9..1e9`. Velocities and gravity: `-1e6..1e6`.
Radius: `1e-6..1e6`. Dynamic mass: `1e-6..1e6`; zero is static. Restitution:
`0..1`. Step delta: `1e-6..0.1` seconds. Iterations: `1..8`. One world contains
at most 256 circles and 64 boxes. NaN and infinities reject. Box dimensions must
be positive. Bounds also apply to staged results; a valid input near an extreme
may produce an out-of-range step, which throws atomically.

The solver does all circle pairs and all circle/box pairs per iteration. It
allocates staged copies per step. It is deliberately bounded, with no spatial
broad phase or performance claim for large scenes.

## Limits

This is a small discrete translational solver, not full ImpulseEngine parity.
There is no continuous collision detection: fast/small bodies can tunnel through
objects. Use suitable speed/radius/delta combinations. There are no rotations,
angular momentum, friction, polygon bodies, joints, sleeping, forces, collision
callbacks or contact persistence. Iterative multi-contact resolution is
order-dependent and does not guarantee an exact stacked equilibrium. Opposing or
overlapping static boxes can leave unresolved penetration. Static/static contacts
are ignored. Restitution tests establish isolated impacts; simultaneous contacts
can differ from a full constraint solver.

## Verification


Maintainers run the private validation suite before release. See the repository README for public build instructions.

