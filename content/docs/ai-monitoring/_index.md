---
title: 'Intro to monitoring for GenAI'
weight: 1
description: Improve your GenAI apps.
---

Monitoring for AI surfaces LLM-specific data from your app environment, giving you end-to-end visibility into the performance, cost, and quality of your AI apps. When your AI assistant receives a prompt and returns a response, the agent captures metric and event data generated from external LLMs and vector stores. Our agent then:

* Parses information about completion, prompt, and response tokens 
* Tracks trace data for requests and responses that pass through any of our supported models
* Correlates negative or positive feedback about a response from your end users 
* Evaluates and makes comparisons about each model in your model inventory

You can access all this data from the platform, letting you create alerts and dashboards to help you effectively manage your AI data and improve app performance.
## Compatibility and requirements 

Monitoring for AI has different library and compatibility requirements depending on your app environment. 

| Agent version                                                                 | Supported libraries                                                                                                                                                         |
|-------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [Go version 3.31.0 and above]() | * [Go OpenAI library]() versions 1.19.4 and above<br> * [AWS SDK for Go v2]() versions 1.6.0 and above |
| [Java version 8.12.0 and above]() | * [AWS SDK for Java v2 Bedrock Runtime Client]() versions 2.20.157 and above                                                       |
| [.NET version 10.23.0 and above]() | * [AWS Bedrock]() version 3.7.200 and above                                                                                  |
| [Node.js version 11.13.0 and above]() | * [OpenAI Node.js API library]() versions 4.0.0 and above. If your model uses streaming, the Node.js agent supports versions 4.12.2 and above<br> * [AWS SDK for JavaScript BedrockRuntime Client]() versions 3.474.0 and above<br> * [LangChain.js]() versions 0.1.17 and above |
| [Python version 9.8.0 and above]() | * [OpenAI]() library versions 0.28.0 and above.<br> * [Boto3 AWS SDK for Python]() versions 1.28.57 and above.<br> * [LangChain]() versions 0.1.0 and above. |
| [Ruby version 9.8.0 and above]() | * [OpenAI gem]() version 3.4.0 and above                                                                                             |

Keep in mind that: 

* When you disable distributed tracing or enable high security mode, the agent won't capture AI data.
* You shouldn't enable monitoring for AI if you're a [FedRAMP customer](), because AI and AI-based technologies are not yet FedRAMP authorized.

{{< callout emoji="💡" >}}
This feature can collect data about any models supported by NVIDIA NIM, like llama3 or mistralai. No additional steps needed.
{{< /callout >}}

## Get started with monitoring for AI

To get started, follow our procedures to [install monitoring for AI](). This doc directs you to the relevant procedures for installing an APM agent, then asks you to return to complete the necessary configuration. When you're done, learn about some of our features that help you explore your AI data:

* [Identify errors in specific prompt and response interactions]() from the response table. 
* If you’re looking to make improvements to your AI models, [learn how to analyze your model with trace-level data]().
* If you’re using different models across app environments, you can [compare the cost and performance of your apps before deployment]().
* Concerned about data compliance? [Create drop filters to drop sensitive data]() before you send it to the platform.

