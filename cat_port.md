### Data Augmentation using Zernike Moments for realistic and extreeme PSFs


**Project Context:** My PhD centred on the rapid discovery of kilonovae. These are the explosions caused by colliding neutron stars. They last between 2-10 days in the visible spectrum, so locating them fast is crucial to understanding their physics. The challenge is that we are looking for them as a counterpart to gravitational waves, the LIGO-O3 sensativity meant this was usually the whole sky (see below).

<img src="images/LIGO.PNG?raw=true"/>

To search these large areas, we need a wide field telescope (GOTO). The problem becomes finding new explosions in a sea of stars. To do this, astronomers use a technique called image subtraction. I implemented a parallelised pythonic version of the ZOGY algorithm, this meant image subtraction could be achieved on the large GOTO images in real time (i.e., image subtraction was completed in less time than the exposure time of the camerars). To make matters more difficult, GOTO had *extreeme* edges. Most telescopes are set such that stars will appear as circles with a 2D-Gaussian spread, this spresd is called the point spread function (PSF). However, this assumption does not hold true for GOTO, meaning a simple Guassian convolution kernel will not do the trick for image subtraction (see below).

**IMAGE**
<img src="images/LIGO.PNG?raw=true"/>

<p style="text-align:center"> A guassian convolution kernel on a non-guassian point source, the convolved template does not match the target which results in a residual in the subtracted image. </p>


Enter Zernike Moments!




