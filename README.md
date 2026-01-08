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