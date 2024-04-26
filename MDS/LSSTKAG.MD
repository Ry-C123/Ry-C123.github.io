# LSST PLAsTiCC Astronomical Classification

This was my first encounter with data science! It was a [kaggle challenge](https://www.kaggle.com/competitions/PLAsTiCC-2018) that had surprising overlap with my PhD. The goal was to identify signal sources in multi-colour phtometric and spectroscopic data in LSST (The Large Synoptic Survey Telescope.) [The code](https://github.com/Ry-C123/LSSTplasticc_kaggle/tree/master) is not great, but I was a young novice!

In essence, through data exploration, I was able to identify 2 clear groups of classes. Those whose redshift was 0 (intra-galatic sources) and those who were redshifted z>0 (extra-galatic). I was further able to see that most sources had spectroscopic variability. This meant I could create an extra feature using a multi-bandpass Lomb-Scargle. 

For the Z=0 group I was able to get > 80% accuracy:

<img src="/images/LSSTKAG/CFM1.PNG?raw=true"/>

For the Z>0 group my accuracy was a little less great:

<img src="/images/LSSTKAG/CFM2.PNG?raw=true"/>

If I had more time I would have looked more deeply into classes 15,42, 52, 62, 67, and 90. The fact that they were the only ones where there was true confusion suggests they belong in the same super-class. The trebulations of a PhD means you don't have much time to waste on fun challenges!

I believe for a first attempt at any machine learning my placement in the rankings was respectable.

<img src="/images/LSSTKAG/RES.PNG?raw=true"/>
