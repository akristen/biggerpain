---
title: 'Portfolio notes~'
weight: 1
---

The site is hosted by Netlify and built on Hugo with the [Hextra theme](https://imfing.github.io/hextra/docs/). I've added shortcode to display my resume as PDF and made some CSS changes for style.  

I've curated these docs to capture different docs types, per [Diataxis](https://diataxis.fr/map/): conceptual, procedural, reference, and tutorial. 

* All docs were written in VS Code.
* I collaborated with stakeholders through GitHub using git version control.
* I took product screenshots with SnagIt. To avoid conflicts of interest, I've removed the original images and replaced them with something more whimsical.

I recommend [checking out my GitHub account](https://github.com/akristen) if you're curious about how I provide feedback to engineering and product SMEs, or how I might manage sweeping changes to information architecture.

## Untangling the AWS story

tl;dr: You can collect AWS metrics and store them in Company's platform by polling individual API endpoints for each AWS service, or by integrating an agent with an AWS service. Company wanted to position the integration as our primary, recommended method. 

The tricky part is that product still supports the API polling method, so the docs needed to stay live. This resulted in a seemingly random intermixing of procedures across several docs without a clear recommendation about where to start. Docs were littered with callouts for a new integration, but didn't describe value or who should opt in. The area lacked formal logos despite having a real urgency to use the integration.

With this context, I made some decisions:

* I [created a single set up doc](https://docs.newrelic.com/install/aws-cloudwatch/) that functions as a "start here" for anyone wanting AWS data in the platform. The steps are for both first time users and existing users on the polling method. 
* I [updated the intro doc](https://docs.newrelic.com/docs/infrastructure/amazon-integrations/get-started/introduction-aws-integrations/) with clear messaging about what procedures exist and why you'd choose one over the other. I removed all of those bizarre, billboard-y style callouts about the integration across all docs. 
* I [preserved the set up instructions for the API polling method](https://docs.newrelic.com/docs/infrastructure/amazon-integrations/connect/set-up-aws-api-polling/) and grouped that doc with other alternative set-up procedures. (tl;dr Amazon is really complex and there were different procedures if you maintain EC2 instances, use their Kubernetes service, or are a GovCloud customer.)

This project was ad hoc, ambiguous, and really fun. I learned a lot about AWS and got to do some IA restructuring, which is my favorite kind of docs work.

## Learning about genAI 

There's a lot I could say about my one year journey supporting a feature for genAI-powered apps (hereby AI apps going forward, for brevity).

From a professional POV, the project gave me real hands on experience working on a feature with industry ambiguity. Our user researcher described it well: GenAI is an area where practicioners learn as they do. I found myself learning alongside my SMEs while relying on academic research and tech news to fill in the blanks. I ventured lots of guesses about how embedding, tokenization, or various models might work, and those guesses were often inelegant at best. My SMEs were patient and ran the gamut of all possible tech roles: software architects, PMs, field folks, engineers, designers, you name it.

All of this, and I still needed to understand what our feature did and who our audience was.

The doc I've provided is an introduction doc that covers a mix of observability and AI concepts. Despite my reservations about AI, this project was a labor of love! I recommend [exploring the entire area for all of the docs work I did in a few months](https://docs.newrelic.com/docs/ai-monitoring/intro-to-ai-monitoring/).

## Going deep with SREs

Even though Company offered some infrastructure solutions, they're primarily known as being app monitoring-forward. As an associate writer, I didn't fully appreciate what this meant or how a docs site might expose a product's strengths and weaknesses. 