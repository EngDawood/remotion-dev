---
name: silence-detection
description: Adaptive silence detection for video/audio files using FFmpeg
metadata:
  tags: silence, detection, trimming, ffmpeg, loudnorm, audio
---

## Step 1: Measure loudness

```bash
npx remotion ffmpeg -i public/video.mov -map 0:a -af loudnorm=print_format=json -f null /dev/null
```

Note the `input_thresh` value from the output.

## Step 2: Detect silences

```bash
npx remotion ffmpeg -i public/video.mov -map 0:a -af "silencedetect=noise=${THRESH}dB:d=0.5" -f null /dev/null
```

## Apply trim in Remotion

```tsx
<Video
  src={staticFile("video.mov")}
  trimBefore={Math.floor(leadingEnd * fps)}
  trimAfter={Math.ceil(trailingStart * fps)}
/>
```
