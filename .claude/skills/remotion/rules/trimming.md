---
name: trimming
description: Trimming patterns for Remotion - cut the beginning or end of animations
metadata:
  tags: sequence, trim, clip, cut, offset
---

## Trim the Beginning

A negative `from` value shifts time backwards:

```tsx
<Sequence from={-0.5 * fps}><MyAnimation /></Sequence>
```

Inside `<MyAnimation>`, `useCurrentFrame()` starts at 15 instead of 0.

## Trim the End

```tsx
<Sequence durationInFrames={1.5 * fps}><MyAnimation /></Sequence>
```

## Trim and Delay

```tsx
<Sequence from={30}>
  <Sequence from={-15}><MyAnimation /></Sequence>
</Sequence>
```
