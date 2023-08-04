# ManticoreSearch

## Background

Manticore is a fork and upgrade of Sphinx.

Check https://manticoresearch.com/blog/manticore-alternative-to-elasticsearch/ under heading "A little of the history".

Interestingly uses MySQL protocol and SQL to perform queries. I was unable to use any of the more advanced tools to connect.

## Pricing

No hosted service, only professional support.

## Score card
### Requirements
> 1. be fast and scalable (i.e. we must be able to start small and grow with minimal concern for performance issues when scaled up)

At least on paper. I gave up testing it after I was unable to find/install good tooling

> 2. have a billing model we can understand and control
	* Think that "search as you type" can produce *many* queries
	* Preferably something that does not scale linearly with number of requests

Clear billing but not for hosting.

> 3. be a mature product that we have reason to believe will be maintained for the next 3-5 years at least

Very unclear. It is 100% Open so company going under would not impact operations immediately

> 4. be able to comply with GDPR (EU hosting at a minimum)

Self hosting only.

> 5. be reasonably easy to use for a developer (no need a math degree to understand what's going on)

Meh. Mostly PHP based and an experimental "Elastic compatible" interface.

2.5/5 Points

### Wishlist

* Permissions - Can not find any clear documentation about access control. Looks like it is not intended to be hit directly from the client.
* Multiple languages (stemming, stop words, etc) - Yes, but it appears only one at a time
* Fuzzy search - YES
* Faceting - Yes 
* Ability to import large documents (300 kb+) - Officially yes, didn't get to actually testing it
* Ability to import many documents (1M+) - No stated limit. Not tested
* Allow weights/boosting - Yes
* Match highlighting - Yes

6/8 Points

## Technical test

It ran but I was unable to properly interface with it quickly. Considering that the stability is somewhat unknown, I have elected to not investigate more in depth.

## Summary

Considering I gave it a fair try and was not able to use standard tools to interface with it, I consider it not developer friendly enough in light of other alternatives.

