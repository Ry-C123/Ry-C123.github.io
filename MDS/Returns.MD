# TITLE

After six months of working at [company], I was tasked with cleaning some returns data for a new product we had just released. Like any good data scientist I visualised all the available data and quickly spotted a problem unrelated to the work I was tasked with. **Two of our products were seeing a massive maintained rised in returns**. I immediately infromed the CTO and Head of Quality (owner of the data) to see if this was something they were aware of. They were not. A response team was built to figure out the issue and I was tasked to lead the data exploration front. 

## Visualising the Issue

The first thing I did was break down WHY the problem had been missed. Up until my snooping, the company was using bulk retail performance of each product per region. This meant that returns impact of faulty batches were convolved with returns of products that were performing normally. This meant that while the functioning batches saturated the sales the underlying problem went undetected **for months**. A second problem was with data capture and data quality. To avoid this problem happening again I developed an intuitive visualisation and alert system that will show when batches start under-performing. 

<img src="/images/BScatter.PNG?raw=true"/>

The above is manufacture date against returns lag (time between manufacture and return) in discrete units (days/weeks/months). The colour of the dot indicates the proportion of the batch made in that manufacturing month that has been returned. The company only care about losses, so any returns after the warranty period are not of concern.  

## Determining the problem

## Modelling the Impact

## Tracking the damage

## Outcomes
