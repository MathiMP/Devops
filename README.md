# Devops
This repo is for understanding how to use github actions.

Github action is a CI/CD Platform and automation Platform. You can write workflows to achieve these goals. Workflow files are written as yml files in `.github/workflows` folder. 

The location of your workflow files also matters. For example some triggers demand your workflow files to be in main branch for them to work such as: 
- `workflow_dispatch`
- `scheduled_runs`

Elements in Workflow File:

| Element | Description | Required | Additional Details |
|---------|-------------| ------| -----|
| `name`  | The name of the workflow. This is displayed in the GitHub Actions UI. | No | If no name is given from actions tab you can see the filepath of your workflow file|
| `run-name`  | The name for workflow runs generated from the workflow | No | If not specified then it is set to event specific information of that workflow. example push event will display the commit message as run name|
| `on`    | The events that trigger the workflow. | Yes | Manual trigger,Scheduled Trigger,Events within a repo,Events from outside a repo
| `jobs`  |Jobs to run on a workflow. |Yes| Name of job, Detail of where it shoudl run, steps inside the job. By default runs as parallel
| `steps` | A list of steps to be executed as part of a job. Each step can run a script or an action. |Yes|To define actions that are to be executed. runs in sequence by default.

# Triggers

When the workflow runs depends on trigger
- Defined using `on: `
- You can have single or multiple triggers in a workflow file.
- Not all events can be used as a trigger.
- Some Events only trigger a workflow run if the workflow file exists on the default branch.
 ex: workflow_dispatch or scheduled
- Only few events supports giving inputs to Github Actions
  - `workflow-dispatch`
  - `repository_dispatch`
  - `workflow_call`
- [Few Most used Triggers Explained In Details](.github/workflows/triggers_in_detail.yml)
- To trigger from cli: `gh workflow run workflowfilename.yml`
- [Repository Dispatch](./github/workflows/trigger_repo_dispatch.yaml)


# Jobs
- You can have more than one job in a workflow
- Jobs run parallely by default in github action
- Jobs id: string value. unique identifier of job.
- Jobs Name: string value. Name of job displayed on github UI
- Jobs run in a runner environment specified by `runs-on`
- Jobs can be made to run series by using `needs`
- You can have more than one needs using array.
- Conditional expressions can be used to decide if the steps are to be executed. Example: 'if: ${{ cancelled() }}'
- `runs-on` : single string, array of strings, variable for strings or array of strings,
- `runs-on: ubuntu-latest` : runs the ubuntu-latest
- `runs-on: [ubuntu-22, ubuntu-24]`: will run on image available on the array.
- The type of machine to run the job on .
- Machine can be VM or containers : github-hosted runner, Larger runner, self-hosted runner
- `runs-on: [self-hosted, linux, x64, gpu]`. Self hosted runner on linux os with x64 architecture


# Github Hosted Runners

- Runners are Machines that execute github actions .
- Github Hosted Runners are virtual machines hosted by github
- Machines with more core and gpu processor use larger runner
- Github images have the list of preinstalled tools.
- Included Software link in logs will describe the preinstalled tools on the runner that ran the workflow.
- Ubuntu and windows machine are hosted in azure. macos is hosted in github macos cloud.
- `GITHUB_WORKSPACE` Actions and shell commands execute in this directory
- Some environment variables set by github by default


# Self hosted runner
- Self hosted are images hosted by users
- You can also use images from a group
  example: `runs-on:
      group: ubuntu-runners
      labels: ubuntu-20.04-16core`
- In the above example github action will search for the runner group `ubuntu-runners` and further check for specific runner images with `ubuntu-20.04-16core` label . Once it is available the job will run

# Container 
- You can make your tasks run inside container using container keyword
- `container: node:18` Image used in container.
- Container property must be used at job level
- Container property have refernce to image taht to be used in container


# Steps

- Steps run sequentially by default. Cannot change this behavior
- Step have name, conditional expressions and runs parameter
- Conditional expression helps in authoring when the step should execute when it should not.
