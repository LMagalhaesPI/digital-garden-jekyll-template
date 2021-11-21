---
title: Feature flag - Internal tool vs third party service!!!
---

What is the best approach to implement a feature flag system? Which of the following three options is the best?

✔️Config file in the project; ([[How to use Microsoft.FeatureManagement to implement feature flag]]) <br/>
✔️Third-Party Service ;([[How to use splitIO to implement feature flag]] and [[How to use Optimizely to implement feature flag]])<br/>
✔️Internal Tool; <br/>

## Config file in the project

 ➕ Manageable by source control;  <br/>
 ➕ Fast to implement;   <br/>
 ➕ Can be included in the CI/CD process; <br/>

 ➖ Require a re-deploy <br/>
 ➖ Depends only on the tech team. <br/>

([[How to use Microsoft.FeatureManagement to implement feature flag]])

## Third-Party Service
 
 ➕ Feature flags can be managed and changed at runtime;<br/>
 ➕ Centralized store;<br/>
 ➕ Admin UI which allows system operators, QAs and product managers to view and modify Features Flags and their configuration; <br/>
 ➕ SDK that can support frontend, backend, and mobile apps;<br/>
 ➕ We can start using it right now;<br/>
 ➕ Fast to implement;<br/>
 ➕ Support of several environments (test);<br/>
 ➕ Best practices because the third party services usually work with several clients;  <br/>

 ➖ Cost;<br/>
 ➖ Not included in the CI/CD process;<br/>

## Internal tool

 ➕ Free;<br/>
 ➕ Adapted to our needs;<br/>
 ➕ Avoid contract lock-in and we have control over all our data;<br/>

 ➖ Needs allocated team to manage and to build (cost + maintenance - indirect costs);<br/>
 ➖ Ressources to scale (indirect costs);<br/>
 ➖ Slower to implement;<br/>

[[Good practices using feature flags]]
[[How to use Optimizely to implement feature flag]]
[[How to use splitIO to implement feature flag]]