---
id: azure-three-tier-architecture
title: Architecture
---

# Architecture

## Introduction

This architecture designed for a sample To-do application is based on a three-tier architecture pattern consisting of a presentation layer, an application layer and a data layer. Three-tier pattern provides separation of concerns. The front-end, the web application that the user interacts with is the presentation layer. The business logic, the business rules and the communication between the presentation layer and the database belongs to the application layer. The data layer consists of the database.

This architecture is designed to mainly optimize the availability, scalability and security of any application that utilizes this architecture. This sample architecture can be used to implement any scalable and secure application that is highly available.   

The high-level architecture diagram is given below.

![alt text](https://github.com/KamalRathnayake/architecture.99x.io/blob/master/docs/kickstarters/azure-three-tier/Untitled%20Diagram.drawio)


## Deployment View

Components
App service, sql server, virtual network, vnet integration, service endpoints

Integrations/Flows
How traffic flows from the app service to the database
Is the database accessible from the public internet?

## Development View
Technologies used for developing
ASP.NET MVC, 

