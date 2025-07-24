# MSP multi-client capabilities 

The Hornbill Platform offers a specialized set of capabilities within our Enterprise Edition, designed specifically for managed service providers (MSPs) who deliver services to multiple clients. These capabilities cater to complex service models, where multiple clients require individualized services, security, and control over their environments.

For straightforward MSP scenarios, Hornbill’s standard product capabilities allow logical data partitioning for each client, effectively running a shared service management solution. However, this basic model often falls short when an MSP is responsible for managing services across multiple clients with unique requirements. For these more demanding cases, Hornbill’s MSP multi-client capabilities are purpose-built to address the complexities and challenges MSPs face.

## The multi-client deployment model
In Hornbill's multi-client deployment model, both the MSP and their individual clients deploy separate instances of the Hornbill platform and specific Hornbill applications as required by each client's needs. This approach extends functionality significantly; it also introduces a robust security and trust model as well as a subscription model that mirrors the needs of an MSP/multi-client deployment. Each party—MSP and client—retains control over their instance, allowing the MSP to provide services while ensuring clients can meet security, regulatory, and audit obligations. Clients maintain full control over who accesses their systems and data, ensuring transparency and compliance at all times.

![Multi-Client Architecture Diagram](/_books/esp-fundamentals/core-capabilities/images/multi-client-diagram.png)

## Key features of the multi-client deployment model
The following specialized capabilities create a unique architecture tailored to MSPs operating in a multi-client environment:

- __MSP <-> Client Two-Way Integration:__ In this model, the MSP’s Hornbill instance acts as the master service provider, while each client's instance operates independently. A secure trust relationship is established between the MSP and each client, ensuring complete data segregation with zero risk of data crossover between clients. This allows the MSP to deliver services seamlessly while respecting the autonomy and security needs of each client.
- __Hornbill Passport:__ The Hornbill Passport is a security framework that enables trusted access between instances. MSP agents can only access client instances if they are authorized by both the MSP and the respective client. Clients maintain control by allowing their security teams to administer access, ensuring compliance with their internal policies.
- __Special Agent Access Licensing:__ This licensing scheme allows MSP agents to access client instances without requiring a dedicated login or subscription on the client instance. This approach supports a hybrid service model where clients may have in-house staff using their Hornbill instance alongside MSP-managed services. The licensing model is designed to be cost-effective—focusing on agent access rather than charging per instance—ensuring flexibility and fairness.
- __Service Desk Agent Workbench:__ The Hornbill Service Desk Agent Workbench provides MSP agents with a unified view of their workload—tickets, tasks, and approvals—across multiple client instances. Agents can manage their work without the need to switch between different client environments, streamlining operations and improving efficiency.

## Summary
Hornbill’s MSP multi-client deployment model offers a robust, secure, and scalable solution for managed service providers. It ensures data protection, security, and access control, meeting the highest enterprise standards. This model enhances an MSP's service offering by providing an out-of-the-box solution that allows for flexible, efficient service management while maintaining strong client autonomy and security controls.


