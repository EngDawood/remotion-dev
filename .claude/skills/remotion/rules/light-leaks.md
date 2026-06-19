---
name: light-leaks
description: Light leak overlay effects for Remotion using @remotion/light-leaks.
metadata:
  tags: light-leaks, overlays, effects, transitions
---

```bash
npx remotion add @remotion/light-leaks
```

```tsx
import { TransitionSeries } from "@remotion/transitions";
import { LightLeak } from "@remotion/light-leaks";

<TransitionSeries>
  <TransitionSeries.Sequence durationInFrames={60}><SceneA /></TransitionSeries.Sequence>
  <TransitionSeries.Overlay durationInFrames={30}><LightLeak /></TransitionSeries.Overlay>
  <TransitionSeries.Sequence durationInFrames={60}><SceneB /></TransitionSeries.Sequence>
</TransitionSeries>;
```

Props: `seed?` (pattern shape), `hueShift?` (0-360, default 0 = yellow-orange).
