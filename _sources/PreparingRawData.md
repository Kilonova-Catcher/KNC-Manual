## Preparing Your Raw Data

Before you dive into preprocessing and stacking your images, it’s important to make sure your files are cleanly organized and contain the right metadata. This saves time, avoids mistakes, and helps ensure your data can be properly calibrated and analyzed — by you or by others.

---

### File Naming Conventions

Give your files clear, consistent names that describe what they are. This makes it much easier to group them into categories and ensures automated tools can correctly process them.

A good file name typically includes:
- **Target name** (e.g., M31, KN240101)
- **Filter used** (e.g., g, r, i)
- **Exposure time** (e.g., 60s)
- **Frame type** (light, dark, flat, bias) or **Stack** 
- **Date** or **session ID**
- **Your Name**

**Example file name:** GRB250317B_Freeberg_T180_2025-03-18T04-36-51_Sloan_r_Stack_40x180sec.fits

Many stacking tools (like ASTAP or Prism) can sort files automatically if your naming system is consistent.

---

### FITS Files and The Importance of Metadata

When working in astronomy, you'll hear a lot about **FITS files** — and almost all your images from the telescope will be saved in this format.

**FITS** stands for **Flexible Image Transport System**, and it’s the standard file format used in astronomy around the world.

FITS files are designed for **data**, not aesthetics.

Unlike JPGs or PNGs, which are meant to look nice on a screen, FITS files are meant to **store scientific information**. Every pixel value in a FITS file corresponds to actual light (photon counts) collected by your camera's sensor.

This data is essential for preprocessing, especially when you're:
- Measuring brightness (photometry)
- Solving for astrometry (needs RA/DEC, pixel scale, orientation)
- Detecting faint transients like kilonovae
- Sharing data across different software and observatories
- Matching lights with darks (based on exposure time, temperature, gain)
- Calibrating flats (based on filter)

A FITS file contains two main parts:

1. **Image Data**  
   - The actual image as a 2D array of numbers (not colors!)
   - Each number corresponds to the light intensity at each pixel

2. **Header**  
   - A block of metadata stored as text
   - Describes how the image was taken and how it should be interpreted

Key metadata often includes:
- `EXPTIME` – Exposure time
- `FILTER` – Filter name
- `DATE-OBS` – Date/time of observation
- `CCD-TEMP` – Sensor temperature
- `OBJECT` – Target name
- `GAIN` or `ISO` – Camera gain or ISO setting
- `BINNING` – Binning mode (e.g., 1x1 or 2x2)

**Tip**: Most software tools will read this metadata automatically. If it's missing or incorrect, plate solving, stacking, or calibration may fail — so it’s a good habit to double-check your FITS headers using a viewer like:
- **Siril**
- **FITS Liberator**
- **AstroImageJ**
- **ASTAP**
- **Prism**

---

| Feature            | FITS                   | JPG / PNG             |
|--------------------|------------------------|------------------------|
| Purpose            | Scientific data        | Display / viewing      |
| Pixel values       | Real light intensities | Compressed RGB values  |
| Metadata           | Extensive header        | Minimal or none        |
| Editable?          | Yes (non-destructive)  | Lossy (data discarded) |
| Used in astronomy? | Yes                 | Not for science      |


**We always expect FITS files to be delivered.**
