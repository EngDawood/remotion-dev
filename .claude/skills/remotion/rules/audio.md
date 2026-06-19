---
name: audio
description: Using audio and sound in Remotion - importing, trimming, volume, speed, pitch
metadata:
  tags: audio, media, trim, volume, speed, loop, pitch, mute, sound, sfx
---

# Using audio in Remotion

```bash
npx remotion add @remotion/media
```

```tsx
import { Audio } from "@remotion/media";
import { staticFile } from "remotion";

export const MyComposition = () => {
  return <Audio src={staticFile("audio.mp3")} />;
};
```

## Trimming

```tsx
<Audio src={staticFile("audio.mp3")} trimBefore={2 * fps} trimAfter={10 * fps} />
```

## Delaying

```tsx
<Sequence from={1 * fps}>
  <Audio src={staticFile("audio.mp3")} />
</Sequence>
```

## Volume

```tsx
<Audio src={staticFile("audio.mp3")} volume={0.5} />
// Dynamic:
<Audio src={staticFile("audio.mp3")} volume={(f) => interpolate(f, [0, fps], [0, 1], { extrapolateRight: "clamp" })} />
```

## Speed / Loop / Pitch

```tsx
<Audio src={staticFile("audio.mp3")} playbackRate={2} />
<Audio src={staticFile("audio.mp3")} loop />
<Audio src={staticFile("audio.mp3")} toneFrequency={1.5} />
```

Pitch shifting only works during server-side rendering.
