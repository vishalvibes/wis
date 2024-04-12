# Web Intelligence Specification (WIS)

The Web Intelligence Specification (WIS) provides a set of guidelines for structuring web applications to improve interaction with AI agents.

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


The WIS approach effectively decouples the AI's understanding and language processing capabilities from the application's logic and data. By doing so, it allows developers to build AI-friendly web services without tailoring them to a specific AI’s capabilities.

The /features endpoint serves as a discovery mechanism for AI to ascertain what the service can do, while the /ask endpoint provides a way for AI to engage with those features using natural language.
