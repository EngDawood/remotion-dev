---
name: timing
description: Interpolation and timing in Remotion
metadata:
  tags: easing, bezier, interpolation, spring, timing
---

```ts
import { interpolate, Easing } from "remotion";

const opacity = interpolate(frame, [0, 60], [0, 1], {
  easing: Easing.bezier(0.16, 1, 0.3, 1),
  extrapolateLeft: "clamp",
  extrapolateRight: "clamp",
});
```

### Common curves

```ts
Easing.bezier(0.16, 1, 0.3, 1)    // Crisp UI entrance
Easing.bezier(0.45, 0, 0.55, 1)   // Editorial / slow fade
Easing.bezier(0.34, 1.56, 0.64, 1) // Playful overshoot
```

### Preset easings

```ts
Easing.inOut(Easing.cubic)
Easing.out(Easing.cubic)  // Use for enter animations
Easing.in(Easing.cubic)   // Use for exit animations
```

### Composing interpolations

Create a single normalized progress (0-1) and derive multiple properties from it to avoid duplicating timing logic.
