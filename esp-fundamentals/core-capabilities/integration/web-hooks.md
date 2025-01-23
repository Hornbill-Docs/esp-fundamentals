# Webhooks
Webhooks provide you a way to customize the database record operations relating to entities on the platform. The idea is, you can intercept and act on specific events, for example adding or updating a database record. You write your own custom script and have the Hornbill platform call that script. 

Webhooks allow different applications or services to communicate with each other in real time via HTTP callbacks. They provide a mechanism for one service to notify another about a specific event that has occurred, allowing the receiving service to immediately react to the event.

## How Webhooks Work

The following diagram shows the data flow of a typical record-oriented data transaction, with the blue boxes indicating where webhooks are able to plug into the transactional data flow. 

![Webhook Transaction](/_books/esp-fundamentals/core-capabilities/images/webhook.svg)


* __Event triggers__:  Webhooks are triggered by specific events, such as creating a new database record, updating a user, and so on. 

* __Event rules__:  Webhook rules are evaluated, and if a match is found, the webhook event is fired. 

* __Webhook call__: Once the event occurs, the Hornbill service sends an HTTP request to the URL specified for the webhook. 

* __Custom application__: Your custom web application that receives the webhook can then take action based on the data received in real time.  Webhooks deliver relevant data to other applications, meaning you get data immediately. The endpoints (URLs) are specific to each webhook and are registered to receive callbacks.

* __Real time__: Webhooks enable real-time processing and reactions to events as they give applications access to real-time data without relying on any type of polling mechanisms. In this way, webhooks are more efficient, because with polling, an application must continually check for new data.

* __Secure__: Webhooks should ensure that data is encrypted during transit using HTTPS to maintain data confidentiality.
Webhooks are widely used due to their efficiency, real-time processing capabilities, and ease of implementation. They are crucial in enabling integrations between disparate systems in today's highly connected digital ecosystem.

## Events
Entity events are defined on an application-by-application basis. While the basic operation of webhooks is the same regardless of any application, the data payloads provided in the payload of webhook calls are entirely dependent on each application's definition of which webhooks it is making available for use.  

A webhook event originates before and after general database operations related to entities when the operations are record-oriented actions. It is possible to plug in your own custom pre-and-post handlers using expressive rules that enable you to extend and customize the way in which simple database operations work. There are two classes of webhook events, referred to as __pre__ and __post__, which indicate when in the transaction the webhook is fired.  In addition to the two classes of events, there are different types of events, including __create__, __update__, and __delete__, which unsurprisingly are fired when a database record is being created, updated, or deleted. 

The concepts of __pre__ and __post__ events are important. Pre-events allow you to act on the event *before* anything is committed to the database.  The classic use case for this type of webhook would be to provide customized input data validation.  For example, suppose you hooked the event for adding a customer record. You could create a custom webhook that may, for example, look up some of the details that have been provided by the user in another system, for example, your CRM system, and verify the input data quality. For pre-event hooks, your webhook script can return a non-200 HTTP response code that will prevent the database action from taking place, returning the error you throw back to the user.  For pre-event hooks, the event includes a number of properties including access to the incoming data. 

For post-events, this happens *after* the data has been committed to the database. There are various use cases here; one example might be that on creation, you want to get the primary key value for the record that has just been created. This could be in order to synchronize with another system, or maybe make an API call back into your Hornbill instance to perform another action. Unlike a pre-event, returning a non-200 error code from the post-event hook will not prevent the transaction from completing.

The following table lists the event names that are available as webhook events.

|Property|Pre/Post|Description|
|:--|:--|:--|
|`create`|`pre`|When a new record is about to be created, this event fires before the record is added to the database.  You can prevent creation by returning a non-200 response code in your webhook script.|
|`created`|`post`|After a new record has been created, you can hook this event. You will get all new data for this record in the event.|
|`update`|`pre`|When an existing record is about to be updated, this event is fired.  You can validate any data that's about to get applied to the database before it is written to the database.|
|`updated`|`post`|After a record has been updated, you will get all of the updated data for this record.|
|`delete`|`pre`|Before a record is deleted, you will receive the current record data.|
|`deleted`|`post`|After a record is deleted, you will receive the record data that has now been deleted from the database.|


## WebHook Expressions
Webhook expressions make use of [Hornbill's ExpressLogic](/esp-fundamentals/reference-guides/express-logic) expression engine. In addition to the common ExpressLogic functions, the properties of the __onEntityEvent__ payload (see below) are accessible for your expressions to determine when you want to fire a webhook. 

For example, the following is a simple example of how a webhook expression would work. Say you are hooking the __create__ event when adding a contact. If you want to make sure that if the user's first name starts with *G* and an email address is not being provided, you could write an expression like this:

```sql
LEFT(h_name) = 'G' AND h_email NOT NULL
```

  

:::note
Webhook HTTP calls are expensive in terms of time to complete, which does directly influence the responsiveness of the user experience. The performance relates to the typical latency involved in making API calls over the Internet.  Webhook rule expressions, on the other hand, are very fast to evaluate, so you should always aim to create a rule that only triggers your webhook when it is needed, instead of always firing the webhook to your script and then using your script to determine if you should be acting on the webhook.  
:::

## Webhook Payload
When a webhook is called, an HTTP POST is made to your URL endpoint, and the payload of that POST request will include a JSON or XML object called __onEntityEvent__ that includes the following properties:

|Property|Description|
|:--|:--|
|`eventSource`|The name of the event source is a URN in the format __urn:webhook:entity:{table}:{event-name}__.|
|`eventTime`|The date/time this event was fired.|
|`actionBy`|The user ID of the person who carried out the action that invoked this webhook.|
|`actionByName`|The display name of the person who carried out the action that invoked this webhook.|
|`entity`|The name of the entity this event relates to.|
|`table`|The name of the database table this entity event relates to.|
|`record`.*|The list of record values relating to the database table for this event.  The [*] means all of the columns that contain a value that are from the __table__ being operated on.|

