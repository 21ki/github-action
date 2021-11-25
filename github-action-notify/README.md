#  https://stackoverflow.com/questions/67516571/github-action-triggered-by-success-of-a-different-action
```shell
 on:
   workflow_run:
     workflows: ["Other Workflow Name"]
     types: [completed] #requested

 jobs:
   on-success:
     runs-on: ubuntu-latest
     if: ${{ github.event.workflow_run.conclusion == 'success' }}
     steps:
       - run: echo "First workflow was a success"

   on-failure:
     runs-on: ubuntu-latest
     if: ${{ github.event.workflow_run.conclusion == 'failure' }}
     steps:
       - run: echo "First workflow was a failure"
```
