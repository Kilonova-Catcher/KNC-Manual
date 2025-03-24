## Preprocessing: Cleaning Your Raw Images

When you take a series of images through your telescope — whether you're capturing a galaxy or chasing a kilonova — you're not just collecting light from your target. You're also picking up unwanted signals from caused by your camera’s electronics, the telescope optics, the environment or even dust on your sensor. These artifacts can affect the accuracy of your measurements or hide faint sources like kilonovae entirely.

This is where **preprocessing** comes in.

Preprocessing is the essential first step in cleaning up your images before doing any kind of analysis, like identifying a transient or measuring brightness. It allows us to remove unwanted noise and correct uneven lighting across the image so that what we’re seeing is actually from the sky — not the camera.

To do this, we use special calibration images: **bias**, **dark**, **flat**, and sometimes **flat-dark** frames.

That’s why we capture **calibration frames** (bias, dark, flat, and sometimes flat-darks): to measure those unwanted signals separately so we can subtract them out from the actual data.

But here's the catch: calibration only works if it's applied **correctly** — which means matching each light image with the *right* dark, flat, and bias frames. And that’s why **sorting and labeling** are so important, as referenced in "Preparing Raw Data".

---

### Why Do We Use Calibration Frames?

Every camera introduces some amount of error into your data. Whether it's thermal noise, pixel sensitivity differences, or shadows caused by dust, these effects can build up and distort your final stacked image.

Calibration frames help correct for:
- **Electronic noise**
- **Thermal noise (from heat in your camera sensor)**
- **Shadows and vignetting**
- **Uneven sensor response across the field**

The idea is simple: take images of *known nothingness*, *known uniform light*, or *matched exposure noise*, and then use them to subtract or divide out imperfections from your actual science frames.

---

### Bias Frames

**What they are**: Bias frames are the shortest possible exposure your camera can take, with the shutter closed or lens cap on. These capture the small electronic offset (or "readout noise") introduced by the camera whenever it reads data from the sensor.

**Why we take them**: To measure the base-level noise of the sensor — so we can subtract it from every other frame (including flats and darks).

**How to take them**:
- Use your camera’s shortest exposure time (often less than 0.01s).
- Keep the lens cap or telescope cover on.
- Take 50–100 bias frames to combine into a **master bias frame**.
- Settings (gain, temperature) should match your light frames.

---

### Dark Frames

**What they are**: Dark frames are taken with the same exposure time, gain, and temperature as your science (light) images — but with the shutter closed or lens cap on. These capture **thermal noise** and **hot pixels**.

**Why we take them**: To subtract temperature-dependent noise and hot pixels from your light images.

**How to take them**:
- Same camera settings as your lights: exposure time, gain, temperature.
- Keep the telescope or camera covered.
- Take 15–25 dark frames to combine into a **master dark frame**.
- Be careful: darks must match your lights *exactly* — no scaling is done in most amateur software like ASTAP.
---
### Subtraction Workflow: Applying Bias and Dark Frames

Once you’ve collected your calibration frames and created your **master bias** and **master dark** frames, the next step is to apply them to your raw images.

This is a part of pre-processing and it corrects your science (light) frames by removing unwanted electronic and thermal noise.

Let’s say you’re working with a set of raw light frames. Here’s what the subtraction workflow looks like:

```text
1. Light Frame (raw)
      └─➤ Contains: signal + bias + dark current + noise

2. Subtract Master Bias
      ➤ Removes the constant electronic offset

3. Subtract Master Dark
      ➤ Removes temperature-dependent thermal noise and hot pixels

4. Output: Calibrated Light Frame
      └─➤ Contains only the true sky signal (plus some random noise)
```
So, basically: 

Corrected Image = Raw Light - Master Dark - (Master Bias if needed)

---

### Flat Frames

**What they are**: Flat frames are images of a uniformly lit surface (like the twilight sky or a light panel). They show how light is unevenly recorded across your sensor due to dust, shadows, and lens imperfections.

