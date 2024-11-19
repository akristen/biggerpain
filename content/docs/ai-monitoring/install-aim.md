---
title: 'Install monitoring for AI'
weight: 2
---

When you install AI monitoring, you're allowing our APM agents to collect metrics and event data from AI libraries and frameworks. To get started, you'll instrument your AI-powered app with an APM agent, then update configurations to adjust the agent's behavior.

{{% steps %}}

### Install the agent

Follow our standard install procedures in our [Node.js installation doc](/docs/), then return to this doc to configure your agent.

### Configure the Node.js agent

To collect AI data, you need to set certain configurations to enable AI monitoring. We recommend applying these configurations in `newrelic.js`, but if you have a more complex set up with multiple environments, you can configure with environment variables.

{{% details title="Configure through `newrelic.js`" %}}

```js
ai_monitoring.enabled = true
span_events.max_samples_stored = 10000
custom_insights_events.max_samples_stored = 100000
```

{{% /details %}}

{{% details title="Configure with environment variables" %}}

```bash
NEW_RELIC_AI_MONITORING_ENABLED = TRUE
```

```bash
NEW_RELIC_SPAN_EVENTS_MAX_SAMPLES_STORED = 10000
```

```bash
NEW_RELIC_CUSTOM_INSIGHTS_EVENTS_MAX_SAMPLES_STORED = 100000
```

{{% /details %}}

### View your data 

Trigger an event in your system, wait a few minutes, then check New Relic for your data. You can find your AI data by going to one.newrelic.com > AI monitoring > AI responses.

{{% /steps %}}
