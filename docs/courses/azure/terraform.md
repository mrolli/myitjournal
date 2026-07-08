---
title: IaC with Terraform
description: A course task that wants to publish the journal to the Azure cloud
---

# IaC with Terraform

## Introduction to Terraform

The first link is a short course on Microsoft Learn and will give you an
overview of Terraform - the big picture. Afterwards, work with the Fundamentals
Lab to have a hands-on experience with Terraform on Azure. Core concepts will be
highlighted here.

- [Fundamentals of Terraform on Azure][course-tf-intro]
- [Terraform on Azure Fundamentals Lab][tf-on-azure-lab]

!!! success Learning Objectives

    - You can describe the concept of IaC and HCL.
    - You can describe the cycle `terrform init -> terraform plan -> terraform apply`
    - You can describe the concept of Terraform state.
    - You can describe when and why remote state is crucial.

## Azure Verified Modules (AVM)

Microsoft is creating Terraform Module for the Azure cloud. The intention here
is to provide reusable modules for standard components like storage account, key
vaults and other resources but also for bigger patterns like landing zones.L
These are the so called Azure Verified Modules (AVM).  
The following links shall help give and overview about the what, the how and the
why. The solution course is hands-on course and shows the journey from empty
green field to a fully features and safe solution that could go into production.

- [Azure Verified Modules][avm]: Overview with introduction video
- [AVM Quickstart][avm-quickstart]: Quickstart Lab setting up a Key Vault with
  Terraform (or Bicep)
- [AVM Solution Development][avm-solution]: Deploying a whole solution with Terraform
  (or Bicep)

[course-tf-intro]: https://learn.microsoft.com/en-us/training/paths/terraform-fundamentals/
[tf-on-azure-lab]: https://azure-samples.github.io/terraform-fundamentals-labs/
[avm]: https://azure.github.io/Azure-Verified-Modules/
[avm-quickstart]: https://azure.github.io/Azure-Verified-Modules/usage/quickstart/terraform/
[avm-solution]: https://azure.github.io/Azure-Verified-Modules/usage/solution-development/terraform/

!!! success Learning Objectives

    - You can explain the goals of AVM.
    - You can give an overview of what type of modules for which languages exist.
    - You can explain the common features of the modules.
    - You can describe the compoments of the solution you built and why they are setup.
    - You can describe the concept of Bastion.
