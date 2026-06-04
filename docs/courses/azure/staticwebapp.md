---
title: Journal in the Cloud
description: A course task that wants to publish the journal to the Azure cloud
---

# Journal, yes, but cloudy

## Cloud Services

In the course [My IT Journal](../mytitjournal/overview/) you built a
zensical-based documentation that is then published as a static website at
GitHub pages. Now we want to publish this website in the Azure Cloud.

!!! hint

    If you did not follow the previous course on Zensical, then you can create a
    small static website built with HTML/Javascript to your liking.

In a public cloud there are hundreds of services that you can consume. Not only
few overlap in terms of application areas but then differ in features and
abstraction level. Running a container can be achieved in many ways with at
least four different services. It only depends on the needs of the workload.
Finding the right tool for the job is one field, where a solution architect must
get proficient.

A good overview of all Azure services grouped by domain is provided by the
[Azure Charts](https://azurecharts.com/directory).

!!! abstract "Task: Identify the right tool to publish your IT journal."

    Use the above mentioned Azure Charts and search for services that let you
    publish static web content. Then choose the one that

    - allows to publish your IT journal
    - has as little monthly cost as possible, ideally CHF 0.-

    Verify your choice with your instructor, if your on the right road, then get
    an overview of the service and try out some tutorials/getting started guides to
    get familiar with the concepts.

??? tip "Hint"

    You are dealing with static web content that only needs to be delivered.
    There is no server side application. No containers involved. Just pure
    HTML/Javascript.
    ??? tip "Solution"
        Azure Static Web Apps is the service of choice.

## Setup using the Azure portal

So, now that you haven chosen the service and visited some documentation and
even did some first steps, it's time to deploy your IT journal!

!!! abstract "Task: Publish the journal"

    Now go ahead and try to publish your IT journal to Azure. Use the portal to
    achieve this goal. Make a documentation of the steps you took.

**Definition of Done**:
Your IT journal is automatically updated every time you make a push to your
main branch either by a direct push or by merging a pull request, which is
actually the same.
