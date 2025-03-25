## Stacking 
When you’re capturing something faint — like a kilonova at the edge of detectability — a single image often isn’t enough. It might be noisy, unclear, or even completely blank at first glance.

That’s where **stacking** comes in.

Stacking is the process of **combining multiple exposures** of the same target to create a single image with **less noise and more signal**.

---

### Signal vs. Noise

Let’s break it down:

- The **signal** in your image — the light from stars, galaxies, or a kilonova — is real. It stays in the same place in every frame.
- The **noise** — from your camera, electronics, or atmosphere — is random. It’s different in every frame.

When you stack images:
- The signal **adds up** (gets stronger)
- The noise **averages out** (gets weaker)

This improves the **Signal-to-Noise Ratio (SNR)**, making faint objects stand out from the background.

---

### Benefits of Stacking

- Makes faint transients (like kilonovae) visible  
- Reveals dim details in galaxies, supernova remnants, or jets  
- Reduces graininess (random noise)  
- Increases photometric accuracy (brightness measurements)  
- Helps confirm if a candidate source is real or just noise

With just one frame, a kilonova might look like random static. But after stacking 5, 10, or 20 frames, it may become unmistakable — a real source that wasn't obvious before.

---

### How Many Frames Should I Stack?

There’s no magic number, but here are general guidelines:

| Goal                         | Number of Frames  |
|------------------------------|-------------------|
| Bright target photometry     | 3–5               |
| Faint transient detection     | 10–30             |
| Deep-sky imaging             | 30–100+           |

The more you stack, the better your result — as long as your tracking is solid and the frames are well-aligned.

---

### Tools for Stacking

Most amateur-friendly tools support stacking automatically:
- **ASTAP**: Fast, automatic star alignment and stacking
- **Prism**: Scripted stacking during preprocessing
- **Siril**: Powerful stacking and preprocessing workflow
- **DeepSkyStacker**: Easy visual interface for stacking

Each has options for **median**, **average**, or **sigma-clipping** stacking, depending on your goals and number of frames.

---

**More frames = more signal = better science.**

Stacking is a key part of transforming raw, noisy exposures into meaningful data!
