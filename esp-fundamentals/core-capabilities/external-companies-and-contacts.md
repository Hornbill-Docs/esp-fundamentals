# External Companies and Contacts

The Hornbill Platform provides the ability for you to define external companies and contacts.  At the platform level, this is used primarily to enable guest logins and access controls to external facing portals. Beyond that, applications may extend this information for application-specific functionality, for example, providing support to external customers (as opposed to internal employees)

The data model for Companies and Contacts is a simple one to many relationship between Companies, where, a Contact must be associated with a Company, and a Company can have many Contacts associated with it. 

:::note
Please keep in mind that an __External Company__ in this context does not in any way relate to the Company OU type that may be defined in your [Internal Groups and Teams Structure](/esp-fundamentals/core-capabilities/internal-groups-and-teams)
:::