# Platform Editions

The Hornbill Platform is offered to customers in two specific editions, referred to as Standard and Enterprise.  Both editions offer the same levels of availability, security, data redundancy features and uptime guarantees.  For organizations deploying one or two primary applications the Standard Edition is perfectly adequate, our applications are optimized to run, at scale on this edition.  However, for some customers, either because of scale or, because of complexity of the workload, the Enterprise Edition may be more appropriate or even required.  The fundamental difference between the Standard and Enterprise editions is configuration of compute resources, with the Enterprise edition tuned and resourced for the higher demands of system scalability, performance, redundancy and MTR that enterprise organizations demand. 

:::note
The compute resource configurations are not bespoke, we currently define two specific architectures (Standard and Enterprise), there is not a "menu" of options that customers can pick and choose from. 
:::

## Platform Edition Feature Matrix
The following feature list provides a side-by-side comparison of the two editions to help you evaluate the differences between the two editions. 

### Scalability & Architecture 
|<div style="width:490px"></div>|<div style="width:200px; text-align:cetnter;">Standard</div>|<div style="width:200px; text-align:cetnter;">Enterprise</div>|
|:--|:--:|:--:|
|Scalability & Arch|
|Compute Nodes/Memory Sharing|Up to 8 instances|Up to 4 instances|
|Storage Technology|HDD|SSD|
|Storage Configuration|RAID 5|RAID 5 + 0|
|Activate Database Server|Single|Multiple|
|GEO Replica DR|Single (remote DC)|Dual (Remote and Local)|
|Collaboration, Application & Process Users|Up to 500 Active|No Limit|

### Main Features 
|<div style="width:490px"></div>|<div style="width:200px; text-align:cetnter;">Standard</div>|<div style="width:200px; text-align:cetnter;">Enterprise</div>|
|:--|:--:|:--:|
|Collaboration|Y|Y|
|Task Management|Y|Y|
|Free Applications|Y|Y|
|Premium Applications|Y|Y|
|Shared Mailboxes|Y|Y|
|Document Management|Y|Y|
|Reporting & Scheduling|Y|Y|
|Advanced Analytics|$|Y|
|Advanced Reporting & Delivery|X|Y|

### Integration
|<div style="width:490px"></div>|<div style="width:200px; text-align:cetnter;">Standard</div>|<div style="width:200px; text-align:cetnter;">Enterprise</div>|
|:--|:--:|:--:|
|iBridge Cloud Integration Basic|Y|Y|
|iBridge Cloud Integration Premium|$|$|
|Enterprise Orchestration Integration Connectors|$|$|

### Security
|<div style="width:490px"></div>|<div style="width:200px; text-align:cetnter;">Standard</div>|<div style="width:200px; text-align:cetnter;">Enterprise</div>|
|:--|:--:|:--:|
|TLS Encryption|Y|Y|
|Single Sign-on (SAML 2.0)|Y|Y|
|Data Encryption At Rest (AES-256)|Y|Y|
|IP Access Controls|X|Y|
|Advanced Security Compliance <sup>(Note 1)</sup>|X|Y|
|Advanced DR (priority recovery)|X|1|
|Security Audit Reports & Extended Audit Storage <sup>(Note 2)</sup>|X|1|
|Extended Mobile Access Controls <sup>(Note 3)</sup>|X|1|

:::note
1. __Advanced Security Compliance__: extends our standard platform by facilitating deeper and more bespoke individual support for security-related needs, including additional service features to provide you with more find-grained controls over IP and mobile access etc. In addition, we provide more personalized support for security audits, and where appropriate, can facilitate you reviewing Hornbill' own ISM and compliance stats (charges generally apply)
2. Instances running on the Enterprise Edition of our platform include a Hot Backup replica database running in the same physical location as the primary and replica databases.  This means in the event of a system failure that requires a database/storage rebuild, your data is already in the physical location, so mean time to recovery is significantly faster than that on Standard edition, where the data is available in a remote data center and will need copying back to the primary DC for restoration.  The transfer of data can take many hours for large data sets.
3. Provides more granular and lower level control over access to your instance, including mobile device and IP address restrictions and access controls
:::

## Standard Edition
The the Standard Edition is the typical configuration for most customers using a single primary Hornbill application will be the Standard edition configuration.  Users access their applications data through the application logic and a database which is their primary database. The primary database (based on MariaDB) is single transactional relational database that serves both transactional as well as read queries.  For light-to medium loads, workflows and data sets, this configuration offers ample performance and reliability. 

![Standard Edition](/_books/esp-fundamentals/about/images/esp-editions-standard.png)

## Enterprise Edition
The Enterprise Edition is a more modular, horizontally scaled configuration, designed primarily to much greater transactional and query throughput, while also separating, balancing and tuning compute resources to more equally match individual customer instance workloads.  In addition to the configuration differences, there are a number of __additional features__ offered that require more compute resources to function adequately and are typically only demanded by enterprise organizations where higher levels of security, auditing, compliance and performance at scale are required. 

![Enterprise Edition](/_books/esp-fundamentals/about/images/esp-editions-enterprise.png)
