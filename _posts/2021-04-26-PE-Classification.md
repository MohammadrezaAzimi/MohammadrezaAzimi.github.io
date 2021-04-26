---
title: "Industry Classification for Private Companies"
date: 2020-06-01
tags: [ML, Natural language processing]
excerpt: "NLP, IMDB"
mathjax: "true"
---
### Project description

In investment banking, identifying the industry of a private company plays an important role for different purposes such as intializing the IPO, acquisition, etc. Each private company can be active in more than one industry. The major problem is that the financial information such as revenue, earnings, share price valuation, etc. are not available for private companies. The following steps are used to build the supervised ML model.  

Data scources: 

1. Purchased data sources that provide the name of private companies, their investors, their previous deals, industry at the highest level such as health care or technology.  

2. External data sources such as the result of web scraping by Bing, or Google News

3. A sample of desired internal classification based on the developed taxonomy using bankers' jargon.  


Example: It is shown in the following figure:

<img src="{{ site.url }}{{ site.baseurl }}/images/PE-Classifiaction/PE.png" alt="ooo">

Details: For the described problem, NLP can be used to translate the unstractured text data to a vector of numerical values. Different binary of multi-class classification approaches can be used to train a model on the labeled data which is eventually be used for the prediction. 

For further questions, please contact me at sa677@njit.edu. 