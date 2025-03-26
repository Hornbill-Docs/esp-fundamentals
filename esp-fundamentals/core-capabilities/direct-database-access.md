# Direct Database Access (DDA)
The Direct Database Access capability is a feature of the [Enterprise Edition](/esp-fundamentals/about/hornbill-editions) of Hornbill, providing customers with direct read-only access to an optimized-for-reporting, transactional database. This access is provided via a dedicated SQL server instance with secure, encrypted private access. 

## Background
Hornbill ESP is a self-contained, fully functional transactional system giving you everything you need out of the box including a range of reporting capabilities with standard reporting, analytics, trending and dashboards, and in-app dynamic reporting and dashboard features.  For many customers, what the Hornbill platform provides out of the box is comprehensive and more than sufficient for their needs when reporting on Hornbill data is stand-alone. 

For some customers, their Hornbill instance is only one of a number of business systems where there is a need to provide cross-system and cross-departmental reporting, often by deploying enterprise BI tools and a data warehouse, where the reporting needs are beyond the capabilities of Hornbill's own integrated reporting capabilities. As a general rule, these organizations have very mature reporting capabilities to meet corporate reporting needs and will often have a dedicated team of people providing enterprise-level reporting that sources data from multiple digital systems and services.  Hornbill's Direct Database Access capability works within these environments. 

## Getting access to the Hornbill database
It is possibly counter-intuitive, but just directly accessing the system's primary database would seem the obvious and easy solution. Indeed this is a very common question.  In practice though, the Hornbill primary database is designed for transactional and UI performance; it is optimized for this use case, and as a result, data is de-normalized and related in ways that may seem  convoluted. Also, in some cases, data representation is optimized, for example things like status, timestamps, and other things that should ideally be human-recognizable will be represented as integer values. This is because we prioritize transactional performance over reporting ease.  A fully optioned-up Hornbill instance with multiple applications can have upwards of 700 database tables; that database is complex and can be difficult to navigate. Our in-built reporting tools restrict access to a sub-set of these tables to make things easier, but none the less, the in-built reporting capabilities of Hornbill are run against our application database, which is not optimized for reporting. This becomes more apparent as the scale of the data increases.  

Hornbill is expected to meet its service performance and availability obligations.  Reporting across large datasets without very careful consideration for performance of each query can lead to database locking and compute resource usage, creating large amounts of latency, which could easily and adversely affect the performance of the Hornbill application for your users.

Direct Database Access (DDA) is more than just providing a connection to a database.  DDA provides you a dedicated data-staging database instance. We replicate a subset of data from the application database to the reporting database.  Unlike the application/transactional database, the target reporting database is better optimized for reporting. Not only are the number of tables significantly reduced to only 10s of tables with just the required data you need, but the data contained within them will have been put through a transformation as part of the ETL (Extract-Transform-Load) replication process that maps data from the application database to data in the reporting database. 

The DDA instance operates on different clusters of compute resources, which insulates the application database from any poorly performing reporting queries that cause a heavy workload on the database server processing, which would otherwise severely affect performance and responsiveness.

![Direct Database Access Data Flow](/_books/esp-fundamentals/core-capabilities/images/direct-database-access.png)

## DDA operation
As you can see from the diagram, the DDA components are all running within the Hornbill Cloud environment. The basic operation of the system is designed around a simple ETL data replication model, where data is extracted periodically from the Hornbill application database, it is transformed in various ways, and then loaded (synchronized) with the DDA database.  The mappings that control what data is extracted, transformed, and replicated into the staging database are managed by Hornbill, and like customer APIs, we ensure that this database schema does not change in ways that would break any customer integration with the data through the direct access.  Typically, a customer would configure their data warehouse to query/extract the data from the staging database into their own data warehouse database, at which point the customer has full control over that data and is free to manipulate/transform as required to meet their specific reporting needs. 


## Benefits of DDA

The DDA service provided by Hornbill offers several business benefits:

- __Optimized reporting:__ By offering a dedicated SQL server instance optimized for reporting, DDA ensures that data retrieval and analysis are efficient and effective. This is particularly beneficial for complex queries and large datasets.

- __Enhanced data integration:__ For organizations that use multiple business systems, DDA facilitates cross-system and cross-departmental reporting. This integration allows for more comprehensive analytics and insights.

- __Customization and control:__ The service allows for the extraction, transformation, and loading of data in ways that align with specific business needs. Companies have control over how they manipulate and transform the data once it is in their own data warehouse.

- __Scalability and performance:__ As business data scales, the need for robust reporting capabilities becomes critical. DDA is designed to handle increased data scale without compromising performance.

- __Secure and encrypted access:__ The provision of secure, encrypted private access ensures that data security and privacy are maintained, which is crucial for sensitive business data.

- __Compatibility with enterprise BI tools:__ This service is compatible with enterprise Business Intelligence tools and data warehouses, allowing organizations to leverage their existing technology investments for advanced analytics.

- __Simplified data structure:__ The transformation process within DDA simplifies the data structure, reducing the number of tables and making the data more accessible and easier to understand compared to the primary transactional database.

- __Reliability and maintenance:__ Managed by Hornbill, the system promises reliability and maintenance of the database schema, ensuring that customer integrations remain stable and consistent.

Overall, DDA addresses the challenges of accessing and reporting on complex, large-scale business data, making it a valuable tool for organizations with advanced data analytics and reporting needs.

