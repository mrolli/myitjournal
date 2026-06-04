---
title: "Project: Music Dashboard"
description: Build a static web app with persistence to visualize Spotify listening data.
---

# Music Dashboard

A web-based dashboard, similar to stats.fm, should be built to analyse and
visualise personal music data. The project should include the following
features:

- Listening hours per day and week
- Analysis of the most-listened-to songs and artists
- "Song of the week"
- Visualisation of the data in charts
- An optional calendar view

Technically, the app should connect to an external API such as the Spotify API.
Since data is often only available within a limited rolling time window, it should
be fetched periodically using a pull-based approach and stored in a suitable backend.

The project should be implemented as a cloud-native web application and deployed
in Azure either as a static web app or as an App Service.

!!! abstract "Task: Create a system architecture"

    Use a tool of your choice (Mermaid in Markdown? 😉) to create one or more
    diagrams that clearly show what needs to be built. Think about which
    components exist, who talks to whom, which data is exchanged, and where data
    is stored and read from.

For projects that are developed natively in the cloud as a static web app or as
an App Service, Microsoft provides another tool: `azd` (Azure Developer CLI).
This tool combines what you did in the previous exercise with `az` and `swa` in
a single command-line tool. `azd` also uses `swa` internally.

!!! abstract "Task: Install `azd` and get to know the tool"

    Install `azd` and try examples such as the React/MongoDB todo app. Try to
    understand the concepts: How is the infrastructure created? How is the
    application published?

Useful resources for `azd`:

- [Video: How to Deploy to Azure with the Azure Developer CLI](https://www.youtube.com/watch?v=f_HpDpEmWZ4)
- [From code to cloud, in minutes](https://azure.github.io/awesome-azd/)
- [Azure Developer CLI Documentation](https://learn.microsoft.com/en-us/azure/developer/azure-developer-cli/azure-developer-cli-vs-azure-cli)

!!! abstract "Task: Implement the music dashboard"

    There are no strict requirements for the code implementation. Azure resources
    can be either a static web app (Free or Standard) or an App Service. If data
    persistence is needed, Cosmos DB may be used. The total solution must not cost
    more than CHF 30 per month.
