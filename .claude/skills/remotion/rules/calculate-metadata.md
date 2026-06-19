---
name: calculate-metadata
description: Dynamically set composition duration, dimensions, and props
metadata:
  tags: calculateMetadata, duration, dimensions, props, dynamic
---

# Using calculateMetadata

Use `calculateMetadata` on a `<Composition>` to dynamically set duration, dimensions, and transform props before rendering.

```tsx
const calculateMetadata: CalculateMetadataFunction<Props> = async ({ props, abortSignal }) => {
  const data = await fetch(props.dataUrl, { signal: abortSignal }).then(r => r.json());

  return {
    durationInFrames: Math.ceil(data.duration * 30),
    props: { ...props, fetchedData: data },
  };
};
```

## Return value

All fields are optional:
- `durationInFrames`, `width`, `height`, `fps`
- `props`: Transformed props
- `defaultOutName`: Default output filename
- `defaultCodec`: Default codec for rendering
