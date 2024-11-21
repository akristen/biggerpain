---
title: 'Install monitoring for AI'
weight: 2
---

When you instrument your AI apps, you're allowing our agents to collect metrics and event data from AI libraries and frameworks. You'll get started by installing an agent onto your AI-powered app, then finish set-up by making configurations that'll specify how you want the agent to behave.

{{% steps %}}

### Install the agent

Follow our standard install procedures in our [Node.js installation doc](/docs/), then return to this doc to configure your agent.

### Configure the Node.js agent

To collect AI data, you need to set certain configurations to enable monitoring for AI. We recommend applying these configurations in `tsukino.js`, but if you have a more complex set up with multiple environments, you can configure with environment variables.

{{% details title="Configure through `tsukino.js`" %}}

```js
ai_olly.enabled = true
span_events.max_samples_stored = 10000
custom_insights_events.max_samples_stored = 100000
```

{{% /details %}}

{{% details title="Configure with environment variables" %}}

```bash
USAGI_MONITOR_AI_ENABLED = TRUE
```

```bash
USAGI_SPAN_EVENTS_MAX_SAMPLES_STORED = 10000
```

```bash
USAGI_CUSTOM_INSIGHTS_EVENTS_MAX_SAMPLES_STORED = 100000
```

{{% /details %}}

### View your data 

Trigger an event in your system, wait a few minutes, then check the platform for your data. You can find your AI data by going to **afakesite.io > AI monitoring > AI responses.**

{{% /steps %}}
