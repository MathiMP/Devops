# Devops
This repo is for understanding how to use github actions.

Github action is a CI/CD Platform and automation Platform. You can write workflows to achieve these goals. Workflow files are written as yml files in `.github/workflows` folder. 

The location of your workflow files also matters. For example some triggers demand your workflow files to be in main branch for them to work such as: 
- `workflow_dispatch`
- `scheduled_runs`

Elements in Workflow File:

| Element | Description | Required | Example |
|---------|-------------| ------| -----|
| `name`  | The name of the workflow. This is displayed in the GitHub Actions UI. | No | `name: My WorkFlow`|
| `runs-name`  | The name for workflow runs generated from the workflow | No | `run-name: Deploy by @${{ github.actor }}`|
| `on`    | The events that trigger the workflow. Could be vents from within a repo. From outside a repo,. Manual and sceduled events| Yes |
| `jobs`  | A map of jobs that will be executed as part of the workflow. Each job runs in a fresh instance of the virtual environment. |
| `steps` | A list of steps to be executed as part of a job. Each step can run a script or an action. |
