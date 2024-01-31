# Returns Analysis

After six months of working at [company], I was tasked with cleaning some returns data for a new product we had just released. Like any good data scientist I visualised all the available data and quickly spotted a problem unrelated to the work I was tasked with. **Two of our products were seeing a massive maintained rise in returns**. I immediately infromed the CTO and Head of Quality (owner of the data) to see if this was something they were aware of. They were not. A response team was built to figure out the issue and I was tasked to lead the data exploration front. 

## Visualising the Issue

The first thing I did was break down WHY the problem had been missed. Up until my snooping, the company was using bulk retail performance of each product per region. This meant that returns impact of faulty batches were convolved with returns of products that were performing normally. In other words, while the functioning batches saturated the sales the underlying problem went undetected **for months**. A second problem was with data capture and data quality. To avoid this problem happening again I developed an intuitive visualisation and alert system that will show when batches start under-performing. 

<img src="/images/BScatter.PNG?raw=true"/>

The above is manufacture date against returns lag (time between manufacture and return) in discrete units (days/weeks/months). The colour of the dot indicates the proportion of the batch made in that manufacturing month that has been returned. The company only care about losses, so any returns after the warranty period are not of concern. The sum of each vertical line is the total return proportion of a batch. The sum of each diagonal indicates the return for a given month. If a dot turns red, the returns rate is higher than what the company deems acceptable. If a column of dots turn red, that is an indication that there is something wrong with a batch. If a diagonal turns red that means there was something wrong with the environment (e.g., a power surge breaking the product, or social perception of the company plumets). Here we can see the problem was with individual batches.

## Determining the problem

Seeing this was a batch issue, I asked for a component break down of some working batches and some broken batches. Using some basic set theory, my hope was that I could highlight shared components in the broken stylers that weren't present in the working batches. 

<img src="/images/BAnaly_found.png?raw=true"/>

The evidence here was clear. There was only one component that was consistent in the broken batches and not the working batches. What's more, this component had been introduced as a result from supply chain issues at the exact manufacture date the returns started. This compnonent analysis saved about 3 months of testing. (As an aside, the component introduced had a lower breaking tolerance than the original; this pointed to a fault that also occurs in the working batches. Years of testing prior to me starting was unable to diagnose the problem. Using my analysis, the company were finally able to address this issue, saving the company millions.)

## Modelling the Impact

## Tracking the damage

## Outcomes
