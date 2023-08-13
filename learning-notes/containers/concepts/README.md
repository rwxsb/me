## Containers
Containers allow to make software portable, they allow your software to run on variety of systems, including local environment to production.

This benefits in development speed, simplifying automation and ensures that code can run consistently anywhere.

Containers offers same consistency and portability as VMs but in a lightweight fashion.

Containers become very useful when below are considered:
- Portability - consistently run anywhere.
- Isolation - Individual apps are isolated from each other.
- Scaling - Increase or decrease the resources.
- Automation - Automating the process of building and deploying apps can save money.
- Efficiency - Containers are lightweight and fast.

### A brief history of containers
In 1970s Unix introduced the concept of `chroot` which allowed to change the root directory of a process.

In 2000s FreeBSD introduced `jails` which allowed to isolate processes from each other.

In 2008 Google introduced `process containers` which allowed to isolate processes from each other. 

LXC (Linux Containers) was introduced in 2008 which allowed to isolate processes from each other.

The whole need for isolating processes from each other was to allow to run multiple applications on a single host this led to development of containers.


### chroot - change root of a process




## Orchestration

Container orchestration, refers to processes used to manage containers and to automate the management of containers.

An orchestration tool is a tool that handles the constraints the way we manage contianers.

If we want to bring up 5 containers:
- We can manually start a container 5 times.
- We may use an orchestration tool such as kubernetes.

For the purposes of redundancy it is a good idea to run each of these containers in a different host, as the requirements for managing containers get more complex orchestration tools become more useful.

## Zero-Downttime Deployments

1. Start a new container with the new version of the app.
2. Direct traffic to the new container.
3. Stop the old container.

How do we coordiante these steps efficiently? We may use an orchestration tool.

## Use cases

Ways containers and orchestration can benefit us. 

### Microservices

Application architecture that breaks down a single application into a collection of smaller services.

This allows us to build, modify and scale each service independently.

If a service needs more workloads we may easily create more instances of this service with orchestration tools this could be automated.

### Cloud Transformation

Process of migration the existing Infrastructure to the cloud.

Since it is relatively easy to containerize an application, this is a good way to start the process of moving to the cloud. This allows zero-downtime deployment when moving to cloud.

### Automated Scaling

Automatically provisioning resources in response to real-time data metrics.

Without scaling, you must provision enough resources to handle peak traffic at all times, which is inefficient.

With scaling, you can provision resources as needed by detecting - or predicting - increase in usage, then remove those servers when usage returns to normal levels.

Automated scaling depends on ability to spin up new instances quickly and efficiently.

Containers can start much more faster compared to VMs, this makes them ideal for automated scaling.

### Continuous Deployment

Process of deploying new code automatically and frequently.

Instead of doing one big deployment every few months, you can deploy small changes as soon as they are ready.

This allows you to get new features to your users faster, and reduces the risk associatd with big deployments that contains large number of changes.

In order to maintain stability while doing continuous deployment it is important make use of automation to ensure that deployments are stable and consistent.

Containers play a role in this process by providing a consistent environment for your code to run in.

### Self-Healing Applications

Applications that are able to automatically detect and take steps to recovers from failures.

Containers help this since they are able start quickly, however with containers when a container fails it is usually more common to replace this broken container with a brand new one.

Orchestration tools can do this automatically.

### Developer Visibility

With containers container is the development environment, this allows developers to have a better understanding of how their code will run in production.


