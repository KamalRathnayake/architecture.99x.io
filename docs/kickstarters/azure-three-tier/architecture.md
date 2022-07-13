---
id: azure-three-tier-architecture
title: Architecture
---

# Architecture

## Introduction

This architecture designed for a sample To-do application is based on a three-tier architecture pattern consisting of a presentation layer, an application layer and a data layer. Three-tier pattern provides separation of concerns. The front-end, the web application that the user interacts with is the presentation layer. The business logic, the business rules and the communication between the presentation layer and the database belongs to the application layer. The data layer consists of the database.

This architecture is designed to mainly optimize the availability, scalability and security of any application that utilizes this architecture. This sample architecture can be used to implement any scalable and secure application that is highly available. 

The web application is deployed as an Azure Web App and the Azure Active Directory B2C authenticates the users of the application. Azure SQL database is used as the database layer of this architecture. The public access to the database is not allowed but the with the enabled service endpoint, all the resources inside the virtual network will have access to the database. App Service Regional VNet Integration enables the backend and the database of the application to communicate through the virtual network. Azure Bastion service enables secure direct access to the environment and the database.   

The high-level architecture diagram is given below.


## Deployment View

Components
App service, sql server, virtual network, vnet integration, service endpoints

Integrations/Flows
How traffic flows from the app service to the database
Is the database accessible from the public internet?

## Development View
Technologies used for developing
ASP.NET MVC, 

