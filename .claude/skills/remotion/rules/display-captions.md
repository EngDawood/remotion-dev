---
name: display-captions
description: Displaying captions in Remotion with TikTok-style pages and word highlighting
metadata:
  tags: captions, subtitles, display, tiktok, highlight
---

# Displaying captions in Remotion

```bash
npx remotion add @remotion/captions
```

## Creating pages

```tsx
const { pages } = useMemo(() => {
  return createTikTokStyleCaptions({
    captions,
    combineTokensWithinMilliseconds: 1200,
  });
}, [captions]);
```

## Word highlighting

```tsx
const CaptionPage: React.FC<{ page: TikTokPage }> = ({ page }) => {
  const frame = useCurrentFrame();
  const { fps } = useVideoConfig();
  const absoluteTimeMs = page.startMs + (frame / fps) * 1000;

  return (
    <AbsoluteFill style={{ justifyContent: "center", alignItems: "center" }}>
      <div style={{ fontSize: 80, fontWeight: "bold", whiteSpace: "pre" }}>
        {page.tokens.map((token) => {
          const isActive = token.fromMs <= absoluteTimeMs && token.toMs > absoluteTimeMs;
          return <span key={token.fromMs} style={{ color: isActive ? "#39E508" : "white" }}>{token.text}</span>;
        })}
      </div>
    </AbsoluteFill>
  );
};
```
