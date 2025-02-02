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