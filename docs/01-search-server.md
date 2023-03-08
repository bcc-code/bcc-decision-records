# Search engine for BCC

## Status

Proposed

## Context

Currently everyone at BCC is using something custom for the search needs, that works or does not work. For example BCC Media APP uses Algolia, BMM uses the built in capabilities of RavenDB. 

We would like to standardize on one solution that is powerful and flexible enough to be shared amongst the different projects in the organization at large.

### Usage Examples

* Bcc Media search
	* Full text of content
	* Title only
	* ...
* BMM search
	* Full text of content
	* Title
	* Song numbers
	* Verses
* Literature
	* Full text search
	* Title Search
	* Keyword search
* Portal
	* Unified search across products

## Requirements

The system must:
1. be fast and scalable (i.e. we must be able to start small and grow with minimal concern for performance issues when scaled up)
2. have a billing model we can understand and control
	* Think that "search as you type" can produce *many* queries
	* Preferably something that does not scale linearly with number of requests
1. be a mature product that we have reason to believe will be maintained for the next 3-5 years at least
2. be able to comply with GDPR (EU hosting at a minimum)
3. be reasonably easy to use for a developer (no need a math degree to understand what's going on)

It should support the following features (loosely ordered by priority):

* Permissions
* Multiple languages (stemming, stop words, etc)
* Fuzzy search
* Faceting
* Ability to import large documents (300 kb+)
* Ability to import many documents (1M+)
* Allow weights/boosting
* Match highlighting

## Alternatives

The alternatives that need closer investigation are:

* [Elastic Search](https://www.elastic.co/)
* [Azure Cognitive Search](https://azure.microsoft.com/en-us/products/search/)
* [AWS CloudSearch](https://aws.amazon.com/cloudsearch/)
* [TypeSense](https://typesense.org/)
* [Sphinx](http://sphinxsearch.com)
* [MeiliSearch](https://github.com/meilisearch/meilisearch)
* [ManticoreSearch](https://github.com/manticoresoftware/manticoresearch)

Other alternatives that have been disqualified already:

* Apache Solr
	* This is the core of Elastic Search so it does not provide lots of convenient tooling that one gets with ES
* [Algolia](https://algolia.com)
	* [Limit on record size](https://support.algolia.com/hc/en-us/articles/4406981897617-Is-there-a-size-limit-for-my-index-records-)
	* Direct scaling with number of requests
	* Focused on E-Commerce so partially not very flexible
	
## Decision

PENDING

Currently the favourite is Elastic search:

* We have already validated that it can handle the documents 
* It meets all requirements
* It seems to have all the needed features
