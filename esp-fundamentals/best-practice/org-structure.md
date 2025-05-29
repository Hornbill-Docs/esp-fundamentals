# Defining Your Organizational Structure

It is possible to map almost any organization structure within Hornbill. The organization structure can be hierarchial and can include functional and non-functional organizational unit types.  To read more about the capabilities of the Hornbill platform in relation to defining your organizational structure, please see the document [Fundamentals : Internal Groups & Team Structure](/esp-fundamentals/core-capabilities/internal-groups-and-teams)

On the face of it, being able to fully map your org structure in Hornbill (or any other tool where you could do the same) seems like a really good idea. But based on our own experience deploying thousands of complex service management solutions into a diverse range of organization types and sizes, and over more than 25 years, mapping an organizational structure into a product can be challenging for a number of reasons:

- __Complexity of Organizational Structures__: Organizations can have intricate and multifaceted structures, including various departments, teams, roles, and reporting relationships. Translating this complexity into a product's design and functionality can be difficult, as the product must accommodate various levels of hierarchy and interactions.

- __Constant Changes__: Organizational structures are not static; they often undergo changes due to growth, restructuring, mergers, or other factors. Incorporating these dynamic changes into a product requires flexibility in design and coding to ensure that the product remains aligned with the evolving organizational structure.

- __Differing Information Needs__: Different stakeholders within an organization require varying levels of detail and access to information. Balancing these needs while designing a product can be challenging. Some users might need a high-level overview of the structure, while others require granular details about specific roles and relationships.

- __Integration with Existing Systems__: Many organizations already have software tools and systems in place to manage their organizational structure and HR processes. Integrating a new product with these existing systems can be complex; it requires a deep understanding of data exchange, synchronization, and interoperability when it comes to different org structure implementations.

- __User Experience Design__: Designing an org structure that effectively represents the organization while maintaining a user-friendly and intuitive interface can be a challenge. Balancing the need for visual clarity with a clean and organized interface requires careful consideration of design principles.

- __Scalability__: As organizations grow, the number of employees, teams, and departments can increase significantly. Designing a product that can handle a large-scale organizational structure without compromising performance is a significant technical challenge.

- __Cultural and Workflow Variations__: Different organizations have unique cultures, workflows, and ways of organizing their teams. Designing a data structure that accommodates these variations while still providing a consistent experience can be complex.

- __User Adoption and Training__: Introducing a new product to an organization involves user adoption and training efforts. Users need to understand how to use the product effectively to navigate the organizational structure and for assignments; they need access to relevant information.

- __Feedback and Iteration__: Designing a product for an organizational structure is an iterative process that requires ongoing feedback from users. Adapting the product based on user feedback and changing requirements can be challenging and can cause significant data impact in terms of managing these changes.

Overall, mapping an organizational structure into Hornbill requires a deep understanding of both organizational dynamics and software functionality. It demands careful consideration of user needs, security concerns, scalability, and design principles to create a product that effectively serves the organization's goals. So, for most organizations using Hornbill, trying to map your actual organizational structure in Hornbill is not a good idea, and can cause a lot of problems further on in your implementation and use if you do not get this right up front. 

## Keeping It Simple
Here is a brief outline of how to keep your org structure simple, by adopting a flat structure. 

1. Add one, and only one, company to your org structure at the top level. 
2. Create Child Departments and Cost Centers all at the top-level (these are used/required in other areas of Hornbill).
3. Create global flat lists of Assignment teams, again all at the top level. 
4. Keep it that way if you possibly can.


## Things you should definitely know before setting up your organizational structure in Hornbill
- It is very difficult to define a hierarchical org structure that gets it right. Generally speaking, organizations are far too dynamic, changing too much and too often to tolerate the rigid definition of a hierarchical org structure. In any transactional system, the more complex the structure is, the more likely it will need regular changes and therefore the larger the overhead to manage those changes in the future.
- In Hornbill, organizational units have IDs. Once you start using these, these IDs are stored and referenced in many parts of the database.  If you follow the guidance for keeping the structure simple, these are singular values. So, from a referential integrity point of view, it is relatively simple to deal with changes of these IDs. If you use a hierarchical structure, these IDs look like paths -- an AAA/BBB/CCC/ type thing. So in this example, renaming the organization unit 'BBB' in your structure becomes very difficult because of the impact that will have across your datasets. 

## Best-practice guidance for setting up your organizational structure in Hornbill
- If at all possible, use a simple, flat structure instead of the hierarchical approach for your organizational structure. A simple structure allows you to create and work with a single organization and a flat list of assignment teams, departments, and cost centers. On the other hand, using a hierarchical structure provides the ability for you to map very complex multi-company hierarchical structures.  A simple flat structure should be sufficient for almost all organizations and should be your default choice if at all possible. Think very carefully about trying to work with a hierarchical structure, because that introduces a significant level of complexity and management overhead that will need dealing with.
- Keep things simple. Remember that your organization will change, and quicker than you might expect. So even if you do map a hierarchical structure, try to keep that structure as simple and as functional as possible, because you will find yourself having to change things often to keep up. Or you will observe as the org structure in use becomes more and more outdated as time goes on. 
- The way you or anyone else sees your organizational structure in relation to the work they do will be different. This is to say, your perspective will change the way the organizational structure appears, and has to appear to make sense in any given context. Trying to map that to one global version of the truth simply does not work in almost all cases.  What you need to do is find the simplest, lowest common denominator that will make sense from the perspective of all users and teams using the system where the organizational structure will be presented. 
- Start simple, no matter how well you feel you know your own structure. You will almost certainly find use cases where your perception does not make sense. So always start simple, use the simple flat model described above if you possibly can.