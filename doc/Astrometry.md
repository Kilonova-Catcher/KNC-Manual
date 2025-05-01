## Astrometry: Pinpointing Where You Are in the Sky

After you've calibrated and stacked your images, the next step is to determine exactly where in the sky each pixel is pointing. This process is called astrometry.

### What Is Astrometry?

Astrometry is the science of measuring the positions of celestial objects. In imaging, it means determining the exact coordinates (RA/DEC) of the stars and sources in your image by comparing the star patterns in your image to a known astrometric catalog.

This solution is saved in the image’s FITS header as a World Coordinate System (WCS), which tells software how to convert pixel positions into sky coordinates.

### Why Is Astrometry Important?

Without astrometry, your image is just a photograph with no spatial reference. Once WCS is applied:

- Each pixel in the image is associated with accurate sky coordinates
- You can report source positions in RA and DEC
- Your data becomes interoperable with catalogs and scientific databases
- Transients can be verified, shared, and followed up by other observers

### Astrometry in Gravitational Wave Follow-Up

Astrometry is essential in optical follow-up of gravitational wave (GW) alerts:

- GW alerts cover large areas of sky (100s of square degrees)
- You need to report the exact sky location of any transient you find
- Astrometry enables comparison to known galaxies or historical images
- Most reporting platforms (e.g., TNS, SkyPortal) require astrometrically solved images

If your data lacks astrometry, it cannot be used for scientific confirmation.

### What Is Plate Solving?

Plate solving is the process used to perform astrometry. It matches the pattern of stars in your image to known catalogs, such as Gaia or UCAC4, and determines:

- The center of your image in sky coordinates
- The plate scale (arcseconds per pixel)
- The rotation angle of the image
- The WCS solution to map pixel (x, y) to (RA, DEC)

Solvers may be built into software like ASTAP or PRISM.

### How to Perform Astrometry

Most astrophotography software tools include or support plate solving. These include:

- ASTAP (built-in solver, offline support)
- Prism (astrometric calibration panel)
- Astrometry.net (free online solver)
- Siril, PixInsight, NINA (with plugins or modules)

Steps:
1. Open your calibrated, stacked FITS image in a supported tool
2. Run the astrometric solver
3. The software will detect stars, match them to a catalog, and compute a solution
4. The FITS file is updated with WCS metadata

### How to Know It Worked

After solving:
- You should be able to move your mouse over the image and see RA/DEC coordinates
- The FITS header will contain WCS keywords like `CRVAL1`, `CRVAL2`, `CD1_1`, etc.
- You can overlay star catalogs or extract coordinates of sources

### How to Use Astrometry.net (Online Plate Solver)

If you don’t have a local plate solver installed, or you want to double-check your solution, you can use the free online solver at [nova.astrometry.net](https://nova.astrometry.net/).

#### Step-by-Step Instructions

1. Visit: https://nova.astrometry.net/
2. Create an account (optional)
3. Upload your image (FITS recommended)
4. Submit and wait for the solution
5. Review the results and download the solved FITS file
6. Use the WCS-enabled file for analysis or submission

#### Notes

- Make sure your image contains stars
- Avoid uploading stretched or heavily edited files
- Raw calibrated stacks work best

### Troubleshooting: Why Didn’t My Plate Solve Work?

#### 1. Image Has No Stars or Very Few Stars
- Cause: Field is too empty or underexposed
- Fix: Stack more frames or increase exposure

#### 2. Image Was Over-Processed
- Cause: Stretching or editing alters pixel data
- Fix: Use unedited calibrated stacks or FITS files

#### 3. Noisy or Uncalibrated Image
- Cause: Hot pixels or gradients interfere with star detection
- Fix: Apply bias/dark/flat calibration before solving

#### 4. Incorrect Image Scale or Metadata
- Cause: Solver can't guess the field size
- Fix: Provide rough RA/DEC and image scale if known

#### 5. Obstructed or Distorted Star Field
- Cause: Clouds, bad tracking, or optical issues
- Fix: Use only well-tracked, clear images

#### 6. Upload Format Issue
- Cause: File is corrupted or unsupported
- Fix: Use FITS format; avoid editing files
  
---
## Related Tools and Websites

### Astrometry.net
https://nova.astrometry.net/  
Free online plate solver with automatic WCS injection.

### Gaia Archive
https://gea.esac.esa.int/archive/  
Official access to the Gaia astrometric catalog.

### ASTAP
https://www.hnsky.org/astap.htm  
Offline astrometry, calibration, and stacking software.

### Prism Software
https://www.prism-astro.com/  
Comprehensive observatory control and image processing suite.

### CDS VizieR Catalog Access
https://vizier.cds.unistra.fr/viz-bin/VizieR  
Explore and download catalogs used for plate solving.

