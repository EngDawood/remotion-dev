---
name: sequencing
description: Sequencing patterns for Remotion - delay, trim, limit duration of items
metadata:
  tags: sequence, series, timing, delay, trim
---

Use `<Sequence>` to delay when an element appears in the timeline.

```tsx
<AbsoluteFill>
  <Sequence><Background /></Sequence>
  <Sequence from={fps} durationInFrames={2 * fps} layout="none"><Title /></Sequence>
  <Sequence from={2 * fps} durationInFrames={2 * fps} layout="none"><Subtitle /></Sequence>
</AbsoluteFill>
```

## Premounting

Always premount any `<Sequence>`:

```tsx
<Sequence premountFor={fps}><Title /></Sequence>
```

## Series

Use `<Series>` when elements should play one after another:

```tsx
<Series>
  <Series.Sequence durationInFrames={45}><Intro /></Series.Sequence>
  <Series.Sequence durationInFrames={60}><MainContent /></Series.Sequence>
  <Series.Sequence durationInFrames={30}><Outro /></Series.Sequence>
</Series>
```

Inside a Sequence, `useCurrentFrame()` returns the local frame (starting from 0).
