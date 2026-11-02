# Simulate fixed-step circle and static-box collisions

Fixed-step circle simulation with circle/circle impulses and immovable
axis-aligned box contacts. `Import physicskit` works from the sealed package.
There are no native dependencies or coupling to SpriteKit. A caller can use each
circle's position to update a sprite independently of rendering.

## Install

From a Buoy consumer project with BPM installed:

```sh
bpm add physicskit --git https://github.com/BuoyBay/physicskit.git --rev refs/heads/main
```

BPM records the resolved commit in its lockfile. Keep that lockfile with the
consumer project for reproducible installs.

## API at a glance

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

## Build from source

With the native `build-packages` driver from [devtools](https://github.com/BuoyBay/devtools)
on your `PATH`, run from this checkout:

```sh
build-packages --root "$PWD" --compile-consumer physicskit
```

The driver checks source targets and compiles an import consumer. See the
[API guide](docs/API.md) for behavior, limits and any host prerequisites.

## Local Buoy setup

On your own machine, install Buoy and run:

```sh
buoy ai init --both
```

## Contributing

[Contributing](CONTRIBUTING.md) · [License](LICENSE)
