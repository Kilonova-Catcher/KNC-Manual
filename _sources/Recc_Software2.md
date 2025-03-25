##  Reccomended Software by KNC Members: Image Calibration,Stacking and Photometry with ASTAP (Michael Freeberg's Workflow)

### ASTAP
- ASTAP is a free image calibration, stacking , astrometry, and photometry tool for deep sky images. The program can be downloaded at the following [url.](https://www.hnsky.org/astap.html)

**Here are some features of ASTAP:**
- In works with astronomical images in the FITS format, but can import RAW DSLR images or XISF, PGM, PPM, TIF, PNG and JPG images. It has a powerful FITS viewer and the native astrometric solver can be used by CCDCiel, NINA, 
APT, Voyager or SGP imaging programs to synchronize the mount based on an image taken,
- Available for MS-Windows 32 & 64 bit, Linux 32, 64 bit, MacOS 64 bit, Raspberry-Pi Linux 32 and 64 bit.
- Stacking of astronomical images including dark and flat frames. Stacking accomplished using a internal star match routine and internal astrometric solver along with background equalizing.
- Blink tab. It is important to examine your images before calibration and stacking. This will allow you to reject images that may have poor tracking, clouds, or other issues with the image that may affect the calibration and stacking of the image.
- Photometry Tab. It will allow you to do image photometry for the following filters.
  - V or G or TG (Johnson-V or Bayer filter green)
  - B (Johnson-B)
  - RC (Cousin-red)
  - SI (Sloan i')
  - SR (Sloan r')
  - SG (Sloan g’)
  - Can use either an internal star database for Johnson V or Johnson B, or it can use an online Gaia database to give V,B.R,SG,SR, and SI using the Gaia transformation coefficient formulas using the Gaia color band BP, RP and G
- It also has a robust fits viewer that can provide deep sky and star annotation, photometry and CCD inspector.
  - You can edit the fits header
  - You can export the fits file to JPEG, PNG, TIFF along with several other formats.
- I primarily use ASTAP for the calibration , stacking , astrometric and photometry functions. However is also has several other functions that may be useful in your particular observation plan.
  - It has pixel math functions
  - Live stacking of Images
  - Mount analysis, such as polar alignment error,
  - CCD Inspector for measuring image curvature.

### ASTAP Database Selection

- In order for ASTAP to perform the astrometry and photometry of your images you need to install several databases. I would recommend the following.
  - D80 very large star database. You can select one of the smaller databases that may be more suitable for your FOV.
  - V50-Photometry and colour star database
  - If you want you can also install the Large Galaxy and Variable star database.
- I have ASTAP installed on both a MAC and Windows system. I have found it to perform very well on image calibration and stacking and photometry. It also is very fast at plate solving an image.
- Documentation for the software is available also on the download page and also using the Help menu in the software. There are also many video’s on You Tube that go over different aspects of ASTAP
- I will go over what is necessary to calibrate, stack , and performing photometry of your image in ASTAP along with a demonstration.

### Calibration Frames
- Bias Frames- Bias frames essentially capture the inherent electronic noise of your camera sensor. Bias frames are taken at the shortest exposure time possible for your camera with the shutter closed or lens cap on scope. Bias frames can be one method to calibrate your flat frames. It is recommended to take 50-100 bias frames which will then be combined to produce a master bias. They should be taken at the same settings as your light frames(temp, gain) as your lights except exposure time
- Flat Dark- This is a dark frame that is taken at the same exposure time as your respective flat. camera, if you want to use flat darks to calibrate your flats , you will need flat darks for each filter to match the exposure time of the respective flat. If you have a sensor for example with amp glow , it is best to use flat darks, however if you have a camera, camera, you can use bias frames or flat darks. I personally prefer to use flat darks. I usually take 15-25 flat darks to combine to make the Master Flat dark for the respective flat. They should be taken at the same settings as your light frames(temp, gain) as your lights except exposure time with the shutter closed or lens cap on scope.
- Dark Frames-Dark frames are taken at the same exposure time as your lights and at the same camera settings as your light frames. If you have a mechanical shutter on your camera, you then take the dark frames with the shutter closed. If you have a camera that has a rolling or global shutter you will have to make sure that you take the dark frames with your lens cap on or scope covered so no stray light affects your dark frames. Dark frames capture the thermal noise for your sensor and also the hot pixels. The longer the exposure the more thermal noise in your image. I usually take 15-25 darks that then get combined to form the Master Dark. ASTAP does not allow for dark frame scaling, you therefore need to take a dark frame that matches the exposure time of the light frame.
- Flat Frames-Flat frames are used to correct for imperfections in the camera optical system. They help remove dust motes, vignetting and light fall-off in the optical system. There are different methods of taking flat frames. Some take sky flats, or you can use a light panel. You need to take flat frames for each filter. You also want to target about 33000 ADU for each flat frame. I use a light panel and Voyager to take my flat frames. Voyager will automatically adjust the exposure time to target 33000 ADU for each flat frame. Flat frames usually have a short exposure time, less than 30 sec. I take 15-25 flats per each filter which are then combined for the Master flat for that respective filter. These are also taken at the same settings(gain , temp) but expose time is determined to target 33000 ADU.
- Science Frames- These are the light frames that you take of your target. For photometry you need to take as many as required to get a good SNR of your target. This will depend on the brightness of your target, the light gathering ability of your scope, the sensitivity of your camera, and which filters are being used. For bright targets you may only need a couple of images with short exposure times but if you are trying to reach 20-21 mag levels you may need a total of a hour of integration time or longer. For most of the targets for KNC , I will take several images and then stack them into a Master Light Frame which is then used for photometry.
- Here are a couple of good videos by Adam Block on You Tube that provides a good discussion of bias, dark flats, darks, flats , and your light frames. These videos were based around Pixinsight, but the concepts of the calibration frames are the same. There are also may other videos that discuss different techniques.

- [Calibration of Astronomical Images (PixInsight/WBPP)](https://www.youtube.com/watch?v=sZmHbxIxZeM)
- [WBPP (PixInsight): Flat Darks and Dark Frame Optimization](https://www.youtube.com/watch?v=WzEpygFGbN0)

- I have attached a [video](https://youtu.be/4asrVIc_DCA) that will go over the calibration, stacking and photometry of your images. This video will only cover the photometry of the stacked image , but ASTAP is also able to perform time series photometry.
