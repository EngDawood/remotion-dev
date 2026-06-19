---
name: fonts
description: Loading Google Fonts in Remotion
metadata:
  tags: fonts, google-fonts, typography, text
---

```bash
npx remotion add @remotion/google-fonts
```

```tsx
import { loadFont } from "@remotion/google-fonts/Roboto";

const { fontFamily } = loadFont("normal", {
  weights: ["400", "700"],
  subsets: ["latin"],
});

export const MyComposition = () => {
  return <div style={{ fontFamily }}>Hello World</div>;
};
```

Call `loadFont()` at the top level of your module, not inside a component.