**Why we take them**: To correct for:
- Vignetting (darkening toward the corners)
- Dust shadows (from particles on the sensor)
- Uneven pixel sensitivity

These aren’t real astronomical features — they’re artifacts caused by the optical path (filters, lenses, dust, sensor variations). To correct for this, we use **flat field frames**.

**How to take them**:
- Point at a uniformly lit source (e.g., a white panel, t-shirt over scope, or the sky during twilight).
- Use the **same filter** and optical setup as your light frames
- Keep the **exposure short**, but bright enough to reach ~30–50% of the camera’s full range (around 20,000–35,000 ADU)
- Take **15–25 frames per filter**
- Settings: Same gain and temperature as lights. Exposure time is based on reaching a good brightness, not on matching the lights.

**Pro tip:** If your setup doesn’t change, you can reuse the same flats for multiple nights.

### Creating the Master Flat

Once you have your flat frames:
1. Load all the flats (per filter) into your preprocessing software
2. **Subtract the master bias or flat-darks** if needed
3. Combine them (using median or average) to make a **master flat**

This master flat is a 2D map of how your system distorts even light.

To apply flat correction you are basically, **dividing** each calibrated light frame (bias- and dark-subtracted) by the master flat: Corrected Image = (Light - Dark) / Flat

---

# Be Consistent
Your master flat should match your lights in:
- Filter (g, r, i, etc.)

- Binning (e.g., 1x1)

- Optical configuration (no focus shifts!)

- Camera gain and temperature (ideally)

If anything changes — refocus, change filters, rotate the camera — you’ll need a new flat.

---

### Flat-Dark Frames

**What they are**: Flat-dark frames are like dark frames, but taken with the **same exposure time as your flats**, not your lights.

**Why we take them**: If your camera has **amp glow** or other noise that affects even short exposures, flat-darks help calibrate your flats more accurately than bias frames.

**How to take them**:
- Cover the telescope or use the shutter.
- Use the **same exposure time as your flat frames**.
- Take 15–25 frames per filter, same gain and temperature.

You can use **either bias frames** *or* **flat-darks** to calibrate your flat frames — but not both. If your camera has amp glow, flat-darks are preferred.

---

### Do We Stack Calibration Frames Too?

Yes — and it's a crucial part of the workflow.

Each type of calibration frame is usually taken **many times** per session:
- 15–25 darks
- 15–25 flats (per filter)
- 50–100 bias frames

Instead of using each one individually, we **combine (stack) them into "master frames"**:
- A **master bias**
- A **master dark** (for a specific exposure, gain, and temperature)
- A **master flat** (for each filter)
- Optionally, a **master flat-dark**

These master frames are then used to correct all your light images from the same session.

---

### Do I Do This Every Time?

Generally, yes — for each observing session or setup, you’ll need matching master frames. That means:
- If you change your **filter**, you need a new master flat
- If you change your **exposure time**, you need a new master dark
- If you change your **camera temperature**, you may need new darks and flats
- If your **optical setup changes** (rotator, camera orientation, etc.), you’ll want new flats

Some amateur astronomers build a **library** of master calibration frames for their setup — as long as the conditions match, those masters can be reused.

---
### Why Sorting Is Essential

If you give your files clear names and organize them by type, most software (like ASTAP, Prism, Siril, etc.) can:
- Automatically detect which frames are which (light, dark, flat, etc.)
- Match them by filter, exposure, and temperature
- Stack only the **correct** images together
- Apply the **right** calibration frames during preprocessing

Without this, the software might:
- Fail to calibrate at all
- Use the wrong calibration frames (causing bad corrections)
- Require you to sort everything manually
---

### Summary

Calibration only works when it's **accurate** — and accuracy comes from matching your light images with the right correction frames.

That’s why:
- We take multiple calibration frames and stack them into **master frames**
- We sort and label all files clearly
- We process each light image using the corresponding master dark, flat, and bias

This turns messy raw data into clean, calibrated images — ready to be stacked, analyzed, or submitted to Kilonova Catcher.

