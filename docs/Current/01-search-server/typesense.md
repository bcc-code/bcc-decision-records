# TypeSense

## Background

A from scratch engine, not based on Solr/Lucene.
RAM only, so search index must fit in ram (not an issue as far as we are able to tell).

## Pricing

Pricing is extremely clear (https://cloud.typesense.org/pricing?memory=8_gb&vcpu=4_vcpus&high_perf_disk=no&typesense_server_version=0.24.0&ha=no&sdn=off&regions=stockholm) possible to self host. Very granular increments.


## Score card
### Requirements
> 1. be fast and scalable (i.e. we must be able to start small and grow with minimal concern for performance issues when scaled up)

Looks like it is very scalable and distributable

> 2. have a billing model we can understand and control
	* Think that "search as you type" can produce *many* queries
	* Preferably something that does not scale linearly with number of requests

Yes!

> 3. be a mature product that we have reason to believe will be maintained for the next 3-5 years at least

They appear to be 100% bootstrapped and have declined VC in 2022 (https://typesense.org/blog/why-we-are-not-raising-funds/).
Since it is fully open source I believe it is not an issue of operation, but could potentially stop development and shut down at any point.
1/2 point

> 4. be able to comply with GDPR (EU hosting at a minimum)

Can self host or give let them do the hosting. For the cloud version you get your own cluster but of course they have full access to the data.
1/2 point.

> 5. be reasonably easy to use for a developer (no need a math degree to understand what's going on)

Yes, many integrations/SDKs provided

4/5 Points

### Wishlist

* Permissions - Scoped API keys https://typesense.org/docs/0.24.0/api/api-keys.html#create-an-api-key
* Multiple languages (stemming, stop words, etc) - Yes
* Fuzzy search - Yes https://typesense.org/docs/0.24.0/api/search.html#typo-tolerance-parameters
* Faceting - Yes https://typesense.org/docs/0.24.0/api/search.html#faceting-parameters
* Ability to import large documents (300 kb+) - Yes, no stated limit
* Ability to import many documents (1M+) - Yes, no stated limit
* Allow weights/boosting - Yes, https://typesense.org/docs/guide/ranking-and-relevance.html#text-match-score
* Match highlighting - Yes https://recipe-search.typesense.org/?r%5Bquery%5D=Curry&r%5BrefinementList%5D%5Bingredient_names%5D%5B0%5D=Onion&r%5BrefinementList%5D%5Bingredient_names%5D%5B1%5D=Coconut%20milk

8/8 Points

## Summary

Not a super known actor, but seems very interesting.

TODO: Do an actual test with our data
