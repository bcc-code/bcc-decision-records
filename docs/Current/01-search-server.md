# Search Engine Standardization for BCC

**Status**: Proposed

## Description
Evaluate and decide on a standardized search engine solution for BCC projects.

### Context
BCC's various projects require a search engine solution that meets a set of requirements.

Examples of such projects are:

* Bcc Media:
	* Full text of content
	* Title only
	* ...
* BMM:
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

### Background
Currently, different projects use different search solutions. The goal is to standardize on a single, powerful, and flexible solution.

## Alternatives

Main alternatives that were evaluated a bit closer are: 

* Elastic Search, 
* Azure Cognitive Search
* AWS CloudSearch 
* TypeSense
* MeiliSearch
* ManticoreSearch

### Disqualified alternatives

Here are some other search engines that popped up, but have been removed from closer investigation for stated reasons.

* Apache Solr
	* This is the core of Elastic Search so it does not provide lots of convenient tooling that one gets with ES
* Apache Lucene	
	* Is what solr is built on so, even more low level than Solr
* [Algolia](https://algolia.com) - Currently in use by BCC Media
	* [Limit on record size](https://support.algolia.com/hc/en-us/articles/4406981897617-Is-there-a-size-limit-for-my-index-records-)
	* Direct scaling with number of requests
	* Focused on E-Commerce so partially not very flexible
* [Sphinx](http://sphinxsearch.com)
	* Is the predecessor upon which ManticoreSearch is built
	* Appears to be only barely maintained

### Summary

| #      | Title                                   | Security         | Delivery     | Sustainability |    
| ------ | --------------------------------------- | ------------     | ----------   | ----------     |   
| 1      | Elastic Search                          | ✅               | ✅           | ✅             |                          
| 2      | Azure Cognitive Search                  | ✅               | ✅           | ✅/❓            |     
| 3      | AWS CloudSearch                         | ✅               | ✅           | ✅/❓           |     
| 4      | TypeSense                               | ✅               | ✅           | ❌             |
| 5      | MeiliSearch                             | ✅               | ✅           | ❌             |
| 6      | ManticoreSearch                         | ❌               | ❌           | ❌             |


### Alt 1: Elastic Search
Elastic search is a well known entity with long history and wide use in all kinds of industries.
Examples of confirmed users that are relevant to above use cases:

* Netflix
* Adobe
* U.S. Airforce (ref Security)
* Spotify
* Stack Excahange (StackOverflow)

**Risks**  
- It can be very complex.

**Benefits**  
- Mature product with rich features.
- Widely used in many related industries (somewhat gold standard for search right now)

### Alt 2: Azure Cognitive Search
A Microsoft Azure-based search engine solution. See [notes](./01-search-server/azure-cognitive-search.md) for more details.	

**Risks**  
- Billing vs. Performance is unclear
- Vendor lock in

**Benefits**  
- Integrates well with other Azure services

### Alt 3: AWS CloudSearch
An Amazon Web Services-based search engine solution. 
Has not been evaluated in detail as the marketing materials did not suggest a significant difference to Azures version,
with the added hurdle of it being in AWS which is currently not heavily utilized by BCC.

**Risks**  
- Billing vs. Performance is unclear
- Vendor lock in

**Benefits**  
- ?

### Others

See notes on [TypeSense](./01-search-server/typesense.md), [MeiliSearch](./01-search-server/meilisearch.md), [ManticoreSearch](./01-search-server/manticore.md).

The common theme is that while they are ok, there is nothing that seems to significantly improve the suitability for our use cases,
while introducing a risk of using (potentially) not very mature software.

## Assessment

We decide on a test with hosted Elastic search Cluster in Azure. This gives us the benefits of having as much control as we can get while still not having to actively think about hosting.

This test is in progress for BMM and Bcc Media at the time of writing.

## Trial
[TODO: Document experience after trialing]

## Decision
PENDING. 



