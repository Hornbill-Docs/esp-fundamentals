# Hornbill Platform Security Model
It is important to understand that the Hornbill Platform has a comprehensive and very granular security model built into to its foundation. The platform is designed to be used by the enterprise, and as such data and system security features need to be flexible enough to allow each organization to manage its security policies as needed.   
 
All interactions with Hornbill are done under the supervision of a [Security Context](#Security Context) which ensures each action is subject to security checks against the rights allocated to a specific user account. Even if an API call does not require any specific security validation, behind the scenes, all API calls from all devices and API channels is still treated in this way. verified through a specific user account. 

For security checks there are four classes of account, these are known as: - 

- User Accounts
- Portal Accounts
- Guest Accounts
- System Accounts

__User Accounts__ are as you might expect, for normal users that will log into the Hornbill platform. So for every User, there will be an associated user account. A user can log into Hornbill using the login credentials associated with a user account. 

__Portal Accounts__ are another special type of account which provide a security context that is applied applied to guest logins that log into the Customer and other external contact portals. 

__Guest Accounts__ are not strictly "accounts" so warrant their own, more detailed explanation in the [Guest Accounts](#Guestt%20Accounts) section below.

__System Accounts__ implicitly exist as part of the platform. System accounts cannot be logged into, interacted with or changed in any way. They are defined to allow the platform to perform background tasks and functions required to make the platform and applications operate in the areas where there is no interactive user. Typically, system tasks, background tasks and jobs, integrations and inter-process communications are all examples of where system accounts are used.  As a system administrator you really do not need to worry about these, its just useful to be aware they exist.  System accounts have an ID that always begins with SYS_xxx


## Security Context
In all cases, in order for any API call to work, you first need to establish a valid security context. There are various ways to create a security context, logging in interactively, using API keys, Single-Sign-On etc. All of these different mechanisms lead to the creation of a security context which is then uses as the security container for subsequent interactions with the system.  Once a security context exists, that is considered a User Session, and as is typical of any login scheme, the established session will generally remain persistent in accordance with the session management and timeout rules, once the user loggs out, or the session is otherwise closed, the session and security context are destroyed.

# Login and Account Types
The Hornbill Platform provides the ability for different classes of users to access different areas of the system.  Under the hood, all users are subject to strict security controls, but different classes of user require very different access controls to be applied.  In essence there are three types of "user" that can access the Hornbill platform, these are called `user`, `basic` and `guest`. 

The Hornbill Platform is, at its core, a workflow automation and digital enablement tool, designed to help organizations to digitize and automate workflows. Users of the Hornbill platform are generally considered to be participating in the provision of service to users or customers, or are in receipt of/consume services being provided.

In broad terms, there are two categories of users.  The first category are users who are involved in the day-to-day work of providing service to others, we refer to these as service providers.  These types of users typically use Hornbill on a day to day basis to facilitate providing service to either Employees or Customers who will also interact with the Hornbill Platform. 

The second category of users are employees and/or customers, who are typically individuals, although can be organizations, who are the recipients, or consumers of the service(s) being provided, including the consumption of services through various types of self-service portals, integrations or automation's.  Often, a Hornbill Service Provider User can also be a Service Consumer, this is fairly typical use case in terms of Enterprise Service Management for Employees. 

|Account Type|Service Type|Description|
|:---|---|---|
|`system`|n/a|System accounts are special internal accounts that enable the system to function. These accounts are allocated allocated by the system and cannot be changed/edited/deleted. System accounts are also inaccessible for logins of any type or other uses.|
|`user`|_see below_|A user account is any individual person or system that has a dedicated account on the Hornbill Platform that can be logged into to gain access to the Hornbill Platform facilities and functions.  The purpose of an "account" on the Hornbill Platform is to act as a security container for interaction with the systems functions. In other words, the **only** way you can get access to any part of the system is _through_ a defined account,  There are three sub-categories of users, those being `full`,  `basic` and `portal` (see below for description)
|`user/full`|Service Provider<br><br>Consumer|This is the user type that would log into Hornbill and use it on a day to day basis as a tool and management system that enables them to provide/deliver the services being provided to others. When we talk about a `subscriber` to Hornbill, they are classed generally as a __user__ of the system. In a typical ESM setting, full users are also Consumers of services being provided|
|`user/basic`|Consumer|This type of user account is equivalent to a normal 'user' account, but, with very reduced access to the features of the system.  A `basic` user can easily be promoted to a `full` user, and visa versa, the fundamental difference between a `full` user and a `basic` user is, a full user requires a subscription to use the main features of the Hornbill Platform and its applications, while a basic user does not require a specific subscription but only gets very limited access to the systems functionality. 
|`user/portal`|Consumer|This is a special system account that cannot be logged into directly. This account type provides security access control to guests logging into, or accessingHornbill via a guest portal.  When accessing the Hornbill Platform via one of its guest portals or mobile applications, all guest logins get the same basic security controls applied to their session, that are defined by the portal account|
|`guest`|Consumer|A guest user is another class of person that may log in, or otherwise access Hornbill through a guest portal or system. Guests are considered Service Consumers, and therefore have very limited access to the Hornbill Platform features. Typically, guests are individual users who are external to the organization, for example, customers, consumers, citizens etc.  There are two sub-categories of guest accounts, being 'anonymous' or 'authenticated'. See descriptions below |
|`guest/anonymous`|Consumer|This type of guest is a person interacting with the Hornbill platform, typically through a portal or integration of some sort, were the user is unknown to, and unauthenticated on the Hornbill Platform.  The most basic example of this this is when a guest who needs to access the customer self-service portal enters the URL and is greeted with the Login Page.  At this point, without logging in, that user may, for example have very limited access to some knowledge or FAQ's or other basic functions that do not require a login in order to access. These interactions are know to the system as access by an `anonymous` guest|
|`guest/authenticated`|Consumer|In the context of the guest portal, an authenticated guest is an individual who has successfully identified themselves as a known individual, typically this means they have a record in the Hornbill '''Contacts''' database and have authenticated/registered against that contact record.|


## Guest Accounts
When we refer to a guest account, we are referring to a Contact Login via a portal.  The typical use-case fo the guest portal is for providing support and other services to people who are "external" to your own organization. A user is able to use the external facing customer portal (depending on configuration options set)