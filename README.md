This repo contains reusable workflows and workflow templates for use in the Mangrove repos.

# About this repo and its peculiar name (`.github`)
The `.github` repo name has special meaning in GitHub, see [Creating starter workflows for your organization](https://docs.github.com/en/actions/using-workflows/creating-starter-workflows-for-your-organization).
In short, it is supposed to contain any organization level files, such as reusable & starter workflows and (optionally) a `README.md` file that is displayed on the organization page.

This repo must be public in order for the other public repos to refer to the workflows in it.

# Reusable workflows and workflow templates
## Reusable workflows
Reusable workflows are located in [.github/workflows](.github/workflows). This location is special and cannot be changed. Also, GitHub does not support organizing this into folders.
We use the following naming convention to make it clear that a workflow is reusable: `reusable-<telling-workflow-name>.yml`.

Reusable workflows must be called by another workflow to run. Thus, to use such a workflow in one of our repos, that repo must contain a wrapper-workflow that calls the reusable workflow.

This wrapper worfklow will be a copy and should therefore be minimal in order to minimize maintenance overhead.

For each reusable workflow, we make such a wrapper workflow in the form of a so-called "workflow template", see the following section.


## Workflow templates
Workflow templates are located in [workflow-templates](workflow-templates). This location is special and cannot be changed. Also, GitHub does not support organizing this into folders.
We use the following naming convention: `<telling-workflow-name>.yml`.

Workflow templates can be copied to our other repos either manually or by going to *Actions -> New workflow* in the target repo and selecting the workflow template in the "By Mangrove" section.

NB: Workflow templates are also called "starter workflows" in the GitHub documentation.


## Secrets at the org level
Many workflows require secrets to work, such as an GPG key for commit signing. Such secrets should be defined at the organization level: https://github.com/organizations/mangrovedao/settings/secrets/actions
This ensures that the secret is available in all our repos.

Please use telling names for secrets to ease maintenance.

Secrets must be passed explicitly from the calling workflow to the reusable workflow. See the existing workflow templates for how to do this.
