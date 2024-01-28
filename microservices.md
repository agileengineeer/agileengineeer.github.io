---
layout: default
title: Microservices
author: Kishore Kota
nav_order: 7
---

# Exploring the Depths of Microservices Architecture: Trends, Patterns, and Best Practices (WIP)

## Abstract
This paper delves into the microservices architectural style, a method of developing software systems that emphasizes modular, independently deployable services. We explore its advantages, challenges, and compare it with traditional monolithic architectures, shedding light on its growing relevance in the modern technological landscape. We will talk about various different patterns in microservices and their usage, an ideal choices for building applications with Microservices.

## 1. Introduction
Microservices architecture, characterized by its fine-grained services and lightweight protocols, has emerged as a pivotal approach in software development. Contrasting sharply with monolithic architecture, it offers enhanced scalability, flexibility, and speed of deployment, catering to the dynamic demands of contemporary businesses. This paper aims to provide a comprehensive understanding of microservices, discussing its patterns, challenges, and impact on organizational structures.

### Key Tenets of Microservices

- Modularity
- Independence
- Scalability
- Polyglot 
- Resilience
- Changeability
- Testability

## 2. Challenges with Microservices

As with everything, there is never a silver bullet. Microservices require a mature development practice and release cycle to be efficient. They require a robust test automation approach like TDD, with supporting CI/CD for moving the code into a higher environment, and proper tooling to support the required automation for provisioning, monitoring, and deployment. 

- When a system is decomposed into multiple different components, it increases the risk of transactionality, requires RPC vs in-process calls, and the overall complexity of the system increases due to the fine-grained nature of functionality decomposition.

- Overall system complexity increases when the functionality is broken down into smaller components. A distributed system is much more complex in maintaining and understanding compared to a singular system that holds the entire logic.

- Establishing domain boundaries and following domain rules, and ensuring everyone plays by the rules of the book requires understanding, time, and practice. This can be seen as more of a limitation.

- The release cycle is not as easy as you might think and, in fact, this is the hardest part. Why? One of the value statements with Microservices is that it reduces overall testing needs for safe deployment. This does not come easy unless teams invest time in establishing a proper testing approach for release cycles. I will be covering some of these in the Testing section of the article below.

- Deployment is going to be harder unless there is good tooling done on the overall release process. This includes establishing a fully automated Pipeline and opinionated pipeline. We will be talking about this in the sections below.

- Availability, Latency, and Resiliency – these may not be as easy as it is with traditional systems and require more engineering support. Overall engineering efforts are higher with microservices – these techniques may not lower the cost of product delivery, yet they provide the ability to scale when an enterprise needs to release faster. The initial investment to get there is very expensive, but after achieving maturity, the organization will reap the benefits of the architecture. If the cost is a concern, then moving to microservices may not be the right fit – in my opinion.

- Finally – dependency management. This is daunting and there's no silver bullet other than trying to establish a process for adjusting priorities and getting alignment.

## Architectural Patterns in Microservices

Below are some of the categories in Microservices from an architectural standpoint. 
- Experience Layer
- Data Aggregation
- Product API
- Orchestration 
- Edge Services

### Product API Microservice
- Each capability needs to be built into its own microservice(s). There is no rule saying that – a single product capability needs to be built into a single microservice. It is up to the discretion of the capability needs.
- Key principles of the Product Microservices are:
  - Establish clear data ownership.
  - Do not represent data that is not owned by your domain, except for any reference data. 
  - Define a clear bounded context.
  - Own data and its life cycle, own the data model in the analytics space as well.
  - Product behavior needs to be agnostic to the Experience Layer.
  - In this category, depending on the needs, your Product Micro Service will be doing these:
    - Data Aggregation from other parts of the system.
    - Core Product Business logic.
    - Data Management.

### Experience Layer Microservice
In most cases, the Experience Layer will need more data than a Product API offers. This is mainly for keeping all the information available for the user in a single painted window and provide a better user experience than clicking through many links. This is applicable for both End Users and/or Internal Users.
Systems supporting the experience layer are more like Back End For Front End – BFF. In most cases, the Experience layer is different between Mobile, Web, and Internal User – so maintaining respective experience layers make more sense and allows for support autonomy between UIs.
Few guiding principles:
- BFF needs to be built by the team owning the UI.
- UI-specific logic and requirements need to be isolated from the Product API.
- Having a separate BFF for each experience layer provides autonomy and isolation for each experience layer. There might be value in reusing these, but keep in mind reuse might increase the testing scope and having separation might be strategic in the release process.
- Consider using GraphQL.

**Who should be building these?** UI teams should be building these, this allows for autonomy over the release process and avoids requirement hand-offs.

### Data Aggregation Microservice
You will see these more often than before. There are certainly products available that can allow for API Data Aggregation without having to write code, I do not have much experience with tooling and cannot speak to the pros and cons of those. Since we are dealing with systems that are decomposed into smaller pieces, the reality is that business logic depends on data from different systems. So, data aggregation via calling API will be a more common theme between systems in a Micro Services environment. Depending on the API integration approach, if an event-based approach is used, that might push some of the Data aggregation responsibility to the system that handles the business process.
