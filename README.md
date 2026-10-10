# mv_screen_fog

Your camera becomes a steamed-up window. Draw in the fog with your finger, wipe it with your palm, and breathe it back.

**Live:** https://waffvil.github.io/mv_screen_fog/

## How to use

| Gesture | What it does |
| --- | --- |
| ☝️ Point one finger | Draw thin lines in the fog |
| ✋ Open palm | Wipe big patches |
| 😗 Make an O with your mouth | Blow fog back on, in front of your mouth |
| 😮 Open your mouth | Softer, wider breath |
| ✧ Upside-down M (3 fingers pointing down), hold | Toggle sigil mode |

Mouse and touch also work (hold Shift for a palm wipe).

Keys: `R` refog · `C` recalibrate mouth · `H` show tracking · `T` sigil mode · `S` save photo · `F` fullscreen · `U` hide UI · hold `Space` to breathe.

For the first ~2 seconds after your face appears, keep your mouth still. That's your neutral, and breath is measured against it.

## Run locally

The camera needs `https` or `localhost`:

```sh
python3 -m http.server 8765
# open http://localhost:8765
```

## How it works

- One `index.html`, no build step.
- Hand and face tracking: [MediaPipe Tasks Vision](https://ai.google.dev/edge/mediapipe/solutions/vision/hand_landmarker) (HandLandmarker + FaceLandmarker), running in the browser.
- Fog: a WebGL2 shader (blurred, lifted, droplet-textured view) driven by a fog-density mask that strokes erase and breath paints back.
- Nothing leaves your device.
