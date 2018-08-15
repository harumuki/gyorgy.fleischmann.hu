---
layout:   post
title:    ITIL® v3 2011 Foundation
author:   flex
comments: true
category: Knowledge / tudás
tags:     [ITIL]
---

Ha már belefutottam ebbe a témába, akkor gyorsan átemelem ide azt az angol nyelvű cikket ([ITIL: Key Concepts and Summary](https://www.simplilearn.com/itil-key-concepts-and-summary-article)), ami alapján a vizsgára készültem. Az eredeti cikket [Priyadharshini](https://www.simplilearn.com/authors/priyadharshini) írta. 

Nem titkolt szándékom volt akkor már ezen a hosszú cikken csiszolni egy picitkét az oldal mögött lévő CSS3 H* stílusokat. Nem mondom, hogy teljesen elégedett vagyok már az eredménnyel, de egyelőre ez marad.

<!-- break -->

<hr>

# ITIL: Key Concepts and Summary

The ITIL (Information Technology Infrastructure Library) has become the de facto standard in IT Service Management. ITIL helps organizations across industries offer their services in a quality-driven and economical way. The framework’s most recent version, published in 2011, is only a progressive update that further refines an existing body of IT Service best practices.

Whether you’re already on your certification journey or are just researching the field of IT Service, before commencing full-fledged preparation for the ITIL exams, it's helpful to learn the basic concepts and terms of ITIL that will help you gain familiarity with the core components of the exam.

## Some Basics IT Service Management Terminology & Key Concepts

- **Services:** It is a means of delivering value to customers without requiring the customer to own specific costs and risks.
- **Service Management:** It is a set of specialized capabilities for delivering value to customers in the form of services.
- **Service Assets:** Service Assets or assets refer to the ‘resources’ and ‘capabilities’ which a Service Provider must allocate in order to offer a service.
- **Value, Utility and Warranty:** The value of a service consists of two components: utility and warranty. Services must offer both utility and warranty in order to have value. Utility, also called ‘fitness for purpose’, refers to the ability of the service to remove constraints or increase the performance of the customer. Warranty, also called ‘fitness for use’ is the ability of the service to operate reliably.
- **Processes:** Processes are structured sets of activities designed to achieve a specific objective. The four basic characteristics of processes are:
1. They transform inputs into outputs
2. They deliver results to a specific customer or stakeholder
3. They are measurable
4. They are triggered by specific events

- **Functions:** Functions are self-contained subsets of an organization intended to accomplish specific tasks. They usually take the form of a team or group of people and the tools they use.
- **Roles:** Roles are defined collections of specific responsibilities and privileges. Roles may be held by individuals or teams.
- **Resources:** Resources are the raw materials which contribute to a service, such as money, equipment, time, staff etc.
- **Capabilities:** Capabilities are the specialized skills or abilities an organization applies to resources in order to create value.

## The ITIL Service Lifecycle

The entire framework of ITIL is divided into five broad components/categories:

- ITIL Service Strategy
- ITIL Service Design
- ITIL Service Transition
- ITIL Service Operation
- ITIL Continual Service Improvement
 
These components form the skeleton of the ITIL Service Lifecycle.

![ITIL Service Lifecycle](https://d112vpovu2xa8r.cloudfront.net/portal_simplilearn_curatasite_com/media/wIWpnG1eim5vnkf.jpeg "ITIL Service Lifecycle")

## ITIL Key Concepts: Processes, Functions

The five broad components of the ITIL Service Lifecycle cover various other sub-categories/aspects, including Demand Management, Capacity Management, Release Management, Incident Management, Event Management, and so on. These are aspects that are meant to cover all areas of ITSM (IT Service Management).

Each of the sub-categories/aspects of the five components of the ITIL framework may be labelled either as a ‘Process’ or as a ‘Function’.

Here’s a diagram that better explains the sub-categories/aspects of the five broader components, classifying them as either a process or as a function.

![The five broader components](https://d112vpovu2xa8r.cloudfront.net/portal_simplilearn_curatasite_com/media/0ZIeQa9WEJRQw5f.jpeg "The five broader components")

Now on to the five core components of ITIL.

## ITIL Core Component: Service Strategy

The purpose of Service Strategy is to provide a strategy for the service lifecycle. The strategy should be in sync with the customer’s business objectives as well as to manage services, and therein lies its scope. The objective of Service Strategy is, therefore, to provide a definition of strategy and governance control.

The utility and warranty of this component are designed to ensure that the service is fit for purpose and fit for use, respectively. Ensuring this is important as these two components are what add value in the delivery of services to customers.

The **Service Strategy** process is concerned with the development of service concepts in preparation for the selection of services to be provided.

### Service Portfolio Management Process:

The **Service Portfolio** is the entire set of services under management by a Service Provider. It consists of three major parts: **Service Pipeline, Service Catalog and Retired Services**.

The Service Portfolio Management process is concerned with management of services that concern information in the Service Portfolio. Service Portfolio Management organizes the process by which services are identified, described, evaluated, selected, and chartered.

### Demand Management Process:

The Demand Management process is concerned with understanding and influencing customer demand. Demand Management models demand in terms of:

- **User Profiles**, which characterize different typical groups of users for a given service.
- **Patterns of Business Activity**, which represent the way users in different user profiles access a service over the course of a given time period.
 
### Financial Management Process:

IT Financial Management provides a means of understanding and managing costs and opportunities associated with services in financial terms. IT Financial Management includes three basic activities: 
- **Accounting** -- tracking how money is actually spent by a Service Provider
- **Budgeting** – planning how money will be spent by a Service Provider
- **Charging** – securing payment from customers for services provided
 
### Strategy Operations:

Strategy Operations ensure that services like fulfilling user requests, resolving service failures, fixing problems as well as carrying out routine operational tasks, are performed efficiently and effectively.

## ITIL Core Component: Service Design

The **‘Four Ps of Service Design’** represent areas which should be taken into consideration when designing a service. They are:
1. **People** – Human resources and organizational structures required to support the service
2. **Processes** – Service Management Processes required to support the service
3. **Products** – Technology and other infrastructure required to support the service
4. **Partners** – Third parties which offer additional support required to support the service

Processes under Service Design are as follows:

### Service Catalog Management:

The **Service Catalog** is the subset of the Service Portfolio which contains services currently available to customers and users. The Service Catalog is often the only portion of the Service Portfolio visible to customers. The Service Catalog commonly acts as the entry portal for all information services in the live environment.

Service Catalog Management involves management and control of the Service Catalog which contains information about services currently available to customers for use.

### Service Level Management:

**Service Level Management** is the process charged with securing and managing agreements between customers and the service provider regarding the levels of performance (utility) and levels of reliability (warranty) associated with specific services. **Service Level Management** results in the creation of **Service Level Agreements (SLAs)** between customers and the provider.

**Operational Level Agreements (OLAs)** are performance agreements nearly identical in nature to SLAs

### Availability Management:

The **Availability Management** process is concerned with management and achievement of agreed-upon availability requirements as established in Service Level Agreements. In ITIL, availability is defined as the ability of a system, service, or configuration item to perform its function when required.

### Capacity Management:

**Capacity Management** is concerned with ensuring that cost-effective capacity exists at all times which meets or exceeds the needs of the business as established in Service Level Agreements. In ITIL, capacity is defined as the maximum throughput a service, system, or device can handle. Capacity Management is divided into three major activities:
- **Business Capacity Management (BCM)**
- **Service Capacity Management (SCM)**
- **Component Capacity Management (CCM)**

### Service Continuity Management:

The IT Service Continuity Management process (ITSCM) is ensures that the IT Service Provider can always provide the minimum, agreed-upon levels of service. IT Service Continuity Management uses techniques such as **Business Impact Analysis (BIA)** and **Management of Risk (MOR)**. ITSCM results in the production of the IT Service Continuity Plan which is an aspect of the overall **Business Continuity Plan**.

### IT Security Management:

IT Security Management focuses on protection of five basic qualities of information assets:
**Confidentiality** – Assurance that the asset is only available to appropriate parties
**Integrity** - Assurance that the asset has not been modified by unauthorized parties
**Availability** - Assurance that the asset may be utilized when required
**Authenticity** - Assurance that the transactions and the identities of parties to transactions are genuine **Non-Repudiation** -- Assurance that transactions, once completed, may not be reversed without approval

### Supplier Management:

**Supplier Management** is the process charged with obtaining value for money from third-party suppliers. Supplier Management plays a very similar role to that of Service Level Management, but with respect to external suppliers rather than internal suppliers and internal/external customers. Supplier Management handles supplier evaluation, contract negotiations, performance reviews, renewals and terminations.

## ITIL Core Component: Service Transition

The objective of the Service Transition process is to build and deploy IT services by also making sure that changes to services and Service Management processes are carried out in a coordinated way.

In this phase of the lifecycle, the design is built, tested and moved into production to enable the business customer achieve the desired value. This phase addresses managing changes: controlling the assets and configuration items (the underlying components such as hardware, software, etc.) associated with the new and changed systems, service validation, and testing and transition planning to ensure that users, support personnel and the production environment have been prepared for the release to production.

### Change Management:

The objective of this process activity is to control the lifecycle of all the changes. The primary objective of Change Management is to enable beneficial changes to be made with minimum disruption to IT services.

### Change Evaluation:

The objective of the change evaluation process is to assess major changes, like the introduction of a new service or a substantial change to an existing service, before those changes are allowed to proceed to the next phase in their lifecycle.

### Project Management (Transition Planning and Support):

This process is aimed at planning and coordinating use of resources to deploy a major release within the predicted cost, time and quality estimates.

### Application Development:

This makes available the applications and systems which provide the required functionality of IT services. This process includes the development and maintenance of custom applications as well as the customization of products from software vendors.

### Release and Deployment Management:

The objective of this process is to plan, schedule and control the movement of releases to test and live environments. The primary goal of this management activity is to ensure that the integrity of the live environment is protected and that the correct components are released.

### Service Validation and Testing:

This ensures that deployed Releases and the resulting services meet customer expectations, and to verify that IT operations is able to support the new service.

### Service Asset and Configuration Management:

The objective is to maintain information about Configuration Items required to deliver an IT service, including their relationships.

### Knowledge Management:

The objective is to gather, analyze, store and share knowledge and information within an organization. The primary purpose of Knowledge Management is to improve efficiency by reducing the need to rediscover knowledge.

## ITIL Core Component: Service Operation

### Event Management:
The objective is to make sure CIs and services are constantly monitored, and to filter and categorize Events in order to decide on appropriate actions.

### Incident Management:

The objective is to manage the lifecycle of all Incidents. The primary objective of Incident Management is to return the IT service to users as quickly as possible.

### Request Fulfilment:

The objective is to fulfill Service Requests, which in most cases are minor Changes (e.g. requests to change a password) or requests for information.

### Access Management:

The objective is to grant authorized users the right to use a service, while preventing access to unauthorized users. The Access Management processes essentially execute policies defined in Information Security Management. Access Management is something also referred to as Rights Management or Identity Management.

### Problem Management:

The process objective is to manage the lifecycle of all Problems. The primary objectives of Problem Management are to prevent Incidents from happening, and to minimize the impact of incidents that cannot be prevented. Proactive Problem Management analyzes Incident Records, and uses data collected by other IT Service Management processes to identify trends or significant Problems.

### IT Operations Control:

The objective is to monitor and control the IT services and their underlying infrastructure. The process objective of IT Operations Control is to execute day-to-day routine tasks related to the operation of infrastructure components and applications. This includes job scheduling, backup and restore activities, print and output management, and routine maintenance.

### Facilities Management:

The process objective is to manage the physical environment where the IT infrastructure is located. Facilities Management includes all aspects of managing the physical environment, for example power and cooling, building access management, and environmental monitoring.

### Application Management:

Application Management is responsible for managing applications throughout their lifecycle.

### Technical Management:

Technical Management provides technical expertise and support for management of the IT infrastructure.

The objective of this is to make sure that IT services are delivered effectively and efficiently. The Service Operation process includes fulfilling user requests, resolving service failures, fixing problems, as well as carrying out routine operational tasks.

Service operation delivers the service on an ongoing basis, overseeing the daily overall health of the service. This includes managing disruptions to service through rapid restoration after incidents; determining the root cause of problems and detecting trends associated with recurring issues; handling daily routine end-user requests; and managing service access.

## ITIL Core Component: Continual Service Improvement (CSI)

The objective of this is to use methods from quality management to learn from past successes and failures. The Continual Service Improvement process aims to continually improve the effectiveness and efficiency of IT processes and services in line with the concept of continual improvement adopted in ISO 2000.

CSI offers a mechanism for the IT organization to measure and improve service levels, the technology,  efficiency and effectiveness of processes used in the overall management of services.

### Service Review:

The objective of Service Review is to review business services and infrastructure services on a regular basis. The aim of this process is to improve service quality where necessary, and to identify more economical ways of providing a service where possible.

### Process Evaluation:

The objective here is to evaluate processes on a regular basis. This includes identifying areas where the targeted process metrics are not reached, and holding regular benchmarking, audits, maturity assessments and reviews.

### CSI Initiatives:

The objective of CSI initiatives is to define specific initiatives aimed at improving services and processes, based on the results of service reviews and process evaluations. The resulting initiatives are either internal initiatives, pursued by the service provider on his/her own behalf, or initiatives which require the customer’s cooperation.

### Monitoring of CSI Initiatives:

The objective is to verify if improvement initiatives are proceeding according to plan, and to introduce corrective measures where necessary.