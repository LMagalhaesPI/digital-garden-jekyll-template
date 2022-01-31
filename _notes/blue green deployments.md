---
title: Blue Green deployments❓❓
---

Blue Green deployment is a deployment strategy that uses two identical environments, both similar, running in parallel in production and sharing the same database. Blue will be is live and green a staging service. When deploying a new release we should release first the Green service, then test everything and turn all the production traffic to this environment using a load balancer. Once it's proved that the Green service is running properly without bugs or problems the deployment is done to the blue service and we change again the service running in production to be the blue one.

👌 Advantages:
✔️ Rollbacks: If anything goes wrong it can be detected in an upstream faze and it never reaches production or affects the final user;
✔️ CI/CD strategy: No downtime needed or no need to wait for the best time to do the deployment because it is transparent for the final user;
✔️ Test in the production environment;

⛔ What can be an issue:
✔️ Code compatibility: running two versions of the applications in parallel and management of the databases. To prevent problems we can use a data migration startegy. 
