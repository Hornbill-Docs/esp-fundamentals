# Direct Database Access (DDA)
Direct Database Access (DDA) is an optional feature available in the Enterprise Edition of the Hornbill platform. It gives customers the ability to securely connect to a read-only database that’s specifically optimized for reporting.

When enabled, a dedicated SQL Server instance is provisioned for your use, offering encrypted, private access to your Hornbill data—designed specifically to support your advanced reporting and analytics needs.

## Background
Hornbill ESP is a fully integrated transactional informaiton system that includes a wide range of built-in reporting tools: standard reports, analytics, trends, dashboards, and in-app dynamic reporting. For many customers, these out-of-the-box capabilities are more than sufficient to meet their reporting needs.

However, some organizations require a broader view — with consolidated reporting across multiple systems or have very advanced and specific reporting requirements. These are typically more mature, enterprise-level environments using BI tools and data warehouses are in use to support cross-functional, cross-system reporting. In such cases, Hornbill’s built-in reporting may not be sufficient to meet all of these customers requirements.

For these scenarios, DDA offers a powerful solution: direct access to your Hornbill data formatted and optimized for enterprise-grade reporting 


## Why not just give customers access to the primary database?
A common question we hear is: “Can we get direct access to the Hornbill database?”

While it might seem like the easiest path, there are important reasons why direct access to the primary Hornbill database is not offered:

- __Optimized for performance, not reporting:__ The primary database is designed to support fast, responsive UI and transactional performance. This means the data is often de-normalized, structured in non-obvious ways, or stored using system-level representations (e.g., statuses as integers).
- __Complex data model:__ A full Hornbill instance may contain 700+ tables. Navigating this structure for reporting can be complex and inefficient.
- __Service reliability:__ Large or poorly optimized queries run directly against the transactional database could degrade performance for end users—something we take great care to avoid.
- __Database Schema is Flud:__ Hornbill reserves the right to change the database schema at any time.  If you depeneded on specific data when accessing the database directly, this would create a significant maintenance overhead for customers.
- __Documentation:__ Large parts of the database schema is not well documented because its not designed for direct customer consumption

Hornbill’s internal reporting tools work within these constraints because they are aligned with the database schema at all times as we evolve our products. 


## DDA is more than just a direct connection to the Database. 

The Direct Database Access (DDA) capability is more than just providing you with a direct connection to a database.  DDA provides a dedicated data-staging database instance. We replicate and normalize a subset of data from the application database to the DDA reporting database.  Unlike the application/transactional database, the target reporting database is better optimized for reporting. Not only are the number of tables significantly reduced to only 10s of tables with just the required data you need, but the data contained within them will have been run through a transformation process to optimize data specifically for reporting needs. 

The DDA database instance is deployed on compute resources that are isolated from the main application database, which insulates the main transactional application database from any poorly performing reporting queries that cause a heavy workload on the database server processing.

![Direct Database Access Data Flow](/_books/esp-fundamentals/core-capabilities/images/direct-database-access.png)

## DDA operation
As shown in the diagram, all DDA components operate entirely within the Hornbill Cloud environment.

At its core, DDA follows a straightforward ETL (Extract, Transform, Load) model:

- __Extract:__ Data is periodically pulled from the Hornbill application (transactional) database.
- __Transform:__ The data is processed and transformed to support reporting needs—normalizing formats, resolving references, and converting values into more readable forms.
- __Load:__ The transformed data is then synchronized into a dedicated reporting (staging) database.

Hornbill manages the mappings that determine what data is extracted, how it's transformed, and what gets loaded into the reporting database. These mappings are carefully maintained—just like our public APIs—to ensure schema stability. This means you can rely on a consistent structure that won’t change unexpectedly or break your integrations.

Once the data is available in the DDA staging database, you can connect your own data warehouse or BI tools to it. From there, you’re in full control: you can extract, transform, and integrate the data however you like to meet your unique reporting and analytics needs.


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