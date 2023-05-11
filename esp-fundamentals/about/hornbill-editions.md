# Platform Editions

The Hornbill Platform is offered to customers in two specific editions, referred to as Standard and Enterprise.  Both editions offer the same levels of availability, security, data redundancy features and uptime guarantees.  For organizations deploying one or two primary applications the Standard Edition is perfectly adequate, our applications are optimized to run, at scale on this edition.  However, for some customers, either because of scale or, because of complexity of the workload, the Enterprise Edition may be more appropriate or even required.  The fundamental difference between the Standard and Enterprise editions is configuration of compute resources, with the Enterprise edition tuned and resourced for the higher demands of system scalability, performance, redundancy and MTR that enterprise organizations demand. 

:::note
The compute resource configurations are not bespoke, we currently define two specific architectures (Standard and EnterprisE), there is not a "menu" of options that customers can pick and choose from. 
:::


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
|Advanced Security Compliance|X|Y|
|Advanced DR (priority recovery)|X|1|
|Security Audit Reports & Extended Audit Storage|X|1|
|Extended Mobile Access Controls|X|1|


## Standard Edition
The the Standard Edition is the typical configuration for most customers using a single primary Hornbill application will be the Standard edition configuration.  Users access their applications data through the application logic and a database which is their primary database. The primary database (based on MariaDB) is single transactional relational database that serves both transactional as well as read queries.  For light-to medium loads, workflows and data sets, this configuration offers ample performance and reliability. 

![Standard Edition](/_books/esp-fundamentals/about/images/esp-editions-standard.png)

## Enterprise Edition
The Enterprise Edition is a more modular, horizontally scaled configuration, designed primarily to much greater transactional and query throughput, while also separating, balancing and tuning compute resources to more equally match individual customer instance workloads.  In addition to the configuration differences, there are a number of __additional features__ offered that require more compute resources to function adequately and are typically only demanded by enterprise organizations where higher levels of security, auditing, compliance and performance at scale are required. 

![Enterprise Edition](/_books/esp-fundamentals/about/images/esp-editions-enterprise.png)
