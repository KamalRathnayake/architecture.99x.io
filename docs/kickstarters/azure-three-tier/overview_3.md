---
id: azure-three-tier-overview-3
title: Overview
---

# Quality attributes

*  Scalability 
    - One million requests per minute
    - Scaling down when there are less requests
    - Use load balancers and horizontal scaling

- Availability  
    - Multi-region availability
    - Time to fetch data must be minimal
    - The data must be redundant
    - Setup and automate backup data storage

*  Security 
    - Only authenticated users can perform operations within the application
    - Setup firewall configurations (VNet / Application Gateway Firewall)
    - Generate audit logs for user actions
    - Apply data masking for user sensitive data in the database
    - Avoid exposing unnecessary resources (database, storage, etc) to public network


(Nishara, Dilshan)