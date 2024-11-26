---
title: 'Intro to monitoring for GenAI'
weight: 1
description: Improve your GenAI apps.
---

Monitoring for AI is our solution for application monitoring (APM) for LLM-based apps. When you enable monitoring for AI, our agents can give you end-to-end visibility into performance, cost, and quality of your OpenAI or BedRock models. You can explore how users interact with an AI assistant, dig into trace-level details about a model's response to an AI event, and compare the performance of different models across app environments. 

## How does monitoring for AI work?

To get started with monitoring for AI, you'll instrument your LLM-powered app with one of our APM agents. Once you've instrumented your app, you can enable monitoring for AI so the agent can capture LLM observability data.

When your AI assistant receives a prompt and returns a response, the agent captures metric and event data generated from external LLMs and vector stores. Our agent can:

* Parse information about completion, prompt, and response tokens 
* Track requests and responses that pass through any of our supported models
* Correlate negative or positive feedback about a response from your end users 

You can access all this information and more from the platform, then create alerts and dashboards to help you effectively manage your AI data and improve performance.

## Improve your LLM app performance

Monitoring for AI can help you answer critical questions about AI app performance: are your end users waiting too long for a response? Is there a recent spike in token usage? Are there patterns of negative user feedback around certain topics? With monitoring for AI, you can see data specific to the AI-layer:

* [Identify errors in specific prompt and response interactions]() from the response table. If you're looking to make improvements to your AI models, [learn how to analyze your model with trace-level data]().
* If you're using different models across app environments, you can [compare the cost and performance of your apps before deploying]().
* Are you concerned about data compliance? [Learn how to create drop filters]() to drop sensitive data before you send it to the platform.

Monitoring for AI allows agents to recognize and capture AI data. Monitoring for AI has different library compatibility requirements depending on what language you used for your LLM-powered app.

## Compatibility and requirements 

Monitoring for AI has different library and compatibility requirements depending on what language you used for your LLM-powered app. 

* When you disable distributed tracing or enable high security mode, the agent won't capture AI data.
* You shouldn't enable monitoring for AI if you're a [FedRAMP customer](), because AI and AI-based technologies are not yet FedRAMP authorized.

### Compatible AI libraries 

| Agent version                                                                 | Supported libraries                                                                                                                                                         |
|-------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [Go version 3.31.0 and above]() | * [Go OpenAI library]() versions 1.19.4 and above<br> * [AWS SDK for Go v2]() versions 1.6.0 and above |
| [Java version 8.12.0 and above]() | * [AWS SDK for Java v2 Bedrock Runtime Client] versions 2.20.157 and above                                                       |
| [.NET version 10.23.0 and above]() | * [AWS Bedrock] version 3.7.200 and above                                                                                  |
| [Node.js version 11.13.0 and above]() | * [OpenAI Node.js API library]() versions 4.0.0 and above. If your model uses streaming, the Node.js agent supports versions 4.12.2 and above<br> * [AWS SDK for JavaScript BedrockRuntime Client]() versions 3.474.0 and above<br> * [LangChain.js]() versions 0.1.17 and above |
| [Python version 9.8.0 and above]() | * [OpenAI]() library versions 0.28.0 and above.<br> * [Boto3 AWS SDK for Python] versions 1.28.57 and above.<br> * [LangChain]() versions 0.1.0 and above. |
| [Ruby version 9.8.0 and above]() | * [OpenAI gem]() version 3.4.0 and above                                                                                             |

### Monitoring at scale with NVIDIA NIM

Monitoring for AI can integrate with and collect data about any models supported by NVIDIA NIM. For example, if you've built a Python or Node.js AI app that uses llama3, mistralai, or one of NVIDIA's proprietary LLMs, you can instrument those apps with monitoring for AI and view performance data about your apps.

No additional steps are needed to integrate with NVIDIA NIM: you can follow our [manual procedures for installation](), or install [directly through the platform]().

## Get started with monitoring for AI

Ready to get started? Make sure to [confirm that you can instrument your AI library or framework](). You may need to update the agent if you've already instrumented your app.

When you're ready, use our doc to [manually install monitoring for ](). This doc directs you to the relevant procedures for installing an APM agent, then walks you through configuring the agent to capture LLM-specific data.