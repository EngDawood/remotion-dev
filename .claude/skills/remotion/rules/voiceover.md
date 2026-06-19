---
name: voiceover
description: Adding AI-generated voiceover to Remotion compositions using TTS
metadata:
  tags: voiceover, audio, elevenlabs, tts, speech, calculateMetadata, dynamic duration
---

# Adding AI voiceover to a Remotion composition

Use ElevenLabs TTS to generate speech audio per scene, then use `calculateMetadata` to dynamically size the composition.

## Generating audio

```ts
const response = await fetch(`https://api.elevenlabs.io/v1/text-to-speech/${voiceId}`, {
  method: "POST",
  headers: { "xi-api-key": process.env.ELEVENLABS_API_KEY!, "Content-Type": "application/json", Accept: "audio/mpeg" },
  body: JSON.stringify({ text: "Welcome.", model_id: "eleven_multilingual_v2", voice_settings: { stability: 0.5, similarity_boost: 0.75 } }),
});
writeFileSync(`public/voiceover/scene.mp3`, Buffer.from(await response.arrayBuffer()));
```

## Dynamic duration via calculateMetadata

```tsx
export const calculateMetadata: CalculateMetadataFunction<Props> = async ({ props }) => {
  const durations = await Promise.all(SCENE_FILES.map((f) => getAudioDuration(staticFile(f))));
  return { durationInFrames: Math.ceil(durations.reduce((sum, d) => sum + d * 30, 0)) };
};
```
