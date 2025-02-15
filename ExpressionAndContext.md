# Expression

Syntax for expression: `${{ }}`
Used to
- To access context
- Combine with Operators
- To set environment variables

### GitHub Actions includes a collection of variables called contexts and  default variables.

# Context

- Context Used to get information in workflows
- Context are objects with properties
    - github context :  
           information about the workflow run and the event that triggered the run. 
    - env context :
          Environment variable set in workflow file is accessible in this env context.
          Environment variable that are part of runner's environment is not included in env context  
          An environment variable defined in a step will override job and workflow environment variables with the same name, while the step executes.
    - vars context
          Configuration variable set at repository, environment or org are avaiable using var context
          Set Your repository variable from repo settings. Secrets and variables section
          This variable is accessible using vars context
    - job
          Contains information of job
          use job.Status to control execution of steps inside the job
    - jobs
          Only in reusable workflow      
    - steps
          Contains information of each step inside a job with a step id
    - runner
          Contains information of runner in the current job
    - secrets
           GITHUB_TOKEN is a secret that is automatically created for every workflow run, and is always included in the secrets context
    - strategy
           matrix strategy information is in this context
           Changes for each job in workflow run
           Accessible for each job and step
    - matrix
    - needs
    - inputs
- Access context information using one of two syntaxes.
    - Index syntax: `github['sha']`
    - Property dereference syntax: `github.sha`
    - Non existent property resolves to empty string

- Why?  Environment variables exist only on the runner. Contexts are available before the job is routed to a runner for execution; this allows you to use a context with the conditional if keyword to determine whether a step should run
 