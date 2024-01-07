---
layout: default
title: Microservices
author: Kishore Kota
---

# Exploring the Depths of Microservices Architecture: Trends, Patterns, and Best Practices (WIP)

## Abstract
This paper delves into the microservices architectural style, a method of developing software systems that emphasizes modular, independently deployable services. We explore its advantages, challenges, and compare it with traditional monolithic architectures, shedding light on its growing relevance in the modern technological landscape. We will talk about various different pattern in micro services and their usage, an ideal choices for building applications with Micro Services.

## 1. Introduction
Microservices architecture, characterized by its fine-grained services and lightweight protocols, has emerged as a pivotal approach in software development. Contrasting sharply with monolithic architecture, it offers enhanced scalability, flexibility, and speed of deployment, catering to the dynamic demands of contemporary businesses. This paper aims to provide a comprehensive understanding of microservices, discussing its patterns, challenges, and impact on organizational structures.


### Key Tenants of Micro Services

- Modularity
- Independent
- Scalability
- Polygot 
- Resilient
- Changeability
- Testability
- 

## 2. Challenges with Micro Services

As with everything, there is never a silver bullet. Micro Services requires a mature development practice and release cycle to be efficient. It requires a good test automation approach like TDD, with supporting CI/CD for moving the code into higher environment and with proper tooling to support for required automation for provisioning, monitoring deployment. 

- When a system is decomposed into multiple different component, it increases the risk of transactionality, requires RPC vs in-process calls, overall complexity of the system increases due to finegrained nature of functionality decomposition.

- Overall system complexity increases when the functionality is broken down to smaller components. A distributed system is much more complex in maintaining and understanding vs a singular system that holds entire logic.

- Establishing domain boundaries and following domain rules and ensuring everyone plays by the rules of the book requires understanding, time, and practice. This can be seen as more of a limitation.

- Release cycle is an easy as you think and in fact this is the hardest part. Why ? One of the value statements with Micro Services is that it reduces overall testing needs for safe deployment. This does not come easy unless teams invest time in establishing proper testing approach for release cycles. I will be covering some of these in Testing section of the article down below.

- Deployment is going to be harder unless there is good tooling done on overall release process. This includes establishing fully automated Pipeline and opinionated pipeline. We will be talking about this in the sections below.

- Availability, Latency and Resiliency – these may not be as easy as it is with traditional system, requires more engineering support. Overall engineering efforts are higher with micro services – these techniques may not lower the cost of the Product delivery, yet this are providing ability to scale when enterprise needs release faster. Initial investment to get there is very expensive, but after achieving maturity organization will reap benefits of the architecture. If Cost is a concern, then moving to micro services may not be a right fit – IMO.

- Finally – dependency management. This is daunting and no silver bullet than trying to establish a process for adjusting priorities and getting alignment.


## Architectural Patterns


Below are the some of the categories in Micro Services from an architectural standpoint. 
- Experience Layer
- Data Aggregation
- Product Capability
- Orchestration 
- Edge Services

### Product Capability Micro Service
- Each capability needs to be built into its own micro service(s). There is no rule saying that – a single product capability needs to be built into a single micro service. It is up to the discretion of the capability needs.
o Let’ssayyouarebuildingsystemtosupportShippingaProductOrder.Shipping Microservice may hold on to the logic for handling shipping process, and if you have complex business rule around deciding which shipping partner is being used, those can go into separate micro service. If you have vendor integration and having respective data transformation, those can go into separate micro service. Depending on the value proposition.
- Key principles of the Product Micro Services are.
o Establishcleardataownership.
o Donotrepresentdatathatisnotownedbyyourdomain,exceptanyreferencedata. o Defineclearboundedcontext.
o Owndataanditslifecycle,ownthedatamodelinanalyticsspaceaswell.
o ProductbehaviorneedtobeagnostictoExperienceLayer.
§ If Mobile channel is allowing an option vs Web not supporting, those will still be product capabilities and need to be built into Product API.
- In this category depending on the needs, your Product Micro Service will be doing these. o DataAggregationfromotherpartsofthesystem.
o CoreProductBusinesslogic.
o DataManagement.


### Experience Layer Micro Service
In most cases Experience Layer will need more data than a Product API offers. This mainly for keeping all the information available for the user in single painted window and provide better user experience than clicking through many links. This is applicable for both End User and / or Internal User.
System supporting experience layer are more like Back End For Front End – BFF. In most cases Experience layer is different between Mobile, Web and Internal User – so maintain respective experience layers make more reasonable and allows for support autonomy between UIs.
Few guiding principles.
- BFF need to be built by team owning UI.
- UI specific logic and requirements needs to be isolated from Product API.
- Having separate BFF for each experience layer provides autonomy and each experience layer
isolation. There might be value is reusing these, but keep in mind reuse might increase testing scope and having separation might be strategic in release process.
Consider using Graph QL.

**Who should be building these?** UI teams should be building these, this allows for autonomy over release process and avoid requirement hand off.

### Data Aggregation Micro Service
You will see these more often than before. There are certainly products available that can allow for API Data Aggregation without having to write code, I do not have much experience with tooling and cannot speak to pro and cos with those. Since we are dealing with system that are decomposed to smaller pieces, realty is that business logic depends on data from different system. SO, data aggregation via calling API will be more common theme between systems in a Micro Services environment. Depending on API integration approach for business process is orchestrated – if an event-based approach is used, that might push some of the Data aggregation responsibility to the system that handles business process.