# Subscription Model

Hornbill is a cloud platform for work management, productivity, collaboration, workflow, orchestration, automation and integration. Hornbill applications, such as Service Manager, Collaboration, Board Manager, Document Manager, Customer Manager and others, run on the Hornbill Platform and use common platform services.

This page explains the structure of the Hornbill subscription model. It does not provide current pricing. For current pricing, contact your Hornbill account team.

## Subscription Model In Principle

Hornbill's subscription model is based on the value provided to people who use Hornbill to deliver services and participate in workflows.

In general:

- Internal employees using Basic User Access and external users using Guest Access do not require a paid subscription for that access.
- People who use Hornbill to provide services, administer services, manage work, participate in workflow activities, or use application capabilities as part of service delivery generally require a paid subscription.
- Platform access and application access are separate considerations. A user may require a Hornbill Platform subscription, an application subscription, or both, depending on what they do.
- Some applications are included for subscribed platform users, while others require an additional application subscription.
- Where an application offers both named and concurrent subscriptions, those are two ways of subscribing to the same application capability.

Hornbill customers should only pay for what they need. Subscription levels can usually be increased or decreased as requirements change, subject to the terms of the customer's subscription agreement.

## Platform And Application Subscriptions

The Hornbill Platform provides the core services that Hornbill applications run on, including authentication, security, workflow, data, audit and application enablement.

Applications build on the platform. Each application defines its own subscription model, which may include free access, named subscriptions, concurrent subscriptions, application-level subscriptions, user-level subscriptions, or optional add-ons.

You should review the subscription model for each Hornbill application you plan to use. Each application should explain how its subscription extends or depends on the Hornbill Platform subscription model.

## Platform Access Types

At the platform level, access for people who are not Hornbill application users is provided through __Basic User Access__ for internal employees and __Guest Access__ for external users, such as customers, consumers or citizens. Individual applications may use application-specific terms for these access patterns. For example, Service Manager refers to some of these people as __Self-Service Users__, while another application might use Guest Access for a community forum or another external-facing experience.

For more information, see [Hornbill Platform User Accounts](/esp-fundamentals/security/user-accounts).

|Feature/Module|Basic|User|
|:--|:--:|:--:|
|Employee Portal / Service Catalog|Yes|Yes|
|Secure access to the platform User and Mobile applications|No|Yes|
|Desktop and Mobile Notifications|No|Yes|
|Email / Shared Mailboxes|No|Yes|
|Tasks and Authorizations|No|Yes|
|Productivity Tools and Features|No|Yes|
|Basic User Profile|Yes|Yes|
|Advanced User Profile|No|Yes|
|Co-Worker Directory|No|Yes|
|News Feed|No|Yes|
|Hornbill Applications (as User)|No|Yes|

__Guest Access__ is intended for external users, such as customers, consumers or citizens, who access Hornbill through guest or customer-facing areas. Guest Access does not require a paid platform subscription for that use.

__Basic User Access__ is intended primarily for internal employees who are not Hornbill application users, but who need limited access to employee-facing areas of Hornbill. Basic users do not require a paid platform subscription for that access.

__User__ accounts are named platform users. A Platform User subscription is required for individuals who need the platform capabilities used to deliver, administer or participate in work, such as workflow tasks, approvals, collaboration, notifications, application access, administration or service ownership.

Platform User subscriptions are always named. They are assigned to named individuals, not shared between people.

## Application Subscriptions

Some Hornbill applications are free for Platform Users to use. Other applications require an additional application subscription. Application subscriptions are independent of, and may be in addition to, the Platform User subscription.

When an application requires a subscription for people who use that application to deliver or manage services, those users must also have the appropriate Hornbill Platform User subscription.

Application subscriptions may be offered on a named basis, a concurrent basis, or another model defined for that application.

## Named Application Subscriptions

A named application subscription is assigned to a specific user and provides that user with dedicated access to the subscribed application.

Named subscriptions are typically appropriate for core operational users who need guaranteed access to the application, such as full-time analysts, administrators, service owners or other dedicated roles.

## Concurrent Application Subscriptions

