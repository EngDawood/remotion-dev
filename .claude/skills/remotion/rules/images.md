## Sizing and positioning

```tsx
<Img src={staticFile("photo.png")} style={{ width: 500, height: 300, objectFit: "cover" }} />
```

## Dynamic image paths

```tsx
const frame = useCurrentFrame();
<Img src={staticFile(`frames/frame${frame}.png`)} />
```

## Getting image dimensions

```tsx
import { getImageDimensions, staticFile } from "remotion";
const { width, height } = await getImageDimensions(staticFile("photo.png"));
```
