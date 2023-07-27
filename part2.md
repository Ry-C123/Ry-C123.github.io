### Data Augmentation using Zernike Moments for realistic and extreeme PSFs Part2


If you haven't read [part 1](cat_port.md) yet, I highly reccomend you do to gain the full experience ;)

---

#### Part2: Injecting Fake Explosions

One of the biggest problems in transient astronmy, when building methadology, is that true transients are very uncommon. So much so, that it is impossible to reliably test any transient identification method using raw data. Therefore, to test the reliabilty of image subtraction we must inject fake transients into our data. Below shows the result of this process.

<img src="images/Galaxy_sub.PNG?raw=true"/>

The above shows that even in the noisiest parts of the image (the centre of a galaxy), tranisents can be resolved easily (the black dots). In fact, one of the pivotal results of my thesis was that we could resolve tranisents down to the noise limit in GOTO images at record speed. The subtraction algorithm uses a modified verison of [ZOGY](https://iopscience.iop.org/article/10.3847/0004-637X/830/1/27) that segments the image and computes the subtraction in a parallel fasion. Below shows the retrieval capabilities of each method. HOTPANTS was the gold standard subtraction algorithm at the time. ZOGY clearly performed better, but would take up to 7 minutes per image. GOTO exposures were 3 minutes and would 8 at a time. This means per 3 minute exposure there was 56 minutes of image processing. Not ideal for real-time transient hunting. ZOGY in Parallel [ZiP](https://github.com/GOTO-OBS/ZiP) would compute all 8 images in under half a minute! Leaving plenty of time to actually find transients. 

<img src="images/SPEEDY.PNG?raw=true"/>
