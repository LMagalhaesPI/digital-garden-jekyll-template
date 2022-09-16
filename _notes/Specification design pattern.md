---
title: Specification design pattern
---

Specification design patten anwser the question where to put place querying, sorting, and paging logic in a Domain-Drive-Design solution. 
The repository methods will be able to receive a specification and produce the expected result given the specificcation. 
This way you have a name in the specification (instead of a LINQ query) and it can be unit tested and reused. 


## Unit of work 


[[Unit Of Work]]