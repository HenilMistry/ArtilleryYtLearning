# Introduction

This readme file have the information about the lesson 2 for Artilley that has been taught and covered as part of the [Video Geeks Youtube channel](https://www.youtube.com/@VideoGeeksNet).

# Core Concepts

## Hight Level Model

- Artillery puts load on the application by launching or creating virtual users or threads which arrives to use the application in phases.
- We can describe the number of virtual users, how they will be launched, we can define the ramp up time for the virtual users creation, etc.
- We can define the phases that will be used by virtual users to execute their task.
- Each virtual user will go through each phases defined. Virtual users can live until they have not executed all the pahses.
- Once the execution of all the pahses is completed, virtual user is dead or it's liftime complets.

### Virtual Users

- It's a emulation of a real user.
- Definition of real user can be vary like, it can be a person or an API client.
- Each virtual users are independent of each other.
- Each virtual users have it's own TCP connection to the application, and maintain its own cookies and other data.

### Load Phases

- A load phases tells Artillery about how many vu (virtual users) to create over a period of time.
- A production level load test should have multiple phases like, A warnup phase, Heavy load phase, spike phase, etc..

## Test Lifecycle

- Artillery start by first phase.
- It will launch the number of VUs every second as per the phase specifications.
- Artillery will then move to another phase until there are none.
- Artillery does not wait for the VUs created by one phase to finish before starting the next phase.
- Test ends when all the VUs finish their execution.
- The duration of load test is the amount of time it takes for all the VUs created by the load phase to finish their scenarios. **This can be longer than the combined duration of load phases**.

# Plugins in Artillery

## Overview

- Artillery has suppport for plugins which adds functionality to built in features.
- Plugins are distributed as `npm` packages.
- Plugins are named with an `artillery-plugin-` prefixes.

## Installing a Plugin

- You can install an artillery plugin just as normal as installing any other npm packages.

```
npm install artillery-plugin-<name>
```

- If artillery is installed, plugins must be installed already.

## Using a Plugin

- Plugin needs to be explicitly loaded in the test script via `config.plugins`

- For e.g. If you want to use a plugin named `example` then you must use the following:

```
config:
    target: <url-endpoint>
    plugins:
        example: {}
```

- Note: There is no such plugin named `example`. It's just for explaining.

- This means that artillery will try to load the plugin named `artillery-plugin-example`.

- Each plugin may have or may not have the configurable options.

## Plugins Examples

- We'll explain about Expect Plugin here.
- For more, please go through [official docs](https://www.artillery.io/docs/reference/extensions).

### Expect Plugin

- Expect plugin adds support for checks and assertion on HTTP Requests to enable functional testing in artillery tests.

- You can enable plugin with defining config.plugins section:

```
config:
    target: <url>
    plugins:
        expect: {}
```

- You can add the expectations to HTTP Requests.

```
scenarios:
    - name: Get a movie
      flow: 
        - get:
            url: '/movies'
            capture: 
                - json: `$[5].title`
                  as: title
            expect:
                - statusCode: 200
                - contentType: json
                - equals: 
                    - 'From Dusk Till Dawn'
                    - '{{ title }}'
```