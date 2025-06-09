# Human Tasks

Human tasks refer to specific steps or actions within a workflow that requires specific human intervention, decision-making, or input. These tasks are generally integrated into automated workflows to ensure that complex processes can be managed effectively while still taking advantage of automation for repetitive, time-consuming, or mundane tasks.

Human tasks are essential components of a workflow because they:

- __Bring human expertise and judgment into the process__: Certain tasks demand human insight, critical thinking, or subjective evaluation, which cannot be effectively automated. Human tasks ensure that the necessary human element is incorporated into the workflow.

- __Facilitate approvals and authorizations__: In many business processes, approvals and authorizations from specific individuals or departments are necessary. The workflow system enables human tasks and approvals to be integrated seamlessly into the workflow, ensuring that the process adheres to organizational policies and guidelines.

- __Enhance collaboration and communication__: Human tasks can foster collaboration and communication among team members by assigning tasks to specific individuals, prompting them to contribute to the process or review and provide feedback on the work of others.

- __Manage exceptions and contingencies__: In cases where a workflow encounters an exception or unforeseen circumstance, a human task can be used to alert relevant personnel, who can then assess the situation and take appropriate action.

- __Provide flexibility and adaptability__: As business needs and processes evolve, human tasks allow for the easy adaptation of workflows, making it simple to add, modify, or remove steps that require human involvement.

Human tasks play a vital role in workflow automation by bridging the gap between automation and human expertise. They ensure that processes run smoothly and effectively while still leveraging the benefits of automation for efficiency and productivity gains.

## Human Task Core Capabilities

A human task on the Hornbill platform has a significant number of capabilities that cater for various use cases and workflow requirements.  By design, human tasks are flexible in order to provide support and usefulness to the widest range of needs. 

Human task core capabilities include:

- Subject and Description
- Due Date
- Time Spent / Billable
- Prioritization
- Categorization
- Start Date / Due Date / Due Duration
- Schedule / Recurring
- Expiry
- Progress
- Assignment & Ownership
- Private Tasks
- Reminders
- And more...


There are two major categories of human task: manually created and automatically created.

### Manually Created Human Tasks

A manually created human task, is, as its name would suggest, a task that is created manually by an individual, in order to assign a task to someone.  This can be as simple as you creating a task for yourself, such as a reminder to carry out a specific task at some point in the future. Or, as a team leader, you many want to create a task for someone else to get something done. Manually created tasks are commonly found in all sorts of applications, from stand-alone to-do type tools, or tasks in Microsoft Outlook, or tasks in project management tools. The Hornbill platform allows you to manually create and assign tasks to individual users or teams. 

__Advantages:__

- Allows for greater flexibility and customization in defining tasks as and when needed.
- Enables the creation of tasks based on specific requirements or unique situations.
- Facilitates human input and decision-making in task creation.

__Disadvantages:__

- Will be time-consuming, and even wholely impractical, especially for large projects or workflows with numerous tasks.
- Prone to human error, such as typos or inconsistencies in task descriptions and assignments.
- Lacks efficiency in handling repetitive tasks (beyond repetitive scheduling) or processes that follow a pattern.


### Automatically Created Human Tasks

Automatic task creation, involves the automatic generation of tasks within a workflow or project through predefined rules, triggers, or conditions in an automation system or workflow management tool. This method is typically employed for processes that are repetitive and/or predictable or that are part of a larger, well-defined, and specific pattern or sequence of activities. 

__Advantages:__

- Saves time and effort by automating the creation of repetitive or predictable tasks.
- Reduces the likelihood of human error and inconsistencies in task definitions.
- Streamlines processes and enhances overall productivity and efficiency.

__Disadvantages:__

- May not be suitable in some cases, such as for tasks requiring human judgment, customization, or unique input.
- Could lead to rigidity in task creation if the automation rules or conditions are not flexible or adaptable.
- May require initial setup time and effort to configure automation rules, triggers, or conditions.

:::tip
A crucial difference between manually created and automatically created human tasks is that tasks generated automatically typically have an immutable reference linking them to their original source, such as an orchestrated workflow or project. This connection serves to identify the task as being part of a specific origin and enables the task's completion status to be reported back to the originating source.
:::

### Automatic Task Creation Origins

Automatic task creation in Hornbill can originate from numerous sources. 

Individual applications, for example Project Manager, will create and assign human tasks as part of running a project. These tasks are said to "belong" to the project, but are assigned to one or more humans for completion. 

Hornbill's workflow orchestration is the primary source of human task generation. (Read more about [Hornbill Workflow Orchestration](/esp-fundamentals/core-capabilities/workflow-orchestration).) In summary, workflow orchestration is the process of coordinating, organizing, and managing various tasks, resources, and systems within a business process to achieve a desired outcome. It involves automating tasks, sequencing activities, orchestrating human activity, and integrating tools, systems and applications to ensure seamless execution and delivery of the workflow.

One of the primary characteristics of human tasks that originate from workflow orchestration in Hornbill is the notion of *outcomes*. In general terms, human task outcomes refer to the results or consequences that emerge from the completion of tasks requiring human intervention within a workflow. These outcomes are typically characterized by the decisions, actions, or judgments made by individuals while performing their assigned tasks. Human task outcomes play a critical role in shaping the overall progression, flow, and outcomes of a workflow. 

Some common aspects of human task outcomes include:

- __Decision-making__: Human task outcomes often involve making decisions, such as approvals, rejections, or choosing between multiple options. These decisions can directly impact the subsequent steps in a workflow and determine the final outcome.

- __Quality and accuracy__: Human task outcomes contribute to the overall quality and accuracy of the process, especially when tasks require subjective evaluations or assessments based on expertise and experience.

- __Collaboration and communication__: Human task outcomes can facilitate collaboration and communication among team members by providing opportunities to discuss, review, or share feedback on specific tasks or aspects of the workflow.

- __Problem-solving and exception handling__: Human task outcomes play a vital role in resolving issues or handling exceptions that may arise during a workflow, as they allow for human intervention and assessment of the situation.

- __Adaptability and flexibility__: Human task outcomes contribute to the adaptability and flexibility of a workflow by enabling adjustments, modifications, or refinements based on individual input, feedback, or changing circumstances, and on a case-by-case basis.

## Task Outcome Capabilities 

While manually created tasks are either open or complete, automatically created tasks typically have one or more outcomes. In the context of Workflow Orchestration, outcomes are a very important and powerful capability as the outcome of a task can be used to drive the direction and flow of a workflow.  There are a number of key capabilities with regards to task outcomes.  These are: 

- __Outcome options__: A human task can provide up to 8 unique outcomes, with a single outcome being selected upon task completion. These outcome choices are typically presented as 1-8 buttons for the user to choose from when completing the task. These outcomes are fully customizable, even down to each individual task if needs be, allowing the individual user completing the task to provide precise and highly relevant completion outcomes.

- __Required information__: Any task can be configured to capture additional information from the person completing the task.  This additional information can be captured using any number of custom fields, text inputs, drop-downs and other form-style input options. Fields can be mandatory or optional, and they can enforce data quality using input validation.

- __Outcome-specific required information__: You can also require additional information on a per-outcome basis, meaning that each individual outcome can request extra, outcome-specific information. This allows for a more granular approach in gathering data during task completion. Similar to the general task configuration, these outcome-specific fields can be designated as either optional or mandatory, and input validation can be applied to ensure data quality before the task is marked as completed. This feature provides an even more thorough understanding of the outcome-based nuances in the task completion process.

Outcomes and additional information collected can all be used by the workflow orchestrator to drive the flow and direction of the workflow's onwards path. 


## Approvals

On the Hornbill platform, an Approval is a special type of human task, specifically tailored to obtain approval or authorization within a workflow orchestration. These differ from general human tasks that are completed by a single individual. Approvals often involve more than one person, can require consensus, and can better deal with the complexities of individual availability and authority levels.

Approvals not only possess a more defined set of outcomes but also offer additional functionality to facilitate approval through voting, consensus weighting, or individual authority. This enables a more versatile and adaptive approach to securing approval in various situations.

