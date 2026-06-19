---
name: subtitles
description: subtitles and caption rules
metadata:
  tags: subtitles, captions, remotion, json
---

All captions must use the `Caption` type from `@remotion/captions`:

```ts
type Caption = {
  text: string;
  startMs: number;
  endMs: number;
  timestampMs: number | null;
  confidence: number | null;
};
```

- To **generate** captions: see [./transcribe-captions.md](./transcribe-captions.md)
- To **display** captions: see [./display-captions.md](./display-captions.md)
- To **import** from .srt: see [./import-srt-captions.md](./import-srt-captions.md)