Some Hornbill applications may offer concurrent subscriptions. A concurrent subscription provides the same subscribed application capabilities as a named subscription for that application, but access is drawn from a shared pool rather than being permanently assigned to one person.

The concurrent model described here applies to any Hornbill application that supports concurrent subscriptions. The Service Manager pricing document uses Service Manager as the example, but the same platform model applies to other applications that offer concurrency.

Concurrent subscriptions are typically appropriate for occasional or intermittent application users, such as subject-matter experts, escalation contacts, specialist resources, part-time users or shift-based users who do not need continuous access.

Concurrent application users must also be Platform Users. A concurrent application subscription does not replace the requirement for a Platform User subscription.

## How Named And Concurrent Subscriptions Work Together

Named and concurrent subscriptions are two ways of subscribing to the same application where that application supports both models.

Customers can combine the two models:

- Use named subscriptions for users who require guaranteed access.
- Use concurrent subscriptions for a wider population of occasional users where shared pooled access is sufficient.

There is no fixed ratio between Platform Users, named application subscriptions and concurrent application subscriptions. Customers decide how many of each they need, subject to the subscription options offered for the application and the terms of their subscription agreement.

## How Concurrent Access Works

A concurrent subscription is allocated from the pool when all of the following are true:

1. The user is logged in as a Platform User.
2. The user intentionally opens the subscribed application, for example by selecting the application icon.
3. A concurrent subscription is available in the pool.

Allocation is always triggered by intentional user access to the application.

### Minimum Usage Period

Opening an application using a concurrent subscription starts a 120-minute minimum usage period.

The subscription is returned to the pool only after the 120-minute minimum usage period has elapsed and the user has intentionally logged out.

If the user logs out after the 120-minute minimum usage period has elapsed, the subscription is returned to the pool immediately.

If the user logs out before the 120-minute minimum usage period has elapsed, the subscription remains allocated until the minimum usage period ends. During that time, the same user can return to the application without starting a new minimum usage period.

It is the user's responsibility to log out intentionally when they have finished using the application. Concurrent subscriptions are not released by inactivity-based automatic logout.

### Pool Exhaustion

When all concurrent subscriptions in the pool have been allocated, additional users cannot access the application until a subscription is released back to the pool.

Users who cannot access the application because the pool is exhausted are shown a notification explaining this.

### Administrator Intervention

Where a user has not logged out and the 120-minute minimum usage period has elapsed, a system administrator can end the session and return that concurrent subscription to the pool. This administrator action cannot be automated.

## Sizing A Subscription

To size a Hornbill subscription, identify the following groups:

- __Basic and Guest Access users__: internal employees using Basic User Access and external users using Guest Access. Individual applications may use application-specific terms for these access patterns. This access is normally free of charge.
- __Platform Users__: named individuals who need authenticated platform access to deliver, administer, own or participate in work.
- __Named application users__: users who need guaranteed, dedicated access to a subscribed application.
- __Concurrent application users__: occasional or pooled users where shared access is sufficient because peak simultaneous usage is lower than the total number of potential users.

Named and concurrent application subscriptions are purchased in addition to Platform User subscriptions.

## Subscription Pricing Considerations

Hornbill subscription pricing can vary because enterprise customers have different user populations, application requirements, compliance needs and commercial arrangements.

The following considerations may apply:

|Consideration|Description|
|:--|:--|
|__User-Level Customization__|Organizations can subscribe users to the platform and applications they need, based on their role and responsibilities.|
|__Subscription Tiers__|Hornbill may offer different subscription tiers, such as Standard, Enterprise, Managed Service Provider or Government, depending on the application, region and commercial arrangement.|
|__Add-Ons and Optional Features__|Some capabilities may be offered as add-ons or optional features. These can be added to a subscription where required.|
|__Payment Model__|Hornbill is a business-to-business service and is generally billed as an annual subscription paid in advance.|
|__Scaling__|Subscription levels can generally be adjusted as needs change, subject to the customer's subscription agreement.|
|__User-Based Licensing__|Pricing is generally based on the business value delivered to people who use Hornbill to provide, manage or participate in services.|
|__Geographical Considerations__|Pricing may vary by region, including where services are delivered from regional data centers.|
|__Compliance and Security__|Organizations with specific compliance or security requirements may need subscription tiers or add-ons that include those capabilities.|

