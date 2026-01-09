# Introduction

This repository contains learning snapshot for Artillery and it is presented as part of [Video Geeks YouTube Channel](https://www.youtube.com/@VideoGeeksNet). Please read through all the README files in this repository. Also, watch the Video Geeks YouTube channel for video lectures.

# What is Artillery ?

Artillery is a modern load testing tool built for simulation of continuous load. Artillery can do the following:

- API Testing
- Full Browser Testing
- Playwright Integration
- Production level load testing
- No need to maintain load testing infra.


# Playwright E2E Testing !

Playwright test can be integrated with Artillery Cloud to provide reprting dashboard, tools for reporting and collaboration, etc.

- A central dashboard for your Team's Playwright test reports.
- Realtime streaming for test results of performance tests.
- Automatic tracking of [web vitals](https://web.dev/articles/vitals)
- Github Actions / Gitlab CI-CD Integrations
- AI Assistant
- Notes and comments on test results
- Sharable URLs

# Setup Artillery CLI

Artillery is available on `npm` and you can use below command to install it.

```
> npm install -g artillery@latest
```

If it's not working, try without `-g` flag. Basically, that flag installs it globally. You can run the artillery CLI with `npx` as follow

```
> npx artillery@latest
```

You can check the installation is successfull by running following command:

```
> npx artillery dino
```

## Configure Repository

You can use below commands to set-up github / gitlab remote repository.

```
> git init
> git remote add origin <remote-repo-link>
> git add .
> git commit -m <relevant-message>
> git push
```

## If you're clonig this ?

If you're clonig or forking this repository then you can use below commands after clone.

```
> npm install
```

# Run your first test!

We'll load test the API that is running on Artillery's website which returns ascii pictures of things at `http://asciiart.artillery.io:8080 `.

- `config` is what defines how our load test will run, e.g. the URL of the system we’re testing, how much load will be generated, any plugins we want to use, and so on.

- `scenarios` is where we define what the virtual users created by Artillery will do. A scenario is usually a sequence of steps that describes a user session in the app.

- You can use the following command to run the test.

```
npx artillery run <file-path>
```

- You can use the following command to record the test on WebUI.

```
npx artillery run <file-path> --record --key <api-key>
```

More information [here](https://www.artillery.io/docs/get-started/first-test).