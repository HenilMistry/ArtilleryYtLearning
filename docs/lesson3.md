# Introduction

This readme file have information about the Lesson 3 covered as part of Artillery Playlist on [Video Geeks YouTube Channel](https://www.youtube.com/@VideoGeeksNet).

# What you'll learn

- How to set up GitHub Actions workflow to run your Artillery tests
- How to schedule your Artillery tests to run at a specific time

# Artillery Github Actions

- You need to use the `artilleryio/action-cli@v1`
- Above can be changed. Please check the latest version availability.
- This is taken from official github actions mentioned [here](https://github.com/marketplace/actions/artillery-load-testing-action).
- Artillery Github Actions has Inputs and Outputs that you can mention in workflow file.

## Inputs

### `command`

This Atillery CLI command will run on CI Runner. You can use all the available commands [here](https://www.artillery.io/docs/reference/cli/run).

```
- name: Load test
  uses: artilleryio/action-cli@v1
  with:
    command: run ./preprod.yml
```

### `working-directory`

This is optional parameter. It is path to a directory to use as the current working directory when running Artillery command.

```
- name: Load test
  uses: artilleryio/action-cli@v1
  with:
    command: run ./test.yml
    working-directory: ./packages/app/load-tests
```

## Outputs

You can generate and access test run report using CLI directly.

```
- name: Load tests
  uses: artilleryio/action-cli@v1
  with:
    # Save the test run report at "./report.json"
    command: run ./prod.yml --output ./report.json

- name: Upload artifact
  uses: actions/upload-artifact@v3
  if: always()
  with:
    name: artillery-report
    # Reference the generated report in the file system.
    path: ./report.json
```

More on Running Artillery on Github Actions is [mentioned here](https://www.artillery.io/docs/cicd/github-actions).

# Steps to set-up Github Actions

- Step-1: Write and set-up YAML file which you want to run on CI Runner
- Step-2: Create workflow file.

# Step-1:

- Step-1 is covered in previous videos:
    - [Basic Artillery Stuff](https://youtu.be/3ouI63XoZ_Y?si=X1J_zprAWATuPPlZ)
    - [Plugins and Load Phases](https://youtu.be/1R8jGJKblfw?si=hVo2HYUgF6rjoVVm)

## Step-2:

- Github looks for the configuration file placed inside your code repository at `.github/workflows`.
- The configuration file uses YAML syntax which will trigger your workflow.
- We can set trigger as we desire.
- In this example we will trigger workflow to run after we push new code to the `main` branch of your Github Repository.
- We will also use [official Artillery Github Actions](https://github.com/artilleryio/action-cli).

```
name: Artillery load test on push

on:
  push:
    branch:
      - main

jobs:
  artillery:
    runs-on: ubuntu-latest

  steps:
    - name: Checkout repository
      uses: actions/checkout@v2
    
    - name: Execute load tests
      uses: artilleryio/action-cli@v1
      with:
        command: run test/test-to-run-on-ci.yml --ouput ./report.json

    - name: Upload artifact
      uses: actions/upload-artifact@v3
      if: always()
      with: 
        name: artillery-report
        path: ./report.json
```
