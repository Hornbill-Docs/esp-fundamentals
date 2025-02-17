# Organization and team structure
It is possible to define part or all of your organizational structure in Hornbill. This allows you to organize your users into logical and organizational groups.  In Hornbill there are two classes of organizational units, general and functional.  While general org types are there to help you define your org structure, functional org types, can not only be part of your organizational structure but also have some extended functional capabilities, generally related to task and work assignments, ownership and content sharing. 


## Common types of organizational structure 
There are many types of organizational structures in use today, each with its own strengths and weaknesses.  Here are some of the most common types that can easily be modeled in Hornbill if required:

1. __Hierarchical Structure__: Also known as the traditional or pyramid structure, this type of organization is characterized by a clear chain of command, where each level of management reports to the level above it. This structure is common in large corporations and government agencies. It can provide clear lines of authority, but may limit flexibility and adaptability.

2. __Flat Structure__: In a flat organization, there are fewer layers of management, and employees tend to have more autonomy and decision-making power. This structure is often found in startups and small businesses. It can promote faster decision-making and better communication, but may struggle with scalability as the organization grows.

3. __Matrix Structure__: This type of organization combines elements of both functional and project-based structures. Employees are grouped by function (e.g., finance, marketing) and by project or product, creating a matrix of reporting relationships. Matrix structures can be effective in fostering collaboration and efficient use of resources, but may also lead to confusion and conflict over competing priorities.

4. __Divisional Structure__: In a divisional organization, business units or divisions operate independently, each focusing on a specific product or market segment. Each division has its own resources and functions, such as finance, marketing, and HR. This structure can support flexibility and innovation within divisions, but may also create redundancies and a lack of communication between divisions.

5. __Functional Structure__: A functional organization groups employees by their specific skills or functions, such as finance, marketing, or HR. This structure is common in medium to large-sized businesses and can lead to operational efficiencies and clear lines of responsibility. However, it may also result in a lack of cross-functional communication and collaboration.  Organizing groups of people into functional structures is critical if you want to assign responsibility for work through responsible teams/groups 

6. __Network Structure__: This type of organization relies on a network of relationships between individuals, teams, or companies, rather than a rigid hierarchy. Network structures are often used by organizations that need to remain agile and respond quickly to changing conditions, such as consulting firms or technology companies. They can foster innovation and adaptability, but may also suffer from a lack of clear authority and accountability. Hornbill Collaboration is an application and feature set that easily facilitates this type of self-organization network approach. 

7. __Holacracy__: Holacracy is an alternative organizational structure that distributes authority and decision-making throughout self-organizing teams or circles. It is designed to promote transparency, adaptability, and employee empowerment. However, it may be challenging to implement and sustain, particularly in large, traditional organizations.

Each organizational structure approach has its pros and cons, the different approaches give you different levels of complexity, the more complex you make it, the more significant the planning, maintenance, and changes will be. 

## Organization Structure Implementation Strategy
When configuring Hornbill to support your organization, you have a choice of a number of different approaches to defining your organizational structure in Hornbill.  Different solutions will more precisely define the exact approach, what we are describing here is the Hornbill ESP platform capabilities. 

- __Single Company__: With this approach you define a simple top-level OU of type "company", and avoid using child OU items, and instead just define a single list of teams. You define a single top-level Company OU, and then define a flat list of assignment teams beneath the top-level company. 
- __Hierarchical__: For organizations that have more complex, multi-level team structures, in this mode, you can define one or more top-level company OU's and, beneath each company OU, you can define any number of teams within that company, and teams can optionally have child teams as required. 
- __Organizational__: For organizations that have really complex, multi-level company/divisional and organizational structures where you want to represent the organizational structure making use of the full range of organizational unit (OU) types and an unlimited depth hierarchical structure, where you can inter-mix non-functional OU's and teams as you need, then this more advanced approach may well be the the right choice. 

