# Direct Database Access
The Direct Database Access capability is a feature of the Enterprise Edition of the Hornbill platform, providing customers with direct read-only access to an optimized for reporting, transactional data. This access is provided via a dedicated SQL server instance with secure, encrypted private access. 

## Background
Hornbill ESP is a self-contained fully functional transactional system giving you everything you need out of the box including a range of reporting capabilities including standard reporting, analytics, trending and dashboards and in-app dynamic reporting and dashboard features.  For many customers what the Hornbill platform provides out of the box is comprehensive and more than sufficient for their needs when reporting on Hornbill data is stand-alone. 

For some customers, their Hornbill instance is only one of a number of business systems where there is a need to provide cross-system and cross-departmental reporting, often by deploying Enterprise BI tools and a Data Warehouse, where the reporting needs are beyond the capabilities of Hornbill's own integrated reporting capabilities. As a general rule, these organizations have very mature reporting capabilities to meet corporate reporting needs and will often have dedicated team of people providing enterprise-level reporting sourcing data from multiple digital systems and services.  The Direct Database Access capability works within these environments. 

## Accessing the Hornbill Database
Its possibly counter-intuitive, but just directly accessing the systems primary database would seem the obvious, and easy solution. Indeed this is a very common question.  In practice, the Hornbill primary database is designed for transactional and UI performance, its optimized for this use case, and as a result, data is often de-normalized and related in ways that may seem very convoluted, this is because we prioritize transactional performance over reporting ease.  A fully optioned-up Hornbill instance with multiple applications can have upwards of 700 database tables, that database is complex and can be very difficult to navigate. Our in-built reporting tools restrict access to a sub-set of these tables to make things easier, but none the less, the in-built reporting capabilities of Hornbill are run against our application database which is not optimized for reporting, this becomes more apparent as the scale of the data increases.  

It is also important to understand that we are expected to meet our service performance and availability obligations.  Reporting across large datasets without very careful consideration for performance of each query can lead to locking and large amounts of latency which can adversely effect the performance of the Hornbill application.

Direct Database Access is more than just providing a connection to a database.  DDA provides you a dedicated data staging database instance, we replicate a sub-set of data from the application database to the reporting database.  Unlike the application/transactional database, the target reporting database is better optimized for reporting, not only are the number of tables significantly reduced to only 10's of tables with just the required data you need, but the data contained within them will have been put through a transformation as part of the ETL replication process that maps data from the application database to data in the reporting database. 

The Direct Access Database instance operates on different clusters of compute resources, so a poorly performing reporting query that loads up the database server processing, meaning the application database is insulated from such workloads that would otherwise severely affect performance and responsiveness. 

![Direct Database Access Data Flow](/_books/esp-fundamentals/core-capabilities/images/direct-database-access.png)

## Direct Database Access Operation
As you can see from the diagram, the Direct Database Access components are all running within the Hornbill Cloud environment. The basic operation of the system is designed around a simple ETL model, where data is extracted periodically from the Hornbill Application Database, its transformed in various ways, and then loaded (synchronized) with the Direct Access Staging Database.  The mappings that control what data is extracted, transformed and replicated into the staging database is managed by Hornbill, and like customer API's we ensure that this database schema does not change in ways that would break any customer integration with the data through the direct access.  Typically, a customer would configure their Data Warehouse to query/extract the data from the staging database into their own data warehouse database, at which point the customer has full control over that data and are free to manipulate/transform as required to meet their specific reporting needs. 


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






