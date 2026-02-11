 
# Load Testing Tool Selection

**Status**: Accepted

## Description

### Context
Our applications require robust load testing to ensure performance and reliability under high user demand. The team needs a tool that supports complex workflows, is easy to use, and integrates well with our existing technology stack.

### Background
During development of the Privacy and consents web app, load testing was being done using a custom tool. This proved to be too time consuming, due to complex behaviour depending on which load profile was being used. Therefore, we decided to evaluate existing load testing tools that could better meet our needs.

## Alternatives

1. Self-authored tools
   Seen as very flexible but lacking in advanced features, scalability, correctnes and reuseability,
2. Loader.io
   Already used by the team, but more suited for simple load tests; limited in handling complex workflows.
3. K6
   A modern, JavaScript-based tool known for its developer-friendly scripting and cloud scalability.
4. NBomber
   A .NET-native framework allowing complex multi-step workflows using C#.

Several other tools investigated previously seemed overly complex to work with.

## Decision: 
After evaluating the alternatives, we have decided to adopt K6 as our primary load testing tool. K6 offers a good balance of ease-of-use, powerful scripting capabilities, and cloud scalability. Its JavaScript-based scripting is familiar to our developers, and it supports complex user workflows effectively.

Points for K6:

- It uses Javascript, which is widely known among our team members.
- It has strong community support and extensive documentation.
- It integrates well with CI/CD pipelines, facilitating automated performance testing.
- It has a wider usage in the industry, making it easier to find resources and expertise, especially when using AI tools for assistance.
- It offers cloud execution options, allowing us to scale our tests without significant infrastructure overhead. (BCC Fellestjenester has a non profit account on Grafana Cloud with reduced price)
- Event team has some prior experience with K6, which will help in the initial setup and training.

## Consequences:
By choosing K6, we expect to improve our load testing processes, enabling more comprehensive performance evaluations. The team will need to invest time in learning K6's features and best practices. We should use Grafana Cloud for large-scale testing, which may incur additional costs. However, the benefits of using a robust and scalable tool outweigh these considerations.
