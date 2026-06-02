---
title: Overview
description: A gentle introduction to the Azure Cloud
---

# Beginning Azure Cloud

In this course you will explore the Microsoft Azure Cloud.

## Introduction

The following resources shall give you a first impression of the Azure Cloud and
an introduction to the Azure Portal.

- Take the [quick tour of Azure](https://azure.microsoft.com/en-us/get-started/)
- Then [get started in the Azure Portal](https://azure.microsoft.com/en-us/get-started/on-demand/)

There is [small documentation](https://knowit.unibe.ch/de/docs/cloud/azure) that
the IT Office at the University of Bern is maintaining that you can visit. The
introduction page and the chapter [Azure
Services](https://knowit.unibe.ch/de/docs/cloud/azure) might be of interest. The
latter showcases some important Azure Services and provides a lot of Links to
documentation, learning material and examples.

## Work Instructions

### Portal Settings

To familiarise with portal, go and adjust some settings:

!!! abstract "Task: Change preferences"

    - Go and inspect your portal settings
    - Change GUI language to English
    - Change layout to "Expanded" for the service behaviour
    - Set the theme to your liking

### Cost Management

We created a resource group for your first deployment task: `rg-<firstname>-journal-test`.

As a first task, you want to make sure that you get an alert, when the resources
you created cost too much. It's a good habit to have a budget setup on a
subscription or a resource group.

!!! abstract "Task: Create a budget"

    - Go to the [Azure Portal](https://porta.azure.com)
    - Navigate to your resources group
    - Create a new monthly budget that...
        - has a budget of CHF 10.-
        - alert you by mail when 50% is actually spent
        - alert you when it is forseen that 90% will be spent

## Documentation

- [Azure portal](https://learn.microsoft.com/en-us/azure/azure-portal/)

## Learning Objectives

- You can navigate the Azure Portal
- You can setup a budget on a resource group (or subscription)
- You know the portal settings
