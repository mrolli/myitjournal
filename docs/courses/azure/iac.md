---
title: Infrastructure as Code
description: A course task that wants to publish the journal to the Azure cloud
---

# Infrastructure as Code (IaC)

## Overview

Previously you clicked your way through the Azure portal. This is a manual
process that needs time. To not forget how it was done, it needs to be
documented.

What if we want to setup infrastructure automatically? What we want to setup
twenty resources in parallel? What if things broken and need to be destroyed and
setup in as little time as possible and the exact same way it was previously built?

That's where infrastructure as code comes into play. You describe the
infrastructure you need in code in either declarative or imperative way and let
tooling do the changes needed in the cloud. The code then becomes the
documentation and can be repeatedly run and builds the very same infrastructure
on every run. Ideally, it is idempotent, which means changes only occur in
the cloud when actually something has been changed in the code. Otherwise, no
changes occur on subsequent runs.

Common tools to work with cloud include:

- [Terraform]
- [OpenTofu]
- [Pulumi]

The three are cloud-agnostic, which means they can work on all common clouds.

Besides these, there are cloud-specific tools that work only on one cloud. For
Azure cloud the following tools are provided by Microsoft to automate cloud
resource management:

- [Azure CLI (az)][az]
- [Bicep][bicep]
- [SWA CLI (swa)][swa]
- [Azure Developer CLI (azd)][azd]

[az]: https://learn.microsoft.com/en-us/cli/azure/?view=azure-cli-latest
[bicep]: https://learn.microsoft.com/en-us/azure/azure-resource-manager/bicep/overview?tabs=bicep
[swa]: https://azure.github.io/static-web-apps-cli/
[azd]: https://learn.microsoft.com/en-us/azure/developer/azure-developer-cli/

## Setup with `az`

`az` is the Azure CLI tool. Using this command, you are effectively sending
requests to the Azure API. The following example illustrates the steps needed to
create a resource group in the region Switzerland North:

```bash
az login
az group create --name rg-mygroup-test-CHN --location switzerlandnorth
az group list -o table

```

Almost everything can be done using the command `az`.

!!! abstract "Task: Setup a static web app using `az`"

    Setup another static web app using the tool `az`. To achieve this, create
    simple bash script `setup.sh` in a new subdir `infra/`. This script shall
    then call `az` to crate the static web app. The subcommands and arguments the
    tool needs are well doucmented.

## Deploy with `swa`

Now you have an empty steatic web app running. Next step is to publish your
journal. For this scenario, you shall do it manually from the CLI. You already
know how to generate the website using `zensical`.

There is another nice CLI tool provided by Microsoft to publish the static web
app to Azure, the [Static Web Apps CLI][swa], see also docs in [Azure Static Web
Apps
documentation](https://learn.microsoft.com/en-us/azure/static-web-apps/static-web-apps-cli-overview).

!!! abstract "Task: Publish your journal to Azure using `swa`"

    Install the SWA CLI and then find your deployment key (either via portal or via
    `az`) and deploy the generated website to the newly generated static web app.