## Frequently Asked Questions

#### What is the basis for Hornbill's subscription pricing strategy?
>Hornbill's subscription pricing is based on the business value delivered through platform capabilities, applications, productivity tools and workflow automation.

#### What is the difference between a user and a customer?
>In this context, a user is someone who uses Hornbill to provide, manage, administer or participate in services and workflows. A customer is a recipient of those services. On the platform, internal employees who are not Hornbill application users typically use Basic User Access, while external users typically use Guest Access.

#### Do my end users or customers need a subscription to access Hornbill?
>Internal employees using Basic User Access and external customers using Guest Access do not normally require a paid subscription for that access.

#### Can a Hornbill user also be a customer?
>Yes. A person may use Hornbill to provide services in one context and consume services in another. For example, an IT analyst may use Service Manager to deliver IT support, while also using the Employee Portal to request HR services.

#### Are there different subscription tiers?
>Yes. Hornbill may offer different subscription tiers or commercial models depending on the application, customer requirements, region and subscription agreement.

#### Does Hornbill provide concurrent subscriptions?
>Yes, where an application supports concurrent subscriptions. Platform User subscriptions remain named and are not concurrent. Concurrent subscriptions apply at the application level and are purchased in addition to the required Platform User subscriptions.

#### How does concurrent access work?
>A concurrent subscription is allocated when a Platform User intentionally opens the subscribed application and a subscription is available in the pool. The allocation starts a 120-minute minimum usage period. The subscription is returned to the pool after that period has elapsed and the user has intentionally logged out.

#### Is concurrent access released automatically when a user is inactive?
>No. Concurrent subscriptions are not released by inactivity-based automatic logout. The user must intentionally log out. If the 120-minute minimum usage period has elapsed and the user has not logged out, a system administrator can end the session and return the subscription to the pool. This administrator action cannot be automated.

#### What happens when all concurrent subscriptions are in use?
>Additional users cannot access the subscribed application until a concurrent subscription is released back to the pool. Those users are shown a notification explaining that access is not currently available.

#### Can I mix named and concurrent subscriptions?
>Yes, where the application offers both models. Named subscriptions are suitable for users who need guaranteed access. Concurrent subscriptions are suitable for occasional or pooled users where shared access is sufficient.

#### Can I create my own subscription sharing or infrequent-user scheme using APIs or automation?
>No. APIs and automation capabilities are provided to support operational efficiency, not to bypass subscription requirements. Users who participate in service delivery or use subscribed application capabilities must have the subscriptions required by the applicable subscription model.

#### How often can subscriptions be scaled or adjusted?
>Subscriptions can generally be scaled up or down in line with the terms of the customer's subscription agreement.

#### How are Hornbill subscriptions billed?
>Hornbill is generally billed on a commercial invoice as an annual subscription paid in advance.

#### How do I find current pricing?
>Current pricing is provided through engagement with Hornbill's commercial team or your Hornbill account team.

#### Does Hornbill offer discounts?
>Hornbill aims to price fairly, consistently and transparently. Any discounting or commercial variation is handled through the applicable commercial process and subscription agreement.

#### What happens if Hornbill increases subscription pricing?
>Subscription pricing during an agreed term is governed by the customer's subscription agreement. Additional subscriptions added during that term are generally based on the pricing agreed for that term, unless the subscription agreement states otherwise.

#### How do I add or remove subscriptions?
>Subscription changes are handled in accordance with the customer's subscription agreement. An authoritative customer contact should raise the request through the Hornbill Success Portal. Hornbill will provide the relevant subscription change documentation and apply any agreed changes.

#### Can free-tier limits be increased?
>Free-tier limits are generally fixed. Where a customer needs to evaluate beyond those limits, Hornbill may be able to provide a short-term evaluation of the relevant app or module through the customer success process.
