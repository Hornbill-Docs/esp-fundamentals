# Platform editions

The Hornbill Platform is offered to customers in two specific editions, referred to as Standard and Enterprise.  Both editions offer the same levels of availability, security, data redundancy features, and uptime guarantees.  For organizations deploying one or two primary applications, the Standard Edition meets their needs; our applications are optimized to run at scale on this edition. However, for some customers, either because of scale or because of complexity of the workload, the Enterprise Edition may be more appropriate or even required. The fundamental difference between the Standard and Enterprise editions is configuration of compute resources, with the Enterprise Edition tuned and resourced for the higher demands of system scalability, performance, redundancy, and mean time to recovery (MTTR) that enterprise organizations demand. 

:::note
The compute resource configurations are not bespoke. We currently define two specific architectures (Standard and Enterprise). There is not a menu of options that customers can choose from. 
:::


![Hornbill Platform Editions](/_books/esp-fundamentals/about/images/esp-editions.png)

## Standard Edition architecture
The Standard Edition is the typical configuration for most customers using a single primary Hornbill application. Users access their application data through the application logic and a database, which is their primary database. The primary database (based on MariaDB) is a single transactional relational database that serves both transactional as well as read queries. For light to medium loads, workflows, and data sets, this configuration offers ample performance and reliability. 

## Enterprise Edition architecture
The Enterprise Edition is a more modular, horizontally scaled configuration, designed primarily to handle much larger transactional and query throughput, while also separating, balancing, and proactively fine-tuning compute resources to more equally match individual customers' instance workloads. In addition to the configuration differences, there are a number of additional features offered that require more compute resources to function adequately. These features are typically only required by large organizations that have requirements for higher levels of security, auditing, compliance, and performance at scale. 

## Feature matrix
The following feature list provides a side-by-side comparison of the Standard and Enterprise Editions to help you evaluate them. 

### Scalability and architecture 
|<div style="width:490px"></div>|<div style="width:200px; text-align:cetnter;">Standard</div>|<div style="width:200px; text-align:cetnter;">Enterprise</div>|
|:--|:--:|:--:|
|Compute nodes/memory sharing|Up to 8 instances|Up to 4 instances|
|Storage technology|SSD|NVME|
|Storage configuration|RAID 5|RAID 5 + 0|
|Active database server|Single|Multiple|
|GEO Replica DR|Single (remote DC)|Dual (remote and local)|
|Collaboration, application, and process users|Suitable for up to 500 users|No limit|

### Main features 
|<div style="width:490px"></div>|<div style="width:200px; text-align:center;">Standard</div>|<div style="width:200px; text-align:center;">Enterprise</div>|
|:--|:--:|:--:|
|Task management|&#x2705;|&#x2705;|
|Free applications|&#x2705;|&#x2705;|
|Premium applications|&#x2705;|&#x2705;|
|Shared mailboxes|&#x2705;|&#x2705;|
|Document management|&#x2705;|&#x2705;|
|Reporting and scheduling|&#x2705;|&#x2705;|
|Advanced Analytics|$<br><small style="font-size: 0.7em">Included since July 2024**<br>(see below note)</small>|&#x2705;|
|Advanced reporting and delivery|-|&#x2705;|
|[Direct Database Access](/esp-fundamentals/core-capabilities/direct-database-access)|-|&#x2705;|
|[Multi-Client/MSP Capabilities](/esp-fundamentals/core-capabilities/multi-client-msp)|-|$|

:::note
- In July 2024, the __Advanced Analytics__ module was rolled into the Service Manager user subscription price as part of a pricing simplification exercise. For existing customers who subscribed before this change, the subscription option for Advanced Analytics remains, as does the lower priced subscriptions for Service Manager users. 
:::

### Integration
|<div style="width:490px"></div>|<div style="width:200px; text-align:center;">Standard</div>|<div style="width:200px; text-align:center;">Enterprise</div>|
|:--|:--:|:--:|
|iBridge Cloud Integration Basic|&#x2705;|&#x2705;|
|iBridge Cloud Integration Premium|$|$|
|Enterprise Orchestration Integration Connectors|$|$|

### Security
|<div style="width:490px"></div>|<div style="width:200px; text-align:center;">Standard</div>|<div style="width:200px; text-align:center;">Enterprise</div>|
|:--|:--:|:--:|
|TLS encryption|&#x2705;|&#x2705;|
|Single sign-on (SAML 2.0)|&#x2705;|&#x2705;|
|Data encryption at rest (AES-256)|&#x2705;|&#x2705;|
|IP access controls|&#x2705; <br><span style="font-size: 7pt; color: gray">(added 09/2024)</span>|&#x2705;|
|Advanced security compliance <sup>(Note 1)</sup>|-|&#x2705;|
|Advanced DR (priority recovery) <sup>(Note 2)</sup>|-|&#x2705;|
|Security audit reports and extended audit storage <sup>(Note 3)</sup>|-|&#x2705;|
|Extended mobile access controls <sup>(Note 4)</sup>|-|&#x2705;|

:::note
1. __Advanced security compliance.__ This extends our standard platform by facilitating deeper and more bespoke individual support for security-related needs, including additional service features to provide you with more fine-grained controls over IP and mobile access, etc. In addition, we provide more personalized support for security audits, and where appropriate, can facilitate you reviewing Hornbill's own ISM and compliance stats (charges generally apply).
2. __Priority DR time.__ Instances running on the Enterprise Edition of our platform include a hot-backup replica database running in the same physical location as the primary and replica databases.  This means in the event of a system failure that requires a database/storage rebuild, your data is already in the physical location, so MTTR is significantly faster than that on Standard Edition, where the data is available in a remote data center and will need copying back to the primary DC for restoration.  The transfer of data can take many hours for large data sets.
3. __Security auditing.__ This includes more comprehensive and granular security auditing, logging, and reporting capabilities generally required in enterprise organizations. 
4. __Extended access controls__. This provides more granular and lower-level control over access to your instance, including mobile device and IP address restrictions and access controls.
:::


## Choosing the right platform edition for your organization
Selecting the appropriate Hornbill platform edition depends on your organization's specific needs. The Standard Edition is robust and capable, supporting hundreds or even thousands of concurrently active users. For most organizations, it offers more than adequate performance.

However, the key limiting factor in scalability is database throughput. In the Standard Edition, both database writes and reads are handled by a single database instance. The Enterprise Edition, on the other hand, uses a master-slave database configuration. This setup dedicates the primary database to write transactions while distributing read operations across multiple slave databases, significantly improving performance and scalability—especially since most database activity in Hornbill applications involves reads.

### When to consider the Enterprise Edition
The Enterprise Edition is ideal for environments with:

- A large number of highly active users.
- Complex workflows or high data throughput.
- Heavy transaction volumes (e.g., logging many requests or operations).
- Large volumes of emails, automations, or workflows.

These factors, along the Workload/Workflow axis, may indicate the need for the Enterprise Edition. The decision will vary based on your specific requirements, user activity, and operational complexity.

Additionally, the Enterprise Edition might be necessary at a smaller scale if you require:

- Advanced security features.
- Faster or prioritized system recovery in disaster recovery (DR) situations.

Each organization's needs are unique, and it may be difficult to assess the platform edition you require. Our product experts can advise you, taking into consideration your specific circumstances and expected usage.  You can generally start with Standard and assess the levels of performance and throughput.

:::note
Although it is possible to switch from Standard to Enterprise without any changes to your instance, behind the scenes it is actually a full data migration from one set of systems to another. This requires a brief downtime (around 30 minutes) in which Hornbill will complete the migration out of hours at a time that is convenient for you. 
::: 