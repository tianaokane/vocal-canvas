# Vocal Canvas

Paint with your voice. Hum, sing, or whisper into your microphone while moving your hand in front of your webcam. The pitch of your voice becomes colour. Your volume becomes brush size. Your hand decides where the paint lands.

Every painting is a record of a sound you made.

[**Try it live →**](https://yourusername.github.io/vocal-canvas)

---

<!-- DEMO VIDEO -->
<!-- Replacing this with my video once recorded -->

---

## How to paint

| Input | Effect |
|---|---|
| 🎵 Voice pitch | Colour — low hum = violet, high note = red via cyan and green |
| 🔊 Volume | Brush size — whisper = fine line, loud = broad stroke |
| ✋ Hand position | Where the paint lands |
| ↕️ Hand height | Opacity — high hand = ethereal, low hand = vivid |
| ✊ Fist | Slowly dissolves the canvas back to black |

Wear headphones. The mic is always listening.

---

## The technical bit

Your microphone signal is analysed every frame using autocorrelation — an algorithm that finds the repeating period of a wave and converts it to a frequency in Hz. That frequency is mapped logarithmically to a hue value, because pitch perception is logarithmic: each octave doubles the Hz but feels like an equal step.

The brush is a comet trail — an array of recent hand positions drawn as a tapered line, thicker and brighter at the head, fading to nothing at the tail. Strokes are composited with additive blending, so overlapping colours build toward white in the most active areas and darker tones accumulate in the quieter passages.

Hand tracking runs via MediaPipe Hands at up to 60 frames per second, giving 21 landmark points per frame. The index fingertip is used as the brush position.

---

## Export

Hit **Export PNG** at any point to download the current painting as a full resolution image. The grid layer and paint layer are composited together — no UI chrome, just the painting.

---

## Built with

- [Web Audio API](https://developer.mozilla.org/en-US/docs/Web/API/Web_Audio_API) — microphone input, pitch detection via autocorrelation
- [MediaPipe Hands](https://developers.google.com/mediapipe/solutions/vision/hand_landmarker) — real-time hand landmark detection
- [HTML5 Canvas 2D](https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API) — layered rendering, additive compositing
- Vanilla JavaScript — no frameworks, no build step

---

## Run locally

```bash
git clone https://github.com/yourusername/vocal-canvas.git
cd vocal-canvas
open index.html
```

Microphone and camera access require browser permissions. Works best in Chrome.

---

*Part of [Body as Controller](https://yourusername.github.io) — a suite of browser instruments played with the human body.*
