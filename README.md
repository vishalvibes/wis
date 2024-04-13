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

## Workflow 1

![Workflow 1](https://i.imgur.com/ujH7AlD.png)

In workflow 1 (Actions Workflow) the visiting agent has to run a loop to perform any operation.

It would be visiting `/actions` before performing any other operation.

This endpoint will give instructions to the visiting agent about how to should an agent start to navigate this webapp.

Meanwhile, For the web applications following WIS workflow 1, it is mandated to implement a `/actions` route.

This route would return a json object which would contain:

- List of endpoints (Just L1 hierarchy)
- Description in natural language of their functionalities
- List of input parameters
- Return value details

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

They too would contain a list of endpoints instructing further actions that the agent could perform after it has the return data in this response.

It's a `tree like structure`, similar to how users navigate through UI interfaces.

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

## Workflow 2

Workflow 2 (Ask Workflow) is recommended only for more complex web applications with the resources to create their own LLM application.

This is a more futuristic workflow, where one agent talks to the other.

Any workflow that implements this workflow is mandated to create a `/ask` route.

An external user agent could query `/ask` in natural language and get things done directly without running any loops.

This obviously means that the loop is run by web applications own agent internally and all the processing has been shifted to the application side instead of users side.

This would take more effort to create, hence not recommended for smaller applications.

![Workflow 2](https://i.imgur.com/D3OkqTq.png)

The `/actions` endpoint serves as a discovery mechanism for AI to ascertain what the service can do then query endpoints in a loop, while the `/ask` endpoint provides a way for AI to engage with the application using natural language.

## Comparison With Current Workarounds

Current workarounds are either trying to create an agent that could interract with frontend interfaces that are primarily built for humans.

Or are trying to integrate one web application at a time, which restricts small developers to build general purpose agents and applications with ease.

## Example

Placing order from a nearby restaurant with good reviews.

In this example we will demonstrate the actions workflow.

![Example workflow](https://i.imgur.com/gop8TtU.png)

## Backwards compatibility and Benefits

- **Gradual Adoption:** WIS allows for incremental implementation alongside existing features.

- **Modular Approach:** Acts as an independent module, leaving the core application unchanged.

- **Utilization of Current APIs:** Enhances current APIs with AI capabilities without fundamental changes.

- **No Downtime Required:** Integrates with current systems without service interruptions.

- **Independent Updates:** Permits isolated updates to the AI layer without affecting the main application.

- **Optional Use:** Provides AI functionalities as an optional layer for users who wish to utilize it.

- **Phased Roll-Out:** Enables controlled, step-wise integration to assess impact and performance.
