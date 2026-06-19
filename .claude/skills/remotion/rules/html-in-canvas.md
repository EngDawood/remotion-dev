# Using `<HtmlInCanvas>` in Remotion

Renders children into a `<canvas>` so you can post-process them with the Canvas 2D API or WebGL.

Only works in Chrome 149+ with the `chrome://flags/#canvas-draw-element` flag enabled.

## Basic usage

```tsx
import { HtmlInCanvas } from "remotion";

export const MyComp = () => {
  return (
    <HtmlInCanvas width={1280} height={720}>
      <div style={{ fontSize: 80 }}>Hello</div>
    </HtmlInCanvas>
  );
};
```

## 2D effect with `onPaint`

```tsx
const onPaint: HtmlInCanvasOnPaint = useCallback(({ canvas, element, elementImage }) => {
  const ctx = canvas.getContext("2d");
  if (!ctx) throw new Error("Failed to acquire 2D context");
  ctx.reset();
  ctx.filter = `blur(4px)`;
  const transform = ctx.drawElementImage(elementImage, 0, 0);
  element.style.transform = transform.toString();
}, []);
```

Do not nest `<HtmlInCanvas>` inside another `<HtmlInCanvas>`.
