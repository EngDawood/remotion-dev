---
name: parameters
description: Make a video parametrizable by adding a Zod schema
metadata:
  tags: parameters, zod, schema
---

Install `zod` with the project's package manager, then define a schema:

```tsx
import { z } from "zod";

export const MyCompositionSchema = z.object({
  title: z.string(),
});

const MyComponent: React.FC<z.infer<typeof MyCompositionSchema>> = (props) => (
  <div><h1>{props.title}</h1></div>
);
```

```tsx
<Composition
  id="MyComposition"
  component={MyComponent}
  durationInFrames={100}
  fps={30}
  width={1080}
  height={1080}
  defaultProps={{ title: "Hello World" }}
  schema={MyCompositionSchema}
/>
```

## Color picker

```bash
npx remotion add @remotion/zod-types
```

```tsx
import { zColor } from "@remotion/zod-types";
export const MyCompositionSchema = z.object({ color: zColor() });
```
