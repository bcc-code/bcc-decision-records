# Azure cognitive search

## Pricing
Confusing and to me not understandable. They talk about "search units", and it has so far not been very clear to me what one search unit it.

There are 2 sections on calculating costs in the azure docs:

https://learn.microsoft.com/en-us/azure/search/search-capacity-planning
https://learn.microsoft.com/en-us/azure/search/search-sku-manage-costs

I feel that the pricing scales *extremely* quickly. Basically starts at 250$/month for a prod environment and multiplies from there. For me it is at this point hard to calculate how much we would *actually* need.

## Background

It is basically a managed Lucene cluster. Quote from the [docs](https://learn.microsoft.com/en-us/azure/search/search-faq-frequently-asked-questions):

> ### Does Cognitive Search support vector search?
> 
> No. Currently, Cognitive Search runs on a version of Apache Lucene that doesn't support vector search.


## Score card
### Requirements
> 1. be fast and scalable (i.e. we must be able to start small and grow with minimal concern for performance issues when scaled up)

Semi true. The jumps in capacity seem to be large with no easy way to gradually increase in steps less than 2.5knok/month

> 2. have a billing model we can understand and control
	* Think that "search as you type" can produce *many* queries
	* Preferably something that does not scale linearly with number of requests

I do not agree that the pricing model is clear. It is well documented but hard to estimate the requirement as it seems to abstract away things like RAM and CPU.

> 3. be a mature product that we have reason to believe will be maintained for the next 3-5 years at least

There is no specific reason to believe that MS will discontinue this product, as it seems to be actively developed (several features in preview)

> 4. be able to comply with GDPR (EU hosting at a minimum)

Hostable in EU under our own account. I believe that satisfies GDPR

> 5. be reasonably easy to use for a developer (no need a math degree to understand what's going on)

Seems ok. It is after all Lucene in a pretty package

3/5 Points

### Wishlist

* Permissions - Not built in: https://learn.microsoft.com/en-us/azure/search/search-modeling-multitenant-saas-applications
* Multiple languages (stemming, stop words, etc) - Yes
* Fuzzy search - Yes https://learn.microsoft.com/en-us/azure/search/search-query-fuzzy
* Faceting - Yes https://learn.microsoft.com/en-us/azure/search/search-faceted-navigation
* Ability to import large documents (300 kb+) - 16MB Via api https://learn.microsoft.com/en-us/azure/search/search-limits-quotas-capacity#document-limits
* Ability to import many documents (1M+) - 24B https://learn.microsoft.com/en-us/azure/search/search-limits-quotas-capacity#document-limits
* Allow weights/boosting - Yes, standard Lucene function
* Match highlighting - Yes https://learn.microsoft.com/en-us/azure/search/search-pagination-page-layout#hit-highlighting

7/8 Points

## Summary

Not great, not bad.
Unlikely choice due to the limits imposed, compared to f.ex. Elastic.
