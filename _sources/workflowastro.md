## The Astronomer's Workflow Diagram

This is the typical end-to-end pipeline for processing astronomical images in Kilonova Catcher.

```text
1. Raw Image Capture
   └─➤ Take multiple light frames of your target

         ↓

2. Calibration Frame Collection
   └─➤ Bias frames (readout noise)
   └─➤ Dark frames (thermal noise)
   └─➤ Flat frames (optical imperfections)

         ↓

3. Preprocessing
   └─➤ Subtract bias/dark
   └─➤ Divide by flat
   └─➤ Output: cleaned, calibrated images

         ↓

4. Stacking
   └─➤ Combine calibrated light frames
   └─➤ Improves signal-to-noise ratio (SNR)

         ↓

5. Astrometry
   └─➤ Plate solve image
   └─➤ Add sky coordinates (WCS) to FITS header

         ↓

6. Photometry or Visual Inspection
   └─➤ Measure brightness of sources
   └─➤ Submit candidate or upload to SkyPortal