This is an important choice you really need to make early on when deploying Hornbill into your organization, please ensure you read our [Best Practice Guide for Defining Your Org Structure](/esp-fundamentals/best-practice/org-structure) before making your choice. Its worth remembering that just because you can do something does not mean you always should, and this applies when it comes to mapping your organizational structure in Hornbill. 


## Organizational Units (OU's)
In Hornbill, an organizational structure is made up of a tree-like hierarchy of Organizational Units (OU's) where each node on the tree as an OU, and each OU can contain child OU's.  There are two types of OU's, which are General and Functional.   Users can be added as a member to one or more OU's providing the flexibility to build one or more organizational structures, for example, line of report/org chart, cross-functional teams, or you can model a simple flat structure of Team OU's and assignment OU's. 

### User Assignment
For the purpose of Hornbill's Organizational Structure, there are two types of users, Full Users and Basic Users. To find out more about these types of users and their differences please refer to [User Account Types](/esp-fundamentals/security/user-accounts#account-types)

### General Organizational Unit (OU) Types
The following types of organizational units are available in Hornbill to help you define your organizational structure. These general types are only used for organizing your users into a browsable structure, and have no specific functional purpose beyond that.  

|OU Type|Description|
|:---|:---|
|department|A division of an organization responsible for a specific function or task, such as human resources, finance, marketing, or sales.|
|costcenter|A cost center is an alternative type of department or unit within an organization that is responsible for incurring costs but does not directly generate revenue. The primary function of a cost center is to support the overall operations of the organization by providing essential services, such as IT, human resources, or administrative support.|
|division|A larger unit of an organization that includes multiple departments or teams, often organized around a product line or geographic region.|
|company|<span style="white-space: nowrap;">```Single Company``` <small>(only one top-level)</small></span><br><br>```Hierarchical``` or ```Organizational``` (multiple top-level and/or nested)|A company is typically a group that provides goods or services, generate revenue, create jobs, manage resources, innovate and adapt, and report to stakeholders. The success of the company is often measured by its ability to achieve these objectives in a sustainable and responsible manner. In a typical organizational structure, a company is often at the very top of the structure|
|businessUnit|A self-contained unit within an organization that operates as a separate entity, often with its own profit and loss responsibility.|
|directorate|A Directorate is a group of senior managers who are responsible for the overall strategic direction and management of a specific area within an organization. The term "Directorate" is often used in government organizations and large corporations.|
|branch|A location of an organization that operates independently but is part of a larger entity, such as a bank branch or retail store.|
|board|A group of individuals who oversee the strategic direction of an organization, often made up of external stakeholders or directors.|
|subsidiary|A subsidiary is a separate legal entity that is owned and controlled by another company, known as the parent company. The subsidiary operates as an independent company with its own management, finances, and legal structure. The parent company may own all or a majority of the subsidiary's shares, giving it control over the subsidiary's operations.|
|function|A specific area of expertise or responsibility within an organization, such as IT, legal, or procurement.|
|general|Where no other OU type fits, this type can be used as part of your organizational structure.  If you find yourself having to use this type, we encourage you to start a conversation on our community forums so we may consider expanding the available organizational unit types in Hornbill|

### Functional Organizational Unit (OU) Types
Functional Organizational Unit (OU) type are available in Hornbill, not only to help you define your organizational structure but they also define the functional grouping of users.  Functional OU's have additional "functional" behavior over and above General OU's, specifically, the assignment of tasks can be made to a functional OU, but not general OU types.  Other applications on the Hornbill Platform may also use functional OU types for assignment and other functional behaviors that are beyond the scope of the Hornbill platform itself.  For specific application behaviors around functional OUs, please refer to the applications specific documentation.  

:::note
When adding users as to your organizational structure, you can add any users or basic users as a member to any OU; but with the one exception that basic users cannot be added as members to functional OU's 
:::

|OU Type|Description|
|:---|:---|
|team|A group of individuals who work together to achieve a common goal, such as a project team, research team, or customer service team.|

Please also see [Human Tasks](/esp-fundamentals/core-capabilities/human-tasks) for more details on how Functional OU types are used and how assignment relates to your Organizational and Groups structure
