### Data Augmentation using Zernike Moments for realistic and extreeme PSFs

#### Part1: Image subtraction
**Project Context:** My PhD centred on the rapid discovery of kilonovae. These are the explosions caused by colliding neutron stars. They last between 2-10 days in the visible spectrum, so locating them fast is crucial to understanding their physics. The challenge is that we are looking for them as a counterpart to gravitational waves, the LIGO-O3 sensativity meant this was usually the whole sky (see below).

<img src="images/LIGO.PNG?raw=true"/>

To search these large areas, we need a wide field telescope [GOTO](https://academic.oup.com/mnras/article/511/2/2405/6505141). The problem becomes finding new explosions in a sea of stars. To do this, astronomers use a technique called image subtraction. I implemented a parallelised pythonic version of the ZOGY algorithm, this meant image subtraction could be achieved on the large GOTO images in real time (i.e., image subtraction was completed in less time than the exposure time of the camerars). To make matters more difficult, GOTO had *extreeme* edges. Most telescopes are set such that stars will appear as circles with a 2D-Gaussian spread, this spresd is called the point spread function (PSF). However, this assumption does not hold true for GOTO, meaning a simple Guassian convolution kernel will not do the trick for image subtraction (see below).

<img src="images/Subtraction1.PNG?raw=true"/>

<p style="text-align:center; font-size:10pt"> A guassian convolution kernel on a non-guassian point source, the convolved template does not match the target which results in a residual in the subtracted image. </p>


There are a few compounding issues here. The first is a kernel that makes no assumption about the PSF shape is needed. Secondly, the kernel needs to vary across the the image as the PSF is a function across a 2D plane (see below).

<img src="images/PSF_2D.PNG?raw=true"/>

<p style="text-align:center; font-size:10pt"> The Full Width Half Maximum (FWHM) of the PSF across the image plane. Highlighting the variability of the PSF in a GOTO image. </p>

The solution to this problem is [Zernike Moments](https://www.researchgate.net/profile/Whoi-Yul-Kim/publication/222528464_A_novel_approach_to_the_fast_computation_of_Zernike_moments/links/5bd997de92851c6b279bcca7/A-novel-approach-to-the-fast-computation-of-Zernike-moments.pdf), Zernike moments are a function that maps an image onto a set of complex Zernike polynomials. In short, these functions can recrrate any abitraliy complex 2D images.

<img src="images/Cat_port.PNG?raw=true"/>
<p style="text-align:center; font-size:10pt"> Using Zernike Moments to rebuild the image of a kitten. </p>

Here's the result of the variable Zernike Moments function across one GOTO image. It's versatility allows for a variety of convolution kernels to be built.

**IMAGE** 
<p style="text-align:center; font-size:10pt"> Using Zernike Moments to build a variable convolution kernel across a GOTO image. </p>

We can now compare the results of the subtraction of the leading software ([PSFex](https://www.astromatic.net/software/psfex/)) to my new Zenike Moments subtraction.

**IMAGE**


