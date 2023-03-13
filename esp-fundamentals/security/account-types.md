# Hornbill Platform Security Model
The platform is designed to be used within enterprise organizations, a key capability is a security model that delivers data and system security features that are flexible enough to support the most stringent of security controls to support any organization.   
 

## Security Controls
Each system and user account is allocated a security context. The security context is made up of several elements which provide fine-grained control over what a specific user account is allowed to do. 

All requests to the Hornbill service are processed under the supervision of a [Security Context](esp-fundamentals/security/account-types#Security Context) which ensures each action is subject to security checks against the rights allocated to a specific user account. Even if an API call does not require any specific security validation, behind the scenes, all API calls from all devices and API channels is still treated in this way. verified through a specific user account. 

For security checks there are four types of account, these are: - 

__User Accounts__ are as you might expect, for normal users that will log into the Hornbill platform. So for every User, there will be an associated user account. A user can log into Hornbill using the login credentials associated with a user account. 

__Portal Accounts__ are another special type of account which provide a security context that is applied applied to guest logins that log into the Customer and other external contact portals. 

__Guest Accounts__ are not strictly "accounts" so warrant their own, more detailed explanation in the [Guest Accounts](#Guestt%20Accounts) section below.

__System Accounts__ implicitly exist as part of the platform. System accounts cannot be logged into, interacted with or changed in any way. They are defined to allow the platform to perform background tasks and functions required to make the platform and applications operate in the areas where there is no interactive user. Typically, system tasks, background tasks and jobs, integrations and inter-process communications are all examples of where system accounts are used.  As a system administrator you really do not need to worry about these, its just useful to be aware they exist.  System accounts have an ID that always begins with SYS_xxx


### Privilege Level
The most fundamental security control applied to any account type is its Privilege Level. The following list shows the privilege level, ascending in access level:

|Privilege Level|Description|
|:---|:---|
|none|The security context has no privilege level assigned, generally means no session established.|
|guest|The security context is a guest, this is the security level applied to any `guest` account login via a customer/external portal session.|
|basic|This privilege level is associated with basic user accounts. Basic user privilege level provides very limited access to the Hornbill platform, typically this type of user would be an employee that does not use Hornbill on a day to day basis, but uses the Employee portal to access services being provided.|
|user|This privilege level is typically associated with a normal user account.|
|admin|This privilege level is in effect a 'super user' account. This privilege level is used sparingly, and should not be used for day to day user accounts.|


## Security Context
In order for any user interface or API call to work, a valid security context has to be established. There are various ways to create a security context, including logging in interactively, using API keys, Single-Sign-On etc. All of these different mechanisms lead to the creation of a security context bound to a session, which is then used as the security container for subsequent interactions with the system.  Once a security context exists, that is considered a User Session, and as is typical of any login scheme, the established session will generally remain persistent in accordance with the session management and timeout rules, once the user logs out, or the session is otherwise closed, the session and security context are destroyed.

# Account Types
The Hornbill Platform provides the ability for different classes of users to access different areas of the system.  Under the hood, all users are subject to strict security controls, but different classes of user require very different access controls to be applied.  In essence there are three types of "user" that can access the Hornbill platform, these are called `user`, `basic` and `guest`. 


|Account Type|Service Type|Description|
|:---|---|---|
|`system`|n/a|System accounts are special internal accounts that enable the system to function. These accounts are allocated allocated by the system and cannot be changed/edited/deleted. System accounts are also inaccessible for logins of any type or other uses.|
|`user`|see _User Account Types_ below|A user account is any individual person or system that has a dedicated account on the Hornbill Platform, that can be logged into in order to gain access to the Hornbill Platform facilities and functions.  The purpose of an _account_ on the Hornbill Platform is to act as a security container for interaction with the systems functions. In other words, the **only** way you can get access to any part of the system is _through_ a defined account,  There are three sub-categories of user account types, those being `full`,  `basic` and `portal` (see below for description)
|`guest`|Consumer|A guest user is another class of person that may log in, or otherwise access Hornbill through a guest portal or system. Guests are considered Service Consumers, and therefore have very limited access to the Hornbill Platform features. Typically, guests are individual users who are external to the organization, for example, customers, consumers, citizens etc.  There are two sub-categories of guest accounts, being 'anonymous' or 'authenticated'. See descriptions below |


## User Account Types
There are two categories of users.  The first category are users who are using Hornbill day-to-day providing service to others, we refer to these as service provider users.  These types of users, known as "full users" are typically providing service to others and are typically employees of the company using Hornbill. The Hornbill Platform is, at its core, a workflow automation and digital enablement tool, designed to help organizations to digitize and automate workflows. Users of the Hornbill platform are generally considered to be participating in the provision of service to users or customers, or are in receipt of/consume services being provided.

The second category of users are basic users, these are also typically employees of the organization, but do not directly use Hornbill to provide service to others, but are the recipients of the service being provided by full users. These users will also make use of self-service features of Hornbill, such as Employee Portal, mobile service catalog and so on.  


|User Account Sub-Type|Service Type|Description|
|:---|---|---|
|`user/full`|Service Provider<br><br>Consumer|This is the user type that would log into Hornbill and use it on a day to day basis as a tool and management system that enables them to provide/deliver the services being provided to others. When we talk about a `subscriber` to Hornbill, they are classed generally as a __user__ of the system. In a typical ESM setting, full users are also Consumers of services being provided|
|`user/basic`|Consumer|This type of user account is equivalent to a normal 'user' account, but, with very reduced access to the features of the system.  A `basic` user can easily be promoted to a `full` user, and visa versa, the fundamental difference between a `full` user and a `basic` user is, a full user requires a subscription to use the main features of the Hornbill Platform and its applications, while a basic user does not require a specific subscription but only gets very limited access to the systems functionality. 
|`user/portal`|Consumer|This is a special system account that cannot be logged into directly. This account type provides security access control to guests logging into, or accessingHornbill via a guest portal.  When accessing the Hornbill Platform via one of its guest portals or mobile applications, all guest logins get the same basic security controls applied to their session, that are defined by the portal account|

## Guest Accounts

When we refer to a guest account, we are referring to a Contact Login via a portal.  Guest are individual people, or sometimes just companies, who are *external* to your organization, who like basic users above, are being provided with support by full users of Hornbill.  Guest users typically log in through a Guest account who's credentials and information is defined in the "Contacts" database within Hornbill. In other words, in order for a Guest to be able to log into Hornbill, they need to have an entry in the contacts database, and, their credentials need to be set up accordingly. 

|Account Type|Service Type|Description|
|:---|---|---|
|`guest/anonymous`|Consumer|This type of guest is a person interacting with the Hornbill platform, typically through a portal or integration of some sort, were the user is unknown to, and unauthenticated on the Hornbill Platform.  The most basic example of this this is when a guest who needs to access the customer self-service portal enters the URL and is greeted with the Login Page.  At this point, without logging in, that user may, for example have very limited access to some knowledge or FAQ's or other basic functions that do not require a login in order to access. These interactions are known to the system as access by an `anonymous guest`|
|`guest/authenticated`|Consumer|In the context of a customer self-service portal, an authenticated guest is an individual who has successfully identified themselves as a known individual, typically this means they have a record in the Hornbill '''Contacts''' database and have authenticated/registered against that contact record.|

## Special User Account - admin

When an instance is provisioned, one default account is created and is configured with full system access (super-user), the login ID for this account is `admin`.  This account is typically used for initial setup of the instance, at least to the point where more specific user accounts are created for the purpose of administration.  The `admin` account cannot be deleted, but it can be disabled or reset with an unknown random password.  The `admin` account is the only account on your instance that the Hornbill Cloud team can reset for you to re-enable login should you lose the credentials or lose the ability for you to reset them yourself. 

