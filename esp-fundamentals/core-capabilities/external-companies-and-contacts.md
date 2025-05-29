# External Companies and Contacts

The hornbill Platform provides the ability for you to deifne external companies and contacts.  At the platform level, this is used primarily to enabled guest logins and access controls to external facing portals. Beyond that, applications may extend this information for application-specific functionallity, for example, providing support to external customers (as sooposed to internal employees)

The data model for Companies and Context is a simple one to many relationship between Companies, where, a Contact but be associated witha Company, and a Company can have many Contacts associated with it. 

:::node
Please keep in mind that an External Company in this context does not in any way relate to the Company OU type that may be defined in your [Internal Groups and Teams Structure](/esp-fundamentals/core-capabilities/internal-groups-and-teams)
:::