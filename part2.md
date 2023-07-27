### Data Augmentation using Zernike Moments for realistic and extreeme PSFs Part2


If you haven't read [part 1](cat_port.md) yet, I highly reccomend you do to gain the full experience ;)

---

#### Part2: Injecting Fake Explosions

One of the biggest problems in transient astronmy, when building methadology, is that true transients are very uncommon. So much so, that it is impossible to reliably test any transient identification method using raw data. Therefore, to test the reliabilty of image subtraction we must inject fake transients into our data. Below shows the result of this process.

<img src="images/Galaxy_sub.PNG?raw=true"/>

The above shows that even in the noisiest parts of the image (the centre of a galaxy), tranisents can be resolved easily (the black dots). In fact, one of the pivotal results of my thesis was that we could resolve tranisents down to the noise limit in GOTO images at record speed. The subtraction algorithm uses a modified verison of [ZOGY](https://iopscience.iop.org/article/10.3847/0004-637X/830/1/27) that segments the image and computes the subtraction in a parallel fasion. Below shows the retrieval capabilities of each method. HOTPANTS was the gold standard subtraction algorithm at the time. ZOGY clearly performed better, but would take up to 7 minutes per image. GOTO exposures were 3 minutes and would 8 at a time. This means per 3 minute exposure there was 56 minutes of image processing. Not ideal for real-time transient hunting. ZOGY in Parallel [ZiP](https://github.com/GOTO-OBS/ZiP) would compute all 8 images in under half a minute! Leaving plenty of time to actually find transients while still performing as well as it's serial predecessor. 

<img src="images/SPEEDY.PNG?raw=true"/>

Here, as stellar magnitude increses, the fainter they get. This means, that most tranients up to 19th magnitude (the noise limit of GOTO prototype images) would be found.  

---

Alright, so now we have an optimal image subtraction algorithm that can find transients down to the noise limit of the image in real-time. We now enter the meat of the final problem. Image subtraction was originally developed on very few and reltively small images, a person could scour them in an evening and pick out the interesting finds. GOTO, however, takes 100s of images every night and each of those images are huge! Even a team of 50 people would take years to look through all the images taken in one night. This means, spotting residuals in the subtracted image needs to be automatic. Luckily a tool called [SExtractor](https://www.astromatic.net/software/sextractor/) (seriously called that) already does this exact job. The problem with automation is that false posotives slip through, so human inspection is still needed. Again this was always doable with smaller images with roughly 100:1 false positives per real transient; GOTO on the other hand, is closer to 10,000:1 becuase of the sheer size of the images. The magnitude of the problem meant we needed to implement machine learning to filter out false posotives in the subtracted data!

In an earlier [research paper](https://academic.oup.com/mnras/article-abstract/499/4/6009/5920226?redirectedFrom=fulltext) we sucessfuly showed that injecting fake transients into the images is a viable data augmetation technique to train a machine learner to filter out false positives. One of the biggest problems faced in the paper was that the injected tranisents were not realstic. So, to improve training in my thesis, I implemented the Zernike Moments PSF estimator from part 1! As shown below, the injected sources would then much better represent what a true transient would look like in the GOTO data.

<img src="images/INJECTION.PNG?raw=true"/>

For proof of concept, a basic neural net was built and trained on the subtracted images. A strict 95% confidence was used to filter out as many false posotives as possible while still containing a reasonable portion of the injected sources. This method proved to be increadibly powerful, finding 100% of transienrs down to magnitude 18.5.

<img src="images/BIG.PNG?raw=true"/>

Finally, an image subtraction pipeline was built to run on the historic LIGO-O3 GOTO campaign data to find transients coincident with gravitational waves. This archive contained over 7000 images, the subtraction process produced 74317748 potential candidates that needed to be filtered. My algorithm reduced that number to just 49 potential candidates. Of the 49 candidates, 16 were determined to be transients that were temporally and spatially coincident with a gravitational wave event. This proved that GOTO is capable of real time kilonova discovery. 



