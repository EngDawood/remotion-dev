---
name: gif
description: Displaying GIFs, APNG, AVIF and WebP in Remotion
metadata:
  tags: gif, animation, images, animated, apng, avif, webp
---

```tsx
import { AnimatedImage, staticFile } from "remotion";

export const MyComposition = () => {
  return <AnimatedImage src={staticFile("animation.gif")} width={500} height={500} />;
};
```

Control fit, playbackRate, and loopBehavior via props.

## Getting GIF duration

```bash
npx remotion add @remotion/gif
```

```tsx
import { getGifDurationInSeconds } from "@remotion/gif";
const duration = await getGifDurationInSeconds(staticFile("animation.gif"));
```
