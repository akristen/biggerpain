---
title: 'Portfolio notes~'
description: Here's some context about my portfolio.
---

The site is hosted by Netlify and built on Hugo with the [Hextra theme](https://imfing.github.io/hextra/docs/). I've added shortcode to display my resume as PDF and made some CSS changes for style.  

I've curated these docs to capture different docs types, per [Diátaxis](https://diataxis.fr/map/): conceptual, procedural, reference, and tutorial. 

* All docs were written in VS Code.
* I collaborated with stakeholders through GitHub using git version control.
* I took product screenshots with SnagIt. To avoid conflicts of interest, I've removed the original images and replaced them with something more whimsical.
* As an additional note, I've removed all hyerplinks but kept the Markdown format to give you a sense of when/how I link to other docs. 

I recommend [checking out my GitHub account](https://github.com/akristen) if you're curious about how I provide feedback to engineering and product SMEs, or how I might manage sweeping changes to information architecture.

## Learning about GenAI 

There's a lot I could say about my one year journey supporting a feature for GenAI-powered apps.

From a professional POV, the project gave me real hands on experience working on a feature with industry ambiguity. Our user researcher described it well: GenAI is an area where practicioners learn as they do. I found myself learning alongside my SMEs while relying on academic research and tech news to fill in the blanks. 

I ventured lots of guesses about how embedding, tokenization, or various models might work, and those guesses proved to be inelegant at best. But my SMEs were patient and together we pushed out a lot of docs content about a completely new feature.

I've included two docs from this feature release. The first is an introduction doc that covers a mix of observability and AI concepts. The second is an API reference for building a function within an agent API to retrieve certain kinds of data from a GenAI-powered app. 

## Untangling the AWS story

tl;dr: You can collect AWS metrics and store them in Company's platform by polling individual API endpoints for each AWS service, or by integrating an agent with an AWS service. Company wanted to position the integration as our primary, recommended method. 

The tricky part is that product still supports the API polling method, so the docs needed to stay live. This resulted in a seemingly random intermixing of procedures across several docs without a clear recommendation about where to start. Docs were littered with callouts for a new integration, but didn't describe value or who should opt in. The area lacked formal logos despite having a real urgency to use the integration.

With this context, I made some decisions:

* I [created a single set up doc](https://docs.newrelic.com/install/aws-cloudwatch/) that functions as a "start here" for anyone wanting AWS data in the platform. The steps are for both first time users and existing users on the polling method. 
* I [updated the intro doc](https://docs.newrelic.com/docs/infrastructure/amazon-integrations/get-started/introduction-aws-integrations/) with clear messaging about what procedures exist and why you'd choose one over the other. I removed all of those bizarre, billboard-y style callouts about the integration across all docs. 
* I [preserved the set up instructions for the API polling method](https://docs.newrelic.com/docs/infrastructure/amazon-integrations/connect/set-up-aws-api-polling/) and grouped that doc with other alternative set-up procedures. (tl;dr Amazon is really complex and there were different procedures if you maintain EC2 instances, use their Kubernetes service, or are a GovCloud customer.)

This project was ad hoc, ambiguous, and really fun. I learned a lot about AWS and got to do some IA restructuring, which is my favorite kind of docs work.

## Going deep with SREs

I created some how to guides in FY23 to help customers navigate the platform's dense UI. Since observability implies a large amount of data coming in about your system, I wanted these docs to help SREs (or whomever) chunk the UI into its relevant parts, then follow the data to identify root cause. I kept the story relatively simple for a couple reasons:

* Since Company's customer base included mostly app developers, I thought a simple story could help them "think like an SRE."
* If an SRE used the doc but had ample experience, I suspected they could take this basic framework for working with host and app data and complexify it to fit their use cases.

These how to guides gave me plenty of exposure to our field and support teams. While I chatted with product and engineering to get a sense of why they made certain usability decisions, it was important to me that I wrote a story about how our users are actually using the product, rather than how we expected them to behave. 
