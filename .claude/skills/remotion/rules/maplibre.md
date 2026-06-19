---
name: maps
description: Make deterministic Remotion map animations with MapLibre GL JS and Turf.
metadata:
  tags: map, map animation, maplibre, turf, geojson, route animation
---

Use MapLibre GL JS for rendering maps. Use Turf for geospatial operations.

## Core rules

- Disable non-deterministic behavior: `interactive: false`, `fadeDuration: 0`.
- Use `delayRender()` / `continueRender()` around map loading and per-frame updates.
- Do not add `mapInstance.remove()` cleanup — it interferes with Remotion's render lifecycle.
- Coordinates are `[longitude, latitude]`.

## Prerequisites

```bash
npm i maplibre-gl @turf/turf
```

```ts
import 'maplibre-gl/dist/maplibre-gl.css';
```

## Basic map

```tsx
const mapInstance = new maplibregl.Map({
  container: containerRef.current,
  style: 'https://demotiles.maplibre.org/style.json',
  center: [8.5417, 47.3769],
  zoom: 7,
  interactive: false,
  fadeDuration: 0,
  canvasContextAttributes: { preserveDrawingBuffer: true },
});

mapInstance.on('load', () => {
  mapInstance.jumpTo({ center: [8.5417, 47.3769], zoom: 7 });
  mapInstance.once('idle', () => continueRender(loadingHandle));
});
```

For animated routes use Turf `greatCircle()`, `lineSliceAlong()`, and `along()`. Use `map.calculateCameraOptionsFromTo()` for camera movement.

## Rendering

```bash
bunx remotion render [composition-id] out/video.mp4 --gl=angle --concurrency=1
```
