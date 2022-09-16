---
title: Quality gates to have continuos integration and continuos deploy! 
---
In a CD/CI process, to accelerate the deployment process without human intervention such that the failed tests/stages will prevent a bad build from getting deployed to production. Furthermore, our solution should support the below requirements:

- Release candidates should be finalized based on automated quality gates;

- Qualified release candidates should be auto-deployed to production and should have required post-deployment monitoring

Quality gates to be implemented:
- SonarCloud runs static code analysis
- Unit testing
- Integration tests
- Limit of errors from AWS??? (dev/qa, health check, right now we don't have the feedback to the pipeline. dl queue)
- performace tests 
- Tests in prod (monotoring and alerts)

