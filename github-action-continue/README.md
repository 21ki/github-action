## [continue-on-error](https://docs.github.com/en/actions/learn-github-actions/workflow-syntax-for-github-actions)
## https://newbedev.com/github-actions-check-steps-status
```shell
name: CI
on: [pull_request]
jobs:
  myjob:
    runs-on: ubuntu-latest
    steps:
      - name: Step 1
        id: hello
        run: <any> 
        continue-on-error: true
      - name: Step 2
        id: world
        run: <any> 
        continue-on-error: true
      - name: Check on failures
        if: steps.hello.outcome != 'success' || steps.world.outcome != 'success'
        run: exit 1


name: CI
on: [pull_request]
jobs:
  myjob:
    runs-on: ubuntu-latest
    steps:
      - name: Step 1
        id: hello
        run: echo ::set-output name=status::failure
        continue-on-error: true
      - name: Step 2
        id: world
        run: echo ::set-output name=status::success
        continue-on-error: true
      - name: Dump steps context
        env:
          STEPS_CONTEXT: ${{ toJson(steps) }}
        run: echo "$STEPS_CONTEXT"
      - name: Check on failures
        if: steps.hello.outputs.status == 'failure' || steps.world.outputs.status == 'failure'
        run: exit 1


name: CI
on: [pull_request]
jobs:
  myjob:
    runs-on: ubuntu-latest
    steps:
      - name: Step 1
        id: hello
        run: <any> 
        continue-on-error: true
      - name: Step 2
        id: world
        run: <any> 
        continue-on-error: true
      - name: Check on failures
        if: (${{ success() }} || ${{ failure() }}) && (${{ steps.hello.outcome }} == 'failure' || ${{ steps.world.outcome }} == 'failure')
        run: exit 1
```
