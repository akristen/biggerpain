---
title: API reference `record_llm_feedback_event`
weight: 2
description: Record an LLM feedback event so you can correlate end user feedback with an LLM response
---

## Syntax 

```py
    fakefunction.record_llm_feedback_event(trace_id, rating, category=None, message=None, metadata=None)
```

Records custom feedback events for GenAI LLMs. 

## Requirements

Ensure you have your API key and you're using agent version 9.8.0 or higher.

## Description 

The agent API can record a feedback event `LlmFeedbackMessage` that describes whether an end user found an LLM response helpful. The agent API, however, records this data in different places since both events occur in two transactions. This means your function needs to:

1. Capture the trace ID that generates with LLM message (`fakefunction.agent.current_trace_id()`) since the trace ID can connect feedback to LLM rresponse. 
2. Pass that trace ID to the endpoint that records the feedback (`fakefunction.agent.record_llm_feedback_event()`)

## Parameters 

| Parameter    | Description                                                                                                                                                 |
|--------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `trace_id`   | Required. ID of the trace where the chat completion(s) related to the feedback occurred. This ID can be obtained via a call to [`current_trace_id`](). |
| `rating`     | Required. Rating provided by an end user (ex: “Good/Bad”, “1-10”).                                                                                         |
| `category`   | Optional. Category of the feedback provided by the end user (ex: “informative”, “inaccurate”).                                                             |
| `message`    | Optional. Freeform text feedback from an end user.                                                                                                         |
| `metadata`   | Optional. Set of key-value pairs to store any other desired data to submit with the feedback event.                                                        |

## Return values

None.

## Example: Obtain trace ID and record feedback

```py
    import fake.agent

    def get_message(request):
        trace_id = fakefunction.agent.current_trace_id()

    def post_feedback(request):
        fakefunction.agent.record_llm_feedback_event(trace_id=request.trace_id, rating=request.rating, metadata= {"my_key": "my_val"})
```
