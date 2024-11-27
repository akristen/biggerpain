---
title: 'Portfolio notes~'
description: Here's some context about my portfolio.
---

The site is hosted on Netlify and built with Hugo using the [Hextra theme](https://imfing.github.io/hextra/docs/).

I've curated these docs to capture the four docs types, per [Diátaxis](https://diataxis.fr/map/): conceptual, reference, procedural, and tutorial. I've shortened these docs so they may not reflect the full scope of the live projects.

* All docs were written in VS Code.
* I worked with stakeholders through GitHub using git version control.
* I took product screenshots with SnagIt. To sidestep any conflicts, I've either replaced original screenshots with something more whimsical or removed the images altogether.
* All hyperlinks are deadlinks. I maintained the Markdown to give you a sense of when/how I link to other docs. 

You should poke around [my GitHub account](https://github.com/akristen) if you're curious about how I provide feedback to engineering and product SMEs, or how I might manage sweeping changes to information architecture.

## Learning about LLMs 

In FY24, I supported a major launch that let data scientists and developers monitor their LLM-based apps. Regardless of my personal opinions about AI hype, the experience allowed me to wrestle with a technology that had real industry ambiguity. Our user researcher summed it up well: GenAI is an area where practicioners learn as they do. This held true for me, too. 

I learned alongside my SMEs, and my research quickly moved beyond tech news and forums into the world of academia. I tested my research and ventured guesses about how certain LLM processes might work. To no one's surprise let alone my own, those guesses proved inadequate. But my SMEs were patient and helpful, and I'm a quick learner. Together we pushed out a ton of docs about a completely new feature in a completely new tech space. I can talk with confidence about embeddings, tokenization, vector databases, LLM temperature—the whole gamut.

I've included two docs from this feature release. The first is an introduction doc that covers a mix of observability and AI concepts. The second is an API reference for retrieving certain kinds of LLM data. 

## Untangling the AWS story

tl;dr: You can collect AWS metrics and store them in Company's platform by polling individual API endpoints for each AWS service, or by integrating an agent with an AWS service. Company wanted to position the integration as our primary, recommended method. 

The tricky part is that product still supports the API polling method, so the docs needed to stay live. This resulted in a seemingly random intermixing of procedures across several docs without a clear recommendation about where to start. Docs were littered with callouts for a new integration, but didn't describe value or who should opt in. The area lacked formal logos despite having a real urgency to use the integration.

With this context, I made some decisions:

* I [created a single set up doc](https://docs.newrelic.com/install/aws-cloudwatch/) that functions as a "start here" for anyone wanting AWS data in the platform. The steps are for both first time users and existing users on the polling method. 
* I [updated the intro doc](https://docs.newrelic.com/docs/infrastructure/amazon-integrations/get-started/introduction-aws-integrations/) with clear messaging about what procedures exist and why you'd choose one over the other. I removed all of those bizarre, billboard-y style callouts about the integration across all docs. 
* I [preserved the set up instructions for the API polling method](https://docs.newrelic.com/docs/infrastructure/amazon-integrations/connect/set-up-aws-api-polling/) and grouped that doc with other alternative set-up procedures. (tl;dr Amazon is really complex and there were different procedures if you maintain EC2 instances, use their Kubernetes service, or are a GovCloud customer.)

This project was ad hoc, ambiguous, and really fun. I learned a lot about AWS and got to do some IA restructuring, which is my favorite kind of docs work.

## Going deep with SREs

I created some how-to guides in FY23 to help customers navigate the platform's UI. I wanted these docs to help users think about their data and the platform in a more meaningful way. That is, I wanted to create a story with clear cause and effect rather than a descriptive doc about what each UI component or element did. I kept the story relatively simple for a couple reasons:

* Since app developers primarily use Company's platform, I decided the doc could invite them to think about their data like an SRE, even if that's not a hat they usually wear. 
* If an SRE used the doc, I suspected they could take this basic framework and complexify it to fit their use cases.

These how-to guides gave me plenty of exposure to our field and support teams. While I chatted with product and engineering to get a sense of why they made certain prod decisions, it was important to me that I wrote a story about how our users are actually using the product, rather than how we wanted them to.