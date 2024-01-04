## Amazon Review Webscraper

One of the first challenges I was given working in [current company] was to quickly determine sentiment of amazon purchases. 
I started by building a generalised web scraper (All the scraping code at the bottom of the page 😉) and using that too mine the data.

All the content of the review is captured; including date it was written, product rating, images, URL of the review, if the purchase is verrfied, and the product variant. This means you can filter your search by more than just product.

Generally speaking, sentiment can be determined by star ratings. All >1 star ratings match their expected sentiment (people clicking on stars do it on purpose, but a lot of people forget to rate and the default is 1 star). This meant that a little sentiment analysis has to be done on 1 star reviews to make sure they're intnetionally 1 star. 

After the analysis has been done word clouds can be built to establish key themes in the ratings. 
[insert pics]

