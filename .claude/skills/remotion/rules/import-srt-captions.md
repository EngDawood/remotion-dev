---
name: import-srt-captions
description: Importing .srt subtitle files into Remotion using @remotion/captions
metadata:
  tags: captions, subtitles, srt, import, parse
---

```bash
npx remotion add @remotion/captions
```

```tsx
import { parseSrt } from "@remotion/captions";

const response = await fetch(staticFile("subtitles.srt"));
const text = await response.text();
const { captions } = parseSrt({ input: text });
```

Once parsed, use with all `@remotion/captions` utilities.
