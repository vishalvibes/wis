# Web Intelligence Specification (WIS)

## Metadata

| Tag                | Value                                                                                                           |
| ------------------ | --------------------------------------------------------------------------------------------------------------- |
| Proposal           | [2024-04-13-WIS](https://github.com/vishalvibes/wis)                                                            |
| Authors            | [Vishal Pratap Singh](https://github.com/vishalvibes), [Harman Marshal Singh](https://github.com/marshalharman) |
| Review Manager     | TBD                                                                                                             |
| Status             | Draft                                                                                                           |
| Implementations    | NULL                                                                                                            |
| Issues             | NULL                                                                                                            |
| Previous Revisions | NULL                                                                                                            |

## Introduction

The Web Intelligence Specification (WIS) provides a set of guidelines for structuring web applications to improve interaction with AI agents.

## Motivation

Creating LLM agents that browses the web is difficult.

Due to the lack of any structure or information, LLM agents need to be configured by the creators for every web application separately.

However, envision a paradigm shift: if the web applications themselves can help LLM agents to browse them effectively. It would be a game changer.

The WIS approach proposes a universal standard to effectively decouple the visiting AI Agent's understanding capabilities from the application's logic and user interface.

By doing so, it allows developers to build AI-friendly web applications without tailoring them to a specific AI’s capabilities.

## Proposed solution

We propose a very simple guideline for web applications to follow.

Developers could implement these 2 workflows into their web application.

### Workflow 1

![Workflow 1](https://i.imgur.com/ujH7AlD.png)

In workflow 1 the visiting agent has to run a loop to perform any operation. It would be visiting `/actions` before performing any other operation. This endpoint will give instructions to the visiting agent about how to should an agent start to navigate this webapp.

Meanwhile, For the web applications following WIS workflow 1, it is mandated to implement a `/actions` route.

This route would return a json object which would contain a list of endpoints (Just L1 hierarchy), a description in natural language of their functionalities, a list of input parameters and the return value details.

```javascript
{
  "status",
  "actions":[
    {
      endpoint,
      description,
      parameters:[],
      return_data_details
    }
  ],
}

//actions: 1st level heirarchy endpoints
```

Each of the endpoint which are mentioned in the `/actions` endpoint are mandated to have their return data in the following format.

They too would contain a list of endpoints instructing, what further actions can the agent perform from here.

It's tree like structure, similar to how users navigate through UI interfaces.

```javascript
{
  "status",
  "data",
  "actions":[
    {
      endpoint,
      description,
      parameters:[],
      return_data_details
    }
  ],
}

// ${action_endpoint_x}: (n+1)th level heirarchy endpoints
```

### Workflow 2

`/ask`

![Workflow 2](https://i.imgur.com/D3OkqTq.png)

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
