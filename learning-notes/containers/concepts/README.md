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

