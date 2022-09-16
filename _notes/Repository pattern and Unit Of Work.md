---
title: Repository pattern and Unit Of Work
---

Unit of work is related with the Repostoy pattern. 

## Repository pattern 

We are isolating all the possible operations to a specific entity in a class. We can have one repostoty per entity or a generic repository. This way we can change our database technology without impact in the application. We will have impact just in the data layer.  

## Unit of work

Unit of work will ensure that all the operations (insert^/update/delete) performed in a user action will be executed under the same transaction rather than doing multiple transactions. 


[[Specification design pattern]]