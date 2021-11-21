---
title: API Gateway vs BFF
---

The goal of having a BFF or API Gateway is to create a sigle point of entry to the system. If we are using an API Gateway the sigle point will be the same for all teh clients. In a BFF case witch client can have a diferent sigle point (BFF).

The BFF makes sense when we have to use diferent communication protocols or if the clients are using different authentication mechanisms
