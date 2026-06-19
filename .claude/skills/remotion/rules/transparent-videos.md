---
name: transparent-videos
description: Rendering transparent videos in Remotion
metadata:
  tags: transparent, alpha, codec, vp9, prores, webm
---

## ProRes (for video editing software)

```bash
npx remotion render --image-format=png --pixel-format=yuva444p10le --codec=prores --prores-profile=4444 MyComp out.mov
```

## WebM / VP9 (for browser playback)

```bash
npx remotion render --image-format=png --pixel-format=yuva420p --codec=vp9 MyComp out.webm
```
