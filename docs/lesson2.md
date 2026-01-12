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