## Preprocessing: Cleaning Your Raw Images

When you take a raw image through your telescope, it might look beautiful at first glance — but beneath the surface are many invisible issues caused by your camera’s electronics, the telescope optics, or even dust on your sensor. These artifacts can affect the accuracy of your measurements or hide faint sources like kilonovae entirely.

This is where **preprocessing** comes in.

Preprocessing is the essential first step in cleaning up your images before doing any kind of analysis, like identifying a transient or measuring brightness. It allows us to remove unwanted noise and correct uneven lighting across the image so that what we’re seeing is actually from the sky — not the camera.

To do this, we use special calibration images: **bias**, **dark**, **flat**, and sometimes **flat-dark** frames.

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

### Flat Frames

**What they are**: Flat frames are images of a uniformly lit surface (like the twilight sky or a light panel). They show how light is unevenly recorded across your sensor due to dust, shadows, and lens imperfections.

**Why we take them**: To correct for:
- Vignetting (darkening toward the corners)
- Dust shadows (from particles on the sensor)
- Uneven pixel sensitivity

**How to take them**:
- Point at a uniformly lit source (e.g., a white panel, t-shirt over scope, or the sky during twilight).
- Take enough exposures so your camera’s histogram peaks at about 30–50% (e.g. ~33,000 ADU).
- Take 15–25 flat frames per filter.
- Settings: Same gain and temperature as lights. Exposure time is based on reaching a good brightness, not on matching the lights.

---

### Flat-Dark Frames

**What they are**: Flat-dark frames are like dark frames, but taken with the **same exposure time as your flats**, not your lights.

**Why we take them**: If your camera has **amp glow** or other noise that affects even short exposures, flat-darks help calibrate your flats more accurately than bias frames.

**How to take them**:
- Cover the telescope or use the shutter.
- Use the **same exposure time as your flat frames**.
- Take 15–25 frames per filter, same gain and temperature.

You can use **either bias frames** *or* **flat-darks** to calibrate your flat frames — but not both. If your camera has amp glow, flat-darks are preferred.
