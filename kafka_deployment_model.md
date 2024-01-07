---
layout: home
title: Kafka Deployment Model
author: Kishore Kota
---


### Kafka in Enterprise Environments: Shared vs. Dedicated Infrastructure Models ( WIP )

## Introduction
This document aims to provide a comprehensive comparison of using Apache Kafka in a shared infrastructure model versus a dedicated infrastructure model for each team within an enterprise.

This document strictly limited to Kafka Tenancy Model and Comparision between Multi Tenancy and Dedicated Tenancy model.


## Out of Scope

- Does not cover details around Kafka usecases, usage or deployment architecture.

### Kafka and Multitenancy
Apache Kafka, while not inherently designed for multitenancy, possesses features that make it suitable for such a setup within an enterprise. Multitenancy in Kafka involves a single Kafka cluster being used by different systems or teams.

#### Supporting Features for Multitenancy
1. **Topic Segregation**: Organizes messages into topics for different teams or applications.
2. **Access Control Lists (ACLs)**: Controls access to specific topics.
3. **Quotas**: Sets limits on resource usage for clients or users.
4. **Scalability**: Kafka's distributed nature allows handling increased loads.
5. **Performance Isolation**: Achieved through careful planning and resource allocation.
6. **Monitoring and Logging**: Essential for tracking usage and diagnosing issues.

#### Challenges in Multitenancy
- **Resource Contention**: Risk of one tenant’s usage impacting others.
- **Maintenance and Upgrades**: Complexity in managing without service disruption.
- **Security and Compliance**: Increased challenge in a shared environment.

---

## Kafka as a Shared vs. Dedicated Infrastructure Model

### Shared Infrastructure Model
#### Pros
- Cost Efficiency 
  * Overall capacity needed can be optimized and efficient use of the resources thus providing cost efficiency.
- Easier Maintenance
  * Allows for dedicated enterprise team to manage Kafka Infrastructure. This takes away burden from each and every team trying to manage Kafka on their own.
- Resource Optimization
  * Shared infrastruture has an advantage to limit underutilization of resources compared to having seperate instaces.

#### Cons
- Risk of Resource Contention
   * As the resource limits are not supported by Kakfa deployment model, this is a possible scenario - a specific teams deployment may cause resource exchaustion due to incorect planning or unexpected scenario.  
- Limited Customization
  * Shared infra limits all teams to be on the same Kafka version and limits any customization, or some use cases might be requiring higher or lower replication factor or availability needs being different, etc.
- Potential Security Concerns
  * Does not enforce RBAC at the topic level, this can lead to unauthorized consumption of a topic. Also, these will end up adding as requirement for infrastructure to enforce prior autherization of events as part of consumer onboarding.
- Maintainability
  * Harder to maintain as this model is a monolithic deployment model for proiving eventing capability for an enterprise. As any version upgrades requires large planning and coordination among many different teams, execution of these version upgrades is much harder in this deployment model. 

### Dedicated Infrastructure Model
#### Pros
- Customization
  * Teams have authroity to defined Kafka infrastructure based on the specific availability and realiability needs.
- Enhanced Security
  * Establishes isolation of Kafka between teams thus limiting unautherized access exposure. 
- Performance Reliability
  * Dedicated resource ensure teams are have dedicated capacity for running the workloads.

#### Cons
- Higher Costs
  * Dedicate capacity for each team limits overall resource sharing and needing to provision more resources causing higher operational cost.
- Increased Maintenance Effort
  * Each team would need to have capacity dedicated support and maintain infrastructure associated with Kafka. Managed service approach would limit the cost of operational support, nonetheless this would be a responsibility of Product Team.
- Underutilization of Resources
  * Idel resources will end up with unutilised capacity, using up operational cost regardless of usage.

### Comparative Analysis
Comparison of shared vs. dedicated models in terms of cost, performance, security, scalability, and maintenance.



| Criteria         | Shared Tenancy | Dedicated Tenancy | Notes |
|------------------|---------------------|----------------------|-----------------|
| Cost             |  ✅         |                   | Cost of Infra Structure and Support           |
| Performance  |               | ✅             |             |
| Reliability              | ✅              | ✅             |          |
| Availability | ✅ | ✅  | |
| Security |  | ✅ | |
| Customization | | ✅ | Ability to customize various configuration options.|
| Maintainability| | ✅  ||





### Recommendations
Suggestions based on different enterprise sizes and needs, with decision factors for consideration.

#### Influencing Factors
- If the eventing is used for transaction procerssing, then it requires establishing strict SLAs to support customer journey needs and hence Performance will be a key aspect for Kafka deployment model.

- If the workloads deploying have varying degree of needs, then superceding requirement will play vital role in establishing overall Availability and Reliability needs. One size fits all solution, which will endup over provisioning capacity needs for some of the use cases.

### Conclusion
Summary of key findings and final thoughts.


### Credits
ChatGPT - Some of the information generated/gathered using ChatGPT.
