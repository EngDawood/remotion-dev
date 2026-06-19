---
name: videos
description: Embedding videos in Remotion - trimming, volume, speed, looping, pitch
metadata:
  tags: video, media, trim, volume, speed, loop, pitch
---

```bash
npx remotion add @remotion/media
```

```tsx
import { Video } from "@remotion/media";
import { staticFile } from "remotion";

export const MyComposition = () => {
  return <Video src={staticFile("video.mp4")} />;
};
```

## Trimming

```tsx
<Video src={staticFile("video.mp4")} trimBefore={2 * fps} trimAfter={10 * fps} />
```

## Volume / Speed / Loop / Pitch

```tsx
<Video src={staticFile("video.mp4")} volume={0.5} />
<Video src={staticFile("video.mp4")} playbackRate={2} />
<Video src={staticFile("video.mp4")} loop />
<Video src={staticFile("video.mp4")} toneFrequency={1.5} />
```

Pitch shifting only works during server-side rendering.
