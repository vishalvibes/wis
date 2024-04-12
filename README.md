# Web Intelligence Specification (WIS)


## Metadata

|Tag |Value |
|---- | ---------------- |
|Proposal |[2024-04-13-WIS](https://github.com/vishalvibes/wis)|
|Authors|[Vishal Pratap Singh](https://github.com/vishalvibes), [Harman Marshal Singh](https://github.com/marshalharman)|
|Review Manager | TBD |
|Status |Draft|
|Implementations |NULL|
|Issues |NULL|
|Previous Revisions |NULL|


## Introduction

The Web Intelligence Specification (WIS) provides a set of guidelines for structuring web applications to improve interaction with AI agents.

## Motivation

The WIS approach effectively decouples the AI's understanding and language processing capabilities from the application's logic and data. By doing so, it allows developers to build AI-friendly web services without tailoring them to a specific AI’s capabilities.


## Proposed solution

Add desctipion

### Workflow 1

`/features`

`Returns` Endpoints with heirarchy rules and description

```javascript
{
  status,
  data,
  actions,
}
// actions: L2 heirarchy endpoints
```

![Workflow 1](https://i.imgur.com/9Fg52Xu.png)

### Workflow 2

`/ask`

![Workflow 2](https://i.imgur.com/5x6tc83.png)

The `/features` endpoint serves as a discovery mechanism for AI to ascertain what the service can do, while the `/ask` endpoint provides a way for AI to engage with those features using natural language.


~~Describe your solution to the problem.~~

Provide examples and describe how they work. -> Maps + Food + Cab booking integration


Show how your solution is better than current workarounds: is it cleaner, safer, or more efficient? -> Current workarounds only work on one web app at a time and scrape UI


## Comparison With Current Workarounds



## Examples

~~## Detailed design~~

~~Describe the design of the solution in detail. This should include an exact description of the changes to the contents of the OpenAPI specification. That description should include a extract of each section of the OpenAPI specification which is impacted by the proposal with all proposed modifications applied. These extracts may be provided through additional files which are identified and described in this section.~~

## Backwards compatibility

Proposals should be structure so that they can be handled by existing OAS compliant software. Any potential issues should be identified and discussed.


### Seamless Integration

Gradual Adoption: WIS allows for incremental implementation alongside existing features.

Modular Approach: Acts as an independent module, leaving the core 
application unchanged.

### Preservation of Existing Infrastructure
Utilization of Current APIs: Enhances current APIs with AI capabilities without fundamental changes.

No Downtime Required: Integrates with current systems without service interruptions.

### Flexible Deployment
Independent Updates: Permits isolated updates to the AI layer without affecting the main application.

Optional Use: Provides AI functionalities as an optional layer for users who wish to utilize it.
### Risk Mitigation
Phased Roll-Out: Enables controlled, step-wise integration to assess impact and performance.

Fallback Mechanisms: Offers traditional service methods as a backup to maintain continuity.

### Forward Compatibility
Scalable for Future AI Advancements: Ensures the system can evolve with AI technology.

Adaptation to AI Progress: Allows enhancements to the WIS component as AI develops, without disrupting the existing application.



## Alternatives considered

Describe alternative approaches to addressing the same problem, and why you chose this approach instead.