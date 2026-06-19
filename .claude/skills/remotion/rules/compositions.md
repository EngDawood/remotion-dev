---
name: compositions
description: Defining compositions, stills, folders, default props and dynamic metadata
metadata:
  tags: composition, still, folder, props, metadata
---

A `<Composition>` defines the component, width, height, fps and duration of a renderable video.

## Default Props

```tsx
<Composition
  id="MyComposition"
  component={MyComposition}
  durationInFrames={100}
  fps={30}
  width={1080}
  height={1080}
  defaultProps={{ title: "Hello World", color: "#ff0000" } satisfies MyCompositionProps}
/>
```

Use `type` declarations for props rather than `interface` to ensure `defaultProps` type safety.

## Folders

```tsx
<Folder name="Marketing">
  <Composition id="Promo" />
  <Composition id="Ad" />
</Folder>
```

## Stills

```tsx
<Still id="Thumbnail" component={Thumbnail} width={1280} height={720} />
```

## Nesting compositions

```tsx
<AbsoluteFill>
  <Sequence width={COMPOSITION_WIDTH} height={COMPOSITION_HEIGHT}>
    <CompositionComponent />
  </Sequence>
</AbsoluteFill>
```