In simpler use cases where an Approval only requires a single individual (or nominated delegate) to complete, a standard human task is simpler to configure and may be perfectly sufficient. This flexibility allows organizations to manage and streamline approval processes within their workflows.

## Task Ownership

The ownership of a task is distinct conceptually from the assignment of the task. In the case of a manually created task, for example, a manager creates a task to be done, but this task will be assigned to someone on the manager's team. The manager is the *owner* of the task, while the individual or team the task has been assigned to complete is the *assignee* of the task. While it is often the case that the terms are used interchangeably, in Hornbill we would say the assignee is *assigned the responsibility* to complete the task, while the owner of the task is typically the task originator.

## Task Assignment

Task assignment is a critical capability when working with human tasks as part of a workflow orchestration. On the Hornbill platform, to assign a task means *the responsibility to complete the task* has been assigned to an individual or team; this is not the same as being given ownership of the task. In most situations, the specific individual who should complete a task would generally not be known at process design time, or even if they were known, that person could be unavailable (for example on leave or sick) at some point in the future when a human task is created and assigned to them for completion.

Task assignment is flexible. A task can be assigned to:

- __an individual user__: Any full user (see [User Account Types](/esp-fundamentals/security/user-accounts#user-account-types) to read more about account types) can have tasks assigned to them. It should be noted that it's possible for a user to be a member of more than one Assignment Team and/or Assignment Role. Therefore when assigning a task to an individual user, it may be required that you assign the task to the user, _in the context of_ a specific team or role. Why you might need to do this is discussed in further detail below in [Assignment Context](/esp-fundamentals/core-capabilities/human-tasks#assignment-context).

- __a team__: When a team is defined with the _Allow Task Assignment_ option set, you have created an "Assignment Team" making it possible for a task to be assigned to this team. Each team will have zero, one, or more associated users. When associating a user to a team, there are a number of task-related controls that can be applied to each user within the context of that team. See [Team User Association & Task Controls](/esp-fundamentals/core-capabilities/human-tasks#team-user-association-and-task-assignment-controls).

- __a functional group__: When a functional group is defined with the _Allow Task Assignment_ option set, you have created an "Assignment Group" making it is possible for a task to be assigned to this group of people.  Each team will have zero, one, or more associated users. When associating a user to a team, there are a number of task-related controls that can be applied to each user within the context of that team. See [Team User Association & Task Controls](/esp-fundamentals/core-capabilities/human-tasks#team-user-association-and-task-assignment-controls).

- __a role__: It is possible to create custom roles, which can be used (if appropriately configured) for the purpose of task assignment. 

### Assignment Context
To accommodate the dynamic nature of organizations and the varying availability of individuals, task assignment within a workflow can be designed to cater to groups of people instead of solely assigning tasks to specific individuals. There are numerous use cases where assigning tasks to a group of people is beneficial, including the following examples:

- __delegated final assignment__: This approach is commonly employed when tasks are assigned to a team or functional group, allowing the team leader or manager to make the final assignment decision based on factors such as availability, priorities, and current situational requirements. 

- __self-assignment__: In this scenario, team members can view incoming tasks and "accept" one to work on, effectively self-assigning the task. 

- __task re-assignment__: This allows a team leader, manager, or current assignee to re-assign the task to another team member, either within the same group or in a different group. 

Many other situations may call for delegated or self-assignment capabilities. The rules governing who can perform specific actions in relation to assignment are typically set within the grouping container (team, functional group, or role) and may be determined on an individual basis. This accommodates the fact that a team of people often consists of individuals who play different roles, such as a manager, team leader, and members in that group.

It is common for an individual user to be a member of multiple assignment teams, functional groups, and roles simultaneously. This is where the concept of "context" becomes relevant. If the controls around who can perform specific actions in relation to assignment are determined by a combination of the container and user membership within that container, then for those controls to be logically applied and effective, a task generally needs to be assigned to a user "in the context" of an assignment team, functional group, or role. 

A suitable example of this concept can be found in the case of team assignment. Imagine a task being assigned to the "Development Team" for completion. The business process does not specify a particular member of the Development Team to complete the task; instead, it only requires someone within the team to do so. Upon arrival to the Development Team's queue, the team leader might be responsible for assigning the task to an individual. However, it would be undesirable for the team leader to assign the task to another team, such as the QA team. In this scenario, the team leader would be presented with limited assignment options, based on the constraints set in the team container and the team leader's membership within that team. This ensures that task responsibility remains within the appropriate team, while still offering some flexibility in assigning individual team members.

There are many other variations on how task assignment can be applied, so it's important to grasp the concept in Hornbill that when assigning a task, it's possible, and quite typical, that the task will be assigned to an individual in the "context" of an assignment team or role. 


### Team User Association and Task Assignment Controls
:::note
A team that works with tasks must have the '''Allow Task Assignment''' option enabled. 
:::

When adding a user to a team, there are controls that define how that user can interact  with tasks assigned to that team.
|User Task Options|Description|
|:---|:---|
|Can See Tasks|As a member, with this option set, a user can see tasks assigned to this team (read-only viewable) but cannot action or accept a task. Without this option set, the user will have no visibility of tasks assigned to the team. It is possible for the user to have a task assigned to them in the context of the team. Once assigned, the user will be able to action the task(s) in the team they have been specifically assigned.|
|Can Action Tasks|The user can action tasks assigned to the team but not yet assigned to a team user (unless a task is already assigned to them). This allows a member user to accept (assign the task to themselves) one or more tasks from the team queue.|

When a user is being added to an assignment team, each user is given an associated role within the team. Outside of tasks, this membership role serves informational purposes. The following membership roles are possible along with the task actions enabled. 

| |Member|Team Leader|Manager|
|:---|:---:|:---:|:---:|
|Can Accept Task From Queue|Yes|Yes|Yes|
|Can Assign Task To Member|No|Yes|Yes|
|Can Re-Assign Task From One Member to Another|No|Yes|Yes|
|Can Assign Task To Another Team|No|No|Yes|
|Can Edit Task Configuration|No|No|Yes|



## Defining Your Task Assignment Architecture
An essential aspect of defining your task assignment architecture is setting up an appropriate [Internal Groups & Team Structure](/esp-fundamentals/core-capabilities/internal-groups-and-teams). A strong correlation exists between lines of responsibility and the way you define your organizational structure, particularly in relation to assignment teams. If you are deploying a specific application, there may well be special consideration needed for the way in which the org structure needs to be defined. In this case, you should refer to documentation for that application to better understand how the [Internal Groups & Team Structure](/esp-fundamentals/core-capabilities/internal-groups-and-teams) will impact the way the application operates. 

Here are some general tips in relation to task assignments for creating your task assignment architecture:

1. __Define clear roles and responsibilities__: Ensure that each team member has a well-defined role and set of responsibilities within their assignment team. This will help avoid confusion and ensure that tasks are assigned to the most suitable individuals.
2. __Align your organizational structure with your assignment strategy__: Your organizational structure should reflect the needs of your assignment architecture. Make sure that your teams are organized in a way that supports efficient task assignment and delegation.
3. __Create flexible assignment options__: Allow for some flexibility in task assignment to accommodate variations in team members' availability, expertise, and workload. This can help ensure tasks are completed efficiently and on time, even in the face of unforeseen circumstances.
4. __Establish a clear escalation path__: In the event that a task cannot be completed by the assigned individual or team, have a well-defined escalation path in place to address any bottlenecks or issues that may arise.
5. __Monitor and review__: Regularly monitor and review your task assignment architecture to identify areas for improvement and optimize task allocation. This can help you maintain a high level of efficiency and effectiveness in your workflows.
6. __Communication and collaboration__: Encourage open communication and collaboration among team members to ensure that tasks are assigned and completed effectively. This can also help to foster a more positive and productive working environment.
7. __Simple is always best__: When implementing a new system, it's easy to be drawn into addressing every edge case, resulting in added complexity. Our recommendation is to maintain simplicity whenever possible. Remember that your organization's structure is not static and will evolve over time. A simpler implementation will be easier to adapt to future changes, ensuring a more efficient and flexible system.

By following these guidelines, you can create a task assignment architecture for your organization that is efficient, effective, and properly aligned with your organizational structure.
