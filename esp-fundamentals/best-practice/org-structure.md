# Defining You Organizational Structure

It is possible to map almost any organization structure within Hornbill. The organization structure can be hierarchial and can include functional and non-functional organizational unit types.  To read more about the capabilities of the Hornbill platform in relation to defining your organizational structure, please see the document [Fundamentals : Organization And Team Structure](/esp-fundamentals/core-capabilities/organization-and-teams)

While on the face of it, being able fully map your org structure in Hornbill (or any other tool where you could do the same) seems like a really good idea, based on our own experience deploying 1000's of complex service management solutions into a diverse range of organization types and sizes, and over a more than 25 years, mapping an organizational structure into a product can be challenging due to several reasons:

- __Complexity of Organizational Structures__: Organizations can have intricate and multifaceted structures, including various departments, teams, roles, and reporting relationships. Translating this complexity into a product's design and functionality can be difficult, as the product must accommodate various levels of hierarchy and interactions.

- __Constant Changes__: Organizational structures are not static; they often undergo changes due to growth, restructuring, mergers, or other factors. Incorporating these dynamic changes into a product requires flexibility in design and coding to ensure that the product remains aligned with the evolving organizational structure.

- __Differing Information Needs__: Different stakeholders within an organization require varying levels of detail and access to information. Balancing these needs while designing a product can be challenging. Some users might need a high-level overview of the structure, while others require granular details about specific roles and relationships.

- __Integration with Existing Systems__: Many organizations already have software tools and systems in place to manage their organizational structure and HR processes. Integrating a new product with these existing systems can be complex and require a deep understanding of data exchange, synchronization, and interoperability when it comes to different org structure implementations.

- __User Experience Design__: Designing an org structure that effectively represents the organizational structure while maintaining a user-friendly and intuitive interface can be a challenge. Balancing the need for visual clarity with a clean and organized interface requires careful consideration of design principles.

- __Scalability__: As organizations grow, the number of employees, teams, and departments can increase significantly. Designing a product that can handle a large-scale organizational structure without compromising performance is a significant technical challenge.

- __Cultural and Workflow Variations__: Different organizations have unique cultures, workflows, and ways of organizing their teams. Designing a data structure that accommodates these variations while still providing a consistent experience can be complex.

- __User Adoption and Training__: Introducing a new product to an organization involves user adoption and training efforts. Users need to understand how to use the product effectively to navigate the organizational structure and for assignments, and access to relevant information.

- __Feedback and Iteration__: Designing a product for an organizational structure is an iterative process that requires ongoing feedback from users. Adapting the product based on user feedback and changing requirements can be challenging and cause significant data impact in terms of managing these changes.

Overall, mapping an organizational structure into Hornbill requires a deep understanding of both organizational dynamics and software functionality. It demands careful consideration of user needs, security concerns, scalability, and design principles to create a product that effectively serves the organization's goals. So, for most organizations using Hornbill, trying to map your actual organizational structure in Hornbill is not a good idea, and can cause a lot of problems further on in your implementation and use if you do not get this right up front. 

## Things you should definitely know before setting up your organizational structure in Hornbill
- The __Hierarchical__ mode is complex and difficult to get right, generally speaking, organizations are far too dynamic, changing too much and too often to tolerate the ridged definition of a hierarchical org structure in any transactional system with creating a significancy large overhead to manage those changes.
- It is possible to switch between these modes at any time.  However, while switching from __Simple__ to __Hierarchical__ mode is trivial, its very difficult, bordering on completely impractical to switch from __Hierarchical__ to __Simple__ mode.
- In Hornbill, Organizational units have ID's, once you start using these, these ID's are stored as referenced in many parts of the database.  In Simple mode, these are singular values so from a referential integrity point of view are relatively simple to deal with changes of these ID's. In __Hierarchical__ mode, these ID's look like paths AAA/BBB/CCC/ type thing, so in this example, renaming the OU BBB becomes very difficult because of the impact that will have across your data sets. 

## Best practice guidance for setting up your organizational structure in Hornbill
- If at all possible, use the __Simple__ org structure mode instead of the __Hierarchical__ mode for your organizational structure. While __Simple__ mode allows you to create and work with a single organization and a flat list of teams, departments and cost centers, while the __Hierarchical__ mode provides the ability for you to map very complex multi-company hierarchical structures.  __Simple__ mode should be sufficient for almost all organizations and should be your default choice if at all possible, think very carefully about trying to work with __Hierarchical__ mode, because that introduces a significant level of complexity and management overhead to deal with.
- Keep things simple, you should remember that your organization will change, and quicker than you might expect, if you map a complex structure you will find yourself having to change things often to keep up, or observe the org structure in use become more and more outdated as time goes on. 
- The way you or anyone else sees your organizational structure in relation to the work they do, will be different, which is basically to say, in real life, your perspective will change the way the organizational structure appears, or has to has to appear to make sense in any given context. Trying to map that to one global version of the truth simply does not work in almost all cases.  What you need to do is find the simplest, lowest common denominator that will make sense from the perspective of all users and teams using the system where the organizational structure will be presented. 
- Start Simple, no matter how well you feel you know your own structure, you will almost certainly find use cases where your perception does not make sense. So always start simple, use the __Simple__ mode described above if you possibly can.  


