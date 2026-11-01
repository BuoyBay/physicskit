---
title: "physicskit typed API"
summary: "Source-derived public signatures, properties, parameters, defaults, and return values."
category: "Reference"
order: 21
types: ["PhysicsBox", "PhysicsCircle", "PhysicsWorld"]
dependencies: []
symbols: ["PhysicsBox", "PhysicsCircle", "PhysicsWorld"]
related: ["api.md", "getting-started.md", "index.md"]
---

# physicskit typed API

Generated from the package source declarations. Platform guards are shown where present; inherited members are documented on the base type. See the [API contracts](api.md) for behavior and limitations.

## PhysicsCircle

`Public Class PhysicsCircle`

A circle with immutable shape/material and explicitly mutable position/velocity.

### Properties

| Name | Type | Read-Only | Shared | Default | Description |
| --- | --- | --- | --- | --- | --- |
| `X` | `Double` | Yes | No | — | — |
| `Y` | `Double` | Yes | No | — | — |
| `VelocityX` | `Double` | Yes | No | — | — |
| `VelocityY` | `Double` | Yes | No | — | — |
| `Radius` | `Double` | Yes | No | — | — |
| `Mass` | `Double` | Yes | No | — | — |
| `Restitution` | `Double` | Yes | No | — | — |
| `InverseMass` | `Double` | Yes | No | — | — |

### Constructor

`Public Sub Constructor(x As Double, y As Double, radius As Double, mass As Double = 1.0, restitution As Double = 1.0)`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `x` | `Double` | `ByVal` | Required |
| `y` | `Double` | `ByVal` | Required |
| `radius` | `Double` | `ByVal` | Required |
| `mass` | `Double` | `ByVal` | `1.0` |
| `restitution` | `Double` | `ByVal` | `1.0` |

Returns: no value.

### SetPosition

`Public Sub SetPosition(x As Double, y As Double)`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `x` | `Double` | `ByVal` | Required |
| `y` | `Double` | `ByVal` | Required |

Returns: no value.

### SetVelocity

`Public Sub SetVelocity(x As Double, y As Double)`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `x` | `Double` | `ByVal` | Required |
| `y` | `Double` | `ByVal` | Required |

Returns: no value.

## PhysicsBox

`Public Class PhysicsBox`

Immovable axis-aligned rectangle.

### Properties

| Name | Type | Read-Only | Shared | Default | Description |
| --- | --- | --- | --- | --- | --- |
| `Left` | `Double` | Yes | No | — | — |
| `Top` | `Double` | Yes | No | — | — |
| `Right` | `Double` | Yes | No | — | — |
| `Bottom` | `Double` | Yes | No | — | — |
| `Restitution` | `Double` | Yes | No | — | — |

### Constructor

`Public Sub Constructor(left As Double, top As Double, right As Double, bottom As Double, restitution As Double = 1.0)`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `left` | `Double` | `ByVal` | Required |
| `top` | `Double` | `ByVal` | Required |
| `right` | `Double` | `ByVal` | Required |
| `bottom` | `Double` | `ByVal` | Required |
| `restitution` | `Double` | `ByVal` | `1.0` |

Returns: no value.

## PhysicsWorld

`Public Class PhysicsWorld`

Fixed-step, insertion-ordered solver. One Step is staged and committed atomically.

### Properties

| Name | Type | Read-Only | Shared | Default | Description |
| --- | --- | --- | --- | --- | --- |
| `FixedDelta` | `Double` | Yes | No | — | — |
| `CircleCount` | `Integer` | Yes | No | — | — |
| `BoxCount` | `Integer` | Yes | No | — | — |

### Constructor

`Public Sub Constructor(delta As Double = 0.01666666666666667, iterations As Integer = 4)`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `delta` | `Double` | `ByVal` | `0.01666666666666667` |
| `iterations` | `Integer` | `ByVal` | `4` |

Returns: no value.

### SetGravity

`Public Sub SetGravity(x As Double, y As Double)`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `x` | `Double` | `ByVal` | Required |
| `y` | `Double` | `ByVal` | Required |

Returns: no value.

### AddCircle

`Public Sub AddCircle(circle As PhysicsCircle)`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `circle` | `PhysicsCircle` | `ByVal` | Required |

Returns: no value.

### AddBox

`Public Sub AddBox(box As PhysicsBox)`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `box` | `PhysicsBox` | `ByVal` | Required |

Returns: no value.

### Clear

`Public Sub Clear()`

No parameters.

Returns: no value.

### Step

`Public Sub Step()`

No parameters.

Returns: no value.
