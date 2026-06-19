---
name: measuring-text
description: Measuring text dimensions, fitting text to containers, and checking overflow
metadata:
  tags: measure, text, layout, dimensions, fitText, fillTextBox
---

```bash
npx remotion add @remotion/layout-utils
```

```tsx
import { measureText, fitText, fillTextBox } from "@remotion/layout-utils";

// Measure
const { width, height } = measureText({ text: "Hello", fontFamily: "Arial", fontSize: 32, fontWeight: "bold" });

// Fit to width
const { fontSize } = fitText({ text: "Hello", withinWidth: 600, fontFamily: "Inter", fontWeight: "bold" });
```

Only call measurement functions after fonts are loaded. Use `validateFontIsLoaded: true` to catch issues early.
