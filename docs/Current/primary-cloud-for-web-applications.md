 
# Primary Cloud For Web Applications

---
**Instructions**
1. [] Fill in description
2. [] Commit file to a *new* branch
3. [] Create a pull-request and add stakeholders as reviewers
4. [] Merge pull-request once a decision has been made
---

**Status**: Assess

## Description
Decide which cloud(s) to use for hosting in-house web applications, which typically consist of the following components:
- API (container-based)
- Static front-end
- Realtime connectivity (e.g. websockets)
- Database (SQL or document DB)
- Cache service (e.g. Redis)
- File storage / delivery
- Search service (e.g. elastic search)

### Context
This decision is limited to custom built web applications since other types of appications (such as BI / reporting or managed services) have thier own constraints. The decision doesn't exclude hosting "niche" services on other clouds, but relates to defining which clouds should be used as the primary cloud(s) for hosting web application infrastructure.
We use Azure AD as our corporate user directory, so moving completely away from Azure is not really an option. 

### Background
Currently we have web applications running on both Azure and GCP. Both clouds have their unique advantages, but the question is whether the business is served by using two clouds instead of just one.

## Alternatives
1. Multicloud strategy (GCP + Azure)
2. Azure-only strategy
3. GCP-only strategy (for web applications)
4. Low-cost hybrid solutions (linode, digital ocean etc.)

### Summary
| #      | Title                                   | Security                     | Delivery                                           | Sustainability |    
| ------ | --------------------------------------- | ------------                 | ----------                                         | ----------     |   
| 1      | Multicloud (GCP+Azure)                  | ❌ (more complex)            | ✅❌ (faster within team, less resuse within org) | ❌✅ (more complex overrall, but flexible) |                          
| 2      | Azure                                   | ✅ (simplest overall)        | ✅ (feature rich)                                  | ✅           |     
| 3      | GCP                                     | ✅ (but good default config) | ✅ (robust)                                        | ❌ (more comlex overall)         |
| 5      | Low Cost                                | ❌                           | ❌                                              | ✅ (lower cost)             |

### Alt 1: Multicloud strategy (GCP + Azure)
In this solution, we support deploying applications to both GCP and Azure and leave the decision to the development team.

The consequences of this are as follows:
1. The teams can pick the cloud they like best
2. We need to maintain know-how and best practices for both clouds (including security, deployment, right-sizing, architecture, monitoring etc.)
3. We need to monitor 2+ clouds (tracing, cost-monitoring etc.)
4. Resources will _typically_ only be shared within one cloud
5. We can pick the cloud that is best suited to the specific needs of the project (technology, cost etc.)

**Risks**  
1. Increased cognative load at an organizational level
2. Less expert knowledge exchange between teams + projects
3. Less redundancy in terms of technical know-how (ie. less developers can jump into "any" project)
4. Potentially more expensive (due to less shared resources + importantly more time on developing know-how and best practices overall)
5. Security management is substantially more complex (at an organizational level)
6. Cost management is more complex (at an organizational level)
7. Monitoring is more complex (at an organizational level)

**Benefits**  
1. Get to pick the "best" of both worlds
2. Developers enjoy working with technologies they know best (and may be most productive doing so -- at least short to mid term)
3. Don't need to migrite existing projects to one or the other cloud (NB. still need to migrate to terraform + shared resources within existing clouds)


### Alt 2: Azure-only strategy (for web apps)
In this solution, we use Azure as the primary platform for hosting web applications. As noted above, Azure is already used as our corporate user directory, making security management more straight forward. 

Azure is developed by Microsoft and in _general_ the following can be said of Azure:
1. Well integrated with Microsoft technologies such as .Net, Azure AD
2. It has a broader offering in terms of services and features within the services than GCP (examples: horizonally scalable postgresql, online db editor, console access to containers, pgBouncer for postgresql, dapr for container apps, etc.)
3. Features occassionally feel a little less robust than the GCP (e.g. container startup time, terraform deployment). The feeling is that MS roles out features faster, but somewhat less mature than GCP. In most cases however, it is a matter of time before things become stable/comparable.
4. Pricing can be higher for certain resources (such as container apps, realtime DB)
5. Application insights provides fantastic functionality, but does not support GoLang natively as of today.

**Risks** 
1. Potentially higher costs for the same resource type
2. Potentially less stable / performant for the same resource type (e.g. container apps)
3. Need to migrate existing solutions

**Benefits**  
1. Easier to handle security, monitoring, cost control
2. Reduce costs through more shared resources
3. Reduce costs through requiring less "redundant" know-how

### Alt 3: GCP-only strategy (for web apps)
In this solution we use GCP as the primary platform for hosting web applications. In this scenario, Azure could still be used as a user directory and synchronized with GCP.

GCP is developed by Google and in _general_ the following can be said of GCP:
1. Low cost for realtime db (propriotory firebase)
2. Good performance and low costs associated with hosting APIs (Cloud run)
3. Good (better) security configuration "by default" (esp. things like cloudproxy)
4. Pricing often slightly lower than Azure (with some notable exceptions like BigQuery, SpannerSQL).
5. Monitoring and tracing tooling is less mature and more "clunky" than on Azure, but supports Go-lang out of the box.

**Risks**  
1. Need to migrate existing projects from Azure - many of which run on .Net (poorer experience)
2. Smaller offering and missing features compared to Azure
3. No presence in Norway (yet)
4. Poorer monitoring experience
5. Need to manage security, costs etc. in multiple clouds (due to corporate applications)

**Benefits**  
1. In general, cheaper and robust services (e.g. cloud run)
2. Loved by existing teams

### Alt 4: Low Cost hybrid strategy
There are a number of alternative cloud providers such as Linode, Digital Ocean etc. which can provide competive pricing compared to Azure and GCP for certain types of resources. 

This is an avenue we haven't fully investigated. In general, the service offerings are much smaller, so it is likely we'd need to use a combination of services. 

**Risks**  
1. More difficult to manage access control, onboarding/offboarding and maintining account access
2. More things to document
4. Typically less stable services (although there may be exceptions)
5. Harder to monitor costs

**Benefits**  
1. Lower costs for certain resouce types

## Assessment
Intuitively an organization of our size and complexity should only use **one** cloud. However, since we already are spread accross two clouds and a range of technologies, the best solution becomes somewhat less clear cut.

Specifically for end-user / high volume web applications, GCP is an appealing platform due to it's robust and secure nature. In addition, having applications that "talk" together in the same cloud is good for tracing, latency etc. 

In general, the knowlege gained in one cloud, can be transferred to another (at a high level). Keeping the same "types" of applications in the same cloud could be beneficial for reuse of more specific knowledge.

In addition, synchronizing users and groups from Azure to GCP has proved to work nicely so far.

For specific applications (such as self-service BI), Azure is probably still a better platform whereas for some niche services (like streaming) other platforms (AWS) are more suitable.

The recommendation for "trial" is to make GCP the "default" cloud for container-based web apps, and work on:
1. Developing best practices for monitoring and tracing.
2. Investigate sharing resources (specifically Redis and Postgresql) on GCP
3. Investigate performance concerns with CloudSQL (can we get pgBouncer setup?)

## Trial
[TODO: Document experience after trialing]


## Decision
[TODO: Document final decision and update tech radar]
      
