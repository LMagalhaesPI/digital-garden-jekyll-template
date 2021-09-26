---
title: Feature flag - All you need to know!
---

There is so much information on the internet about feature flags, but when I needed to study it I couldn't find a centralized place with all I needed and most of the information seems to be biases by some tool's brands. In this article I will write will cover the most important topics that we need to take into consideration when we are thinking to adopt a feature flag process:
<br/>

➕ What is a feature flag; <br/>
➕ Why is that good? <br/>
➕ Relevant data to be taken into consideration; <br/>
➕ Best practices; <br/>
➕ Comapration of several tools and options; <br/>
➕ Conclusions; <br/>

## What is a feature flag

Feature Flag, also known as Feature toggle or Feature switch is a process used to enable or disable functionalities remotely without the need to deploy code. It should be easier as toggling it on or off using an interface or editing a config file. The other option is feature branches, re-deploy and go through the code push process. All code changes can be made in the primary branch, and only when the feature is ready it will be enabled via the feature flag.

## Why is that good?

The following points are just the most important advantages that feature flags can bring us:

✔ `Improve CI/CD process`: Feature flagging allows us to continuously deliver and deploy software to their users in a faster way. It brings us the ability to shorten release cycles and get new functionality in the user’s hands quickly and safely. The final benefit is the ability to allow quick learning with `quicker release cycles`. 

✔ `Testing in production`: Because it is impossible to completely simulate the production environment in the QA environments can be useful to have the possibility to release a feature for a small number of users or for a reduced time and test it this way minimizing the risk. It also provides a fast way to do a rollback if necessary via kill switch;

✔ `Canary releases`: Allow a feature to be released for a sub-group of users. It can be useful when we want to release for a small group of users to ensure that the feature is working properly or it’s what the client expects.

✔ `Rollback/kill switch`- If a live issue or bug is discovered in a feature under a feature flag it can be disabled instantly without the need for new code;


✔ `Empower teams`: Using feature flags the teams are less dependent on release processes that can be manipulated by the need to deliver features at a certain time. If we can do it wherever we want and just enable or disable using a toggle we will spend less energy on release processes and more developing the best possible product. It will decouple product and development and keep their schedules in tune.

✔ `Feature gating`: Control features without redeploying and this way reduce the frequency of deploys;

## Relevant data to be taken into consideration:

- How fast is it to implement each toggle and how easy is it to turn off/on it. We can do this associated to our pipeline or completely independently through a user UI or changes in the database. 

- Is it possible to do A/B testing using this approach? ABTesting is a different technology but it can be implemented integrated with feature flags. The truth is that we can turn an ABTesting into a feature Flag.
  
- How to manage several environments.

- How can I use it in my product.
  
- How will we perform it on mobile?

- Cost, resources, maintenance, and all the resource costs.

## Types of feature flags:

- `Release toggles`: They are used to ship to production features not completed tested or partially implemented. The lifetime of this kind of toggles should be reduced by a few weeks.
- `Experimental toggles`: It's a kind of an ABTesting, the feature flag will be enabled/disable taking into consideration the users and the process need to keep tracking of the user's behavior so we can have different code paths. The lifetime of this type depends on the experience and can fluctuate between hours and weeks.
- `Operational toggles`: This kind of toggles and mainly used in featured that can impact the performance of the system. It can be a long-term type of toggle. 
- `Permission toggles`: Enable or disable features for a specific group of users. It can be a long-term type of toggle. 

## Best practices 

☝🏽 Never reuse a feature flag;<br/>
☝🏽 Create a naming convecting to name the feature flags:<br/>
&emsp;&emsp;Feature name;<br/>
&emsp;&emsp;Team name;<br/>
&emsp;&emsp;Service name;<br/>
&emsp;&emsp;Ticket number;<br/>
<br/>
☝🏽 Code reviews or control and audit access to change any feature flag config;<br/>
☝🏽 Users should always have the same experience;<br/>
☝🏽 Observe and adjust;<br/>
☝🏽 Assign an experation data for each flag:<br/>
&emsp;&emsp;Create a task to remove the feature flag;<br/>
&emsp;&emsp;Remove the feature flag and all the code related with it;<br/>

## Comapration of several tools and options:

What is the best approach to implement a feature flag system? Which of the following three options is the best taking into consideration our needs?

✔️Config file in the project; <br/>
✔️Third-Party Service;<br/>
✔️Internal Tool; <br/>

### Config file in the project

 ➕ Manageable by source control;  <br/>
 ➕ Fast to implement;   <br/>
 ➕ Can be included in the CI/CD process; <br/>

 ➖ Require a re-deploy <br/>
 ➖ Depends only on the tech team. <br/>

### Third-Party Service

We can find in the market several options of tools that we can start using in a few minutes. SpritIO and Optimizely are two of the most well known tools.
 
 ➕ Feature flags can be managed and changed at runtime;<br/>
 ➕ Centralized store;<br/>
 ➕ Admin UI which allows system operators, QAs, and product managers to view and modify Features Flags and their configuration; <br/>
 ➕ SDK that can support frontend, backend, and mobile apps;<br/>
 ➕ We can start using it right now;<br/>
 ➕ Fast to implement;<br/>
 ➕ Support of several environments (test);<br/>
 ➕ Best practices because the third party services usually work with several clients;  <br/>

 ➖ Cost;<br/>
 ➖ Not included in the CI/CD process;<br/>

### Internal tool

 ➕ Free;<br/>
 ➕ Adapted to our needs;<br/>
 ➕ Avoid contract lock-in and we have control over all our data;<br/>

 ➖ Needs allocated team to manage and to build (cost + maintenance - indirect costs);<br/>
 ➖ Ressources to scale (indirect costs);<br/>
 ➖ Slower to implement;<br/>

## Conclusion

If you are starting now I think that the best approach is to start with the simple and fast approach and then evaluate to a solution more sophisticated. 

If you are interested in check my demos using different tools check my digital garden:

