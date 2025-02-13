# Direct Database Access (DDA)
The Direct Database Access capability is a feature of the [Enterprise Edition](/esp-fundamentals/about/hornbill-editions) of Hornbill, providing customers with direct read-only access to an optimized for reporting, transactional data. This access is provided via a dedicated SQL server instance with secure, encrypted private access. 

## Background
Hornbill ESP is a self-contained fully functional transactional system giving you everything you need out of the box including a range of reporting capabilities including standard reporting, analytics, trending and dashboards and in-app dynamic reporting and dashboard features.  For many customers what the Hornbill platform provides out of the box is comprehensive and more than sufficient for their needs when reporting on Hornbill data is stand-alone. 

For some customers, their Hornbill instance is only one of a number of business systems where there is a need to provide cross-system and cross-departmental reporting, often by deploying Enterprise BI tools and a Data Warehouse, where the reporting needs are beyond the capabilities of Hornbill's own integrated reporting capabilities. As a general rule, these organizations have very mature reporting capabilities to meet corporate reporting needs and will often have dedicated team of people providing enterprise-level reporting sourcing data from multiple digital systems and services.  The Direct Database Access capability works within these environments. 

## Getting Access to the Hornbill Database
Its possibly counter-intuitive, but just directly accessing the systems primary database would seem the obvious, and easy solution. Indeed this is a very common question.  In practice though, the Hornbill primary database is designed for transactional and UI performance, its optimized for this use case, and as a result, data is quite de-normalized and related in ways that may seem very convoluted, and in some cases data representation is optimized, for example things like status, timestamps and other things that should ideally be human-recognizable  will be represented as integer values, this is because we prioritize transactional performance over reporting ease.  A fully optioned-up Hornbill instance with multiple applications can have upwards of 700 database tables, that database is complex and can be very difficult to navigate. Our in-built reporting tools restrict access to a sub-set of these tables to make things easier, but none the less, the in-built reporting capabilities of Hornbill are run against our application database which is not optimized for reporting, this becomes more apparent as the scale of the data increases.  

Hornbill is expected to meet its service performance and availability obligations.  Reporting across large datasets without very careful consideration for performance of each query can lead to database locking and compute resource usage, creating large amounts of latency which could easily and adversely effect the performance of the Hornbill application for your users.

Direct Database Access (DDA) is more than just providing a connection to a database.  DDA provides you a dedicated data staging database instance, we replicate a sub-set of data from the application database to the reporting database.  Unlike the application/transactional database, the target reporting database is better optimized for reporting, not only are the number of tables significantly reduced to only 10's of tables with just the required data you need, but the data contained within them will have been put through a transformation as part of the ETL (Extract-Transform-Load) replication process that maps data from the application database to data in the reporting database. 

The Direct Access Database instance operates on different clusters of compute resources, so a poorly performing reporting query that loads up the database server processing, meaning the application database is insulated from such workloads that would otherwise severely affect performance and responsiveness. 

![Direct Database Access Data Flow](/_books/esp-fundamentals/core-capabilities/images/direct-database-access.png)

## Direct Database Access Operation
As you can see from the diagram, the Direct Database Access components are all running within the Hornbill Cloud environment. The basic operation of the system is designed around a simple ETL (Extract-Transform-Load) data replication model, where data is extracted periodically from the Hornbill Application Database, its transformed in various ways, and then loaded (synchronized) with the DDA Database.  The mappings that control what data is extracted, transformed and replicated into the staging database is managed by Hornbill, and like customer API's we ensure that this database schema does not change in ways that would break any customer integration with the data through the direct access.  Typically, a customer would configure their Data Warehouse to query/extract the data from the staging database into their own data warehouse database, at which point the customer has full control over that data and are free to manipulate/transform as required to meet their specific reporting needs. 


## Benefits of Direct Database Access

The Direct Database Access service provided by Hornbill offers several business benefits:

- __Optimized Reporting:__ By offering a dedicated SQL server instance optimized for reporting, Direct Database Access ensures that data retrieval and analysis are efficient and effective. This is particularly beneficial for complex queries and large datasets.

- __Enhanced Data Integration:__ For organizations that use multiple business systems, Direct Database Access facilitates cross-system and cross-departmental reporting. This integration allows for more comprehensive analytics and insights.

- __Customization and Control:__ The service allows for the extraction, transformation, and loading of data in ways that align with specific business needs. Companies have control over how they manipulate and transform the data once it is in their own data warehouse.

- __Scalability and Performance:__ As business data scales, the need for robust reporting capabilities becomes critical. Direct Database Access is designed to handle increased data scale without compromising performance.

- __Secure and Encrypted Access:__ The provision of secure, encrypted private access ensures that data security and privacy are maintained, which is crucial for sensitive business data.

- __Compatibility with Enterprise BI Tools:__ This service is compatible with Enterprise Business Intelligence tools and data warehouses, allowing organizations to leverage their existing technology investments for advanced analytics.

- __Simplified Data Structure:__ The transformation process within Direct Database Access simplifies the data structure, reducing the number of tables and making the data more accessible and easier to understand compared to the primary transactional database.

- __Reliability and Maintenance:__ Managed by Hornbill, the system promises reliability and maintenance of the database schema, ensuring that customer integrations remain stable and consistent.

Overall, Direct Database Access addresses the challenges of accessing and reporting on complex, large-scale business data, making it a valuable tool for organizations with advanced data analytics and reporting needs.

## Data Requests
Your data is yours to control and own. The authoritative contact for a Hornbill instance can request a complete extract of the data (Database and File Attachments) once every 90 days which will be provided via Secure FTP in encrypted format. If you require more frequent access then the Hornbill DDA Service.

## Frequently Asked Questions

### How Can I connect to the Direct Database Access service?
Your subscription must be for the [Enterprise Edition](/esp-fundamentals/about/hornbill-editions) of Hornbill and you are required to request this be setup and enabled for your instance.  Once this is done, you will be given the connection and login credentials, as well as instructions on how to test your connectivity to the staging database server.

### What Software Do I need to connect to the Direct Database Access service
You can use any software that supports the standard, and ubiquitous MySQL wire protocol, including any ODBC drivers that support the same. 

###W hat Database System does Hornbill Use to provide Direct Database Access?
 We may use any MySQL-compatible database systems. At the time of this writing we happen to be using MariaDB running on Linux operating system. 

### How can I be sure the connection is secure?
> One of the reasons why we ask you to explicitly request this service is to make sure that we set it up in a way, and you use it in a way that is secure.  All connections are encrypted, password protected and generally not on the standard TCP/IP port.  We also recommend where possible that we set up an TCP/IP address whitelist so we only allow access to your Direct Access Database staging server from a specific IP address. 

### Can I control what data gets replicated to the Direct Access Database?
> No, the DDA replication and transform mapping is defined and maintained by Hornbill, specifically, each application team, and the platform team contribute their published data to the DDA, which is a roll-up of all platform and apps published reporting database.  We aim to make all useful data available, while at the same time hide all the complexities of the system database metadata, schema de-normalization and other app performance optimizations that make our main database less suitable for reporting. 

### Why is the Direct Database Access service only available to Enterprise customers?
> To ensure that performance is not impacted, enterprise edition subscription run on different clusters of compute resources that already include multi-database master-slave replication.  We perform DDA sync operations generally on one of the slave databases in order to minimize impact on the primary application/transactional database. The DDA  Database Access is an extension of the Enterprise Platform multi-database architecture, it cannot be simply added to any instance, unless that instance is on our enterprise-level technology stack.  

### Can I have a trial of the Direct Database Access service?
> In order to provide direct database access your instance needs to be running on our Enterprise platform edition infrastructure, which would mean you will have automatic right to use the DAS if you require.  In order to provide a trial for non-Enterprise platform customers we would have to migrate your instance, which would include some planning and downtime, making it impractical for us to provide a trial of Direct Database Access.  As an alternative, we can provide you with access to one of our demo systems Direct Database Access database, where you will have the opportunity to connect and review the demo data through direct access. 

### Can I run hard-hitting complex queries on the Direct Database Access staging server?
> Yes you can, these servers are isolated so you will not create a problem for your Hornbill instance.  However, we encourage you to use the Direct Access Database server as a staging table and replicate that data to your own database and/or data warehouse platform where you can optimize your systems for whatever levels query complexity you require.  We would also advise that if you place a great deal of load on the DDA staging database, then the DDA replication process will slow down, and, in that case you could suffer severe lags in time between your live data and replicated data. There is no one approach fits all, so we encourage you to keep and open mind and test with your particular environment to find the optimum way of making use of the data you can access directly. 

### Who decides what the database schema on the Direct Database Access database contains for my instance?
> The database schema presented in the DDA database is controlled and maintained by Hornbill's product teams. As we develop/evolve our products, we will ensure that any customer reporting-relevant data is included in the DDA database. When accessing the database through the Direct Database Access service, you access it read-only, giving you no option to directly add or change data, or modify the database schema. If you want to request changes or additions to the DDA Database, please follow our [Process for Raising Feature Requests](/esp-fundamentals/about/request-product-enhancements)

### Can I customize the DDA database to include other data that I know is in my instance but not presented in the DDA database?
> No, the DDA Database is not customizable, the DDA database is a sub-set of the main database that sits under the hood in your Hornbill instance. The Hornbill Platform, and each Application creates the DDA database schema as part of the product definition, you can think of the DDA database schema in the same way as our customer-facing API's.  The DDA database is designed first and foremost to be a customer-facing data set, not subject to breaking changes, so just like our Customer API's you can build your data integrations for reporting against the DDA and expect that it will not change, and break your integrations. Behind the schemes the DDA Database is created using an DDA (Extract-Transform-Load) process, so the database presented in the DDA is a sub-set, and transformed database schema, this is done to create more reporting-friendly database schema for you to work with. 

 ### Can I request other data that I know is in my instance to be included in the DDA Database?
> Yes, asking for additional data is a comment feature request.  However, just like our API's and other product features, any changes to the DDA Schema is a function of product enhancement, and is made globally for all customers using Hornbill, in other words, the DDA Schema is part of our product definition, its not in its self a configurable thing.  All reasonable requests are considered, but, please keep in mind that such changes go through our normal product change process for consideration. If you want to request changes or additions to the DDA Database, please follow our [Process for Raising Feature Requests](/esp-fundamentals/about/request-product-enhancements)

### Can I add my own data to the Direct Access Database server/database?
> Simple answer here is no, you cannot.  Direct Access Database is read-only, your login credentials will not have any permissions on the database other than read. 

### What if there is data in Hornbill that I want to report on that is not in the Direct Access Database?
> Just ask us, we will consider all reasonable requests for additional data.  Keep in mind, this is much like asking for a product feature or a new API. Any changes we make to the DDA/replication mapping and or direct access database schema will be made globally on our platform and will affect all customers, so we will only expand the schema to make it generically more useful to all. 