## Data requests
Your data is yours to control and own. The authoritative contact for a Hornbill instance can request a complete extract of the data (database and file attachments) once every 90 days, which will be provided via Secure FTP in encrypted format. If you require more frequent access to large data sets, then you should use the Hornbill DDA service.

## FAQs

### How can I connect to the DDA service?
> Your subscription must be for the [Enterprise Edition](/esp-fundamentals/about/hornbill-editions) of Hornbill, and you must request this be set up and enabled for your instance.  Once this is done, you will be given the connection and login credentials, as well as instructions on how to test your connectivity to the staging database server.

### What software do I need to connect to the DDA service?
> You can use any software that supports the standard, and ubiquitous MySQL wire protocol, including any ODBC drivers that support the same. 

### What database system does Hornbill use to provide DDA?
> We may use any MySQL-compatible database systems. At the time of this writing, we are using MariaDB running on the Linux operating system. 

### How can I be sure the connection is secure?
> One of the reasons why we ask you to explicitly request this service is to make sure that we set it up in a way that is secure, and that you use it in a way that is secure.  All connections are encrypted, password-protected, and generally not on the standard TCP/IP port.  We also recommend, where possible, that we set up a TCP/IP address whitelist so we only allow access to your DDA staging server from a specific IP address. 

### Can I control what data gets replicated to the Direct Access database?
> No, the DDA replication and transform mapping is defined and maintained by Hornbill. Specifically, each application team, and the platform team, contribute their published data to the DDA, which is a roll-up of all platform and apps published reporting database.  We aim to make all useful data available, while at the same time hide all the complexities of the system database metadata, schema de-normalization, and other app performance optimizations that make our main database less suitable for reporting. 

### Why is the DDA service only available to Enterprise customers?
> To ensure that performance is not impacted, Enterprise Edition subscriptions run on different clusters of compute resources that already include multi-database master-slave replication.  We perform DDA-sync operations generally on one of the slave databases in order to minimize impact on the primary application/transactional database. The DDA database access is an extension of the Enterprise Platform multi-database architecture; it cannot be simply added to any instance, unless that instance is on our enterprise-level technology stack.  

### Can I have a trial of the DDA service?
> In order to provide direct database access, your instance needs to be running on our Enterprise Edition platform infrastructure, which would mean you will have automatic right to use the Direct Access server (DAS) if you require.  In order to provide a trial for non-Enterprise Edition customers, we would have to migrate your instance, which would include some planning and downtime, making it impractical for us to provide a trial of DDA.  As an alternative, we can provide you with access to one of our demo systems DDA database, where you will have the opportunity to connect and review the demo data through direct access. 

### Can I run hard-hitting complex queries on the DDA staging server?
> Yes, you can. These servers are isolated, so you will not create a problem for your Hornbill instance.  However, we encourage you to use the DAS as a staging table and replicate that data to your own database and/or data warehouse platform where you can optimize your systems for whatever levels of query complexity you require.  We would also advise that if you place a great deal of load on the DDA staging database, then the DDA replication process will slow down, and, in that case you could suffer severe lags in time between your live data and replicated data. There is no one-fits-all approach, so we encourage you to keep an open mind and test with your particular environment to find the optimum way of making use of the data you can access directly. 

### Who decides what the database schema on the DDA database contains for my instance?
> The database schema presented in the DDA database is controlled and maintained by Hornbill's product teams. As we develop/evolve our products, we will ensure that any customer's reporting-relevant data is included in the DDA database. When accessing the database through the DDA service, you access it read-only, giving you no option to directly add or change data, or modify the database schema. If you want to request changes or additions to the DDA database, please follow our [process for raising feature requests](/esp-fundamentals/about/request-product-enhancements).

### Can I customize the DDA database to include other data that I know is in my instance but not presented in the DDA database?
> No, the DDA database is not customizable. The DDA database is a subset of the main database that sits under the hood in your Hornbill instance. The Hornbill Platform, and each application, creates the DDA database schema as part of the product definition. You can think of the DDA database schema in the same way as our customer-facing APIs.  The DDA database is designed first and foremost to be a customer-facing dataset, not subject to breaking changes. So, just like our customer APIs, you can build your data integrations for reporting against the DDA and expect that it will not change, and not break your integrations. Behind the scenes, the DDA database is created using a DDA (ETL) process, so the database presented in the DDA is a subset, and transformed database schema. This is done to create a more reporting-friendly database schema for you to work with. 

 ### Can I request other data that I know is in my instance to be included in the DDA database?
> Yes, asking for additional data is a common feature request.  However, just like our APIs and other product features, any changes to the DDA schema is a function of a product enhancement, and is made globally for all customers using Hornbill. In other words, the DDA schema is part of our product definition; it is not in itself a configurable thing.  All reasonable requests are considered, but, please keep in mind that such changes go through our normal product change process for consideration. If you want to request changes or additions to the DDA database, please follow our [process for raising feature requests](/esp-fundamentals/about/request-product-enhancements).

### Can I add my own data to the DDA server/database?
> No, you cannot.  The Direct Access database is read-only. Your login credentials will not have any permissions on the database other than read. 

### What if there is data in Hornbill that I want to report on that is not in the Direct Access database?
> Just ask us; we will consider all reasonable requests for additional data.  Keep in mind, this is much like asking for a product feature or a new API. Any changes we make to the DDA/replication mapping and or Direct Access database schema will be made globally on our platform and will affect all customers. So, we will only expand the schema to make it generically more useful to all.