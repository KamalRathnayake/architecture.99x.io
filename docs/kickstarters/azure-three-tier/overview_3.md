---
id: azure-three-tier-overview-3
title: Overview
---

# Quality attributes

*  Scalability 
    - One million todos per minute.
    - Scaling down when the request is less.
    - Use load balancers and horizontal scaling.

- Availability  
    - Multi region availability.
    - Time to access the todos must be minimal.
    - The data must be redundant.
    - Setup and automate backup data storage.

*  Security 
    - Only the authenticated user must be able to view,edit or delete his/her todos.
    - Setup firewall configuration (VNet /Application gateway firewall).
    - Generate logs for the actions performed by users.
    - Apply data masking to user sensitive data in the database.
    - Avoid exposing unnecsarry resources (database, storage, etc) to public network.


(Nishara, Dilshan)