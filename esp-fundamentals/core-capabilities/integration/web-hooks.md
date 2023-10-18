# Web Hooks
Webhooks provide you a way to customize the database record operations relating to entities on the platform. The idea is, you can intercept and act on specific events, for example adding or updating a database record, you are able to write your own custom script and have the Hornbill platform call that script. 

Webhooks are a way for different applications or services to communicate with each other in real time via HTTP callbacks. They provide a mechanism for one service to notify another about a specific event that has occurred, allowing the receiving service to immediately react to the event.

## How Webhooks Work

The following diagram shows the data flow of a typical record-oriented data transaction, with the blue boxes indicating where WebHooks are able to plug into the transactional data flow. 

![Webhook Transaction](/_books/esp-fundamentals/core-capabilities/images/webhook.svg)


* __The Event Triggers__:  Webhooks are triggered by specific events, such as creating a new database record, updating a user etc. 

* __Event Rules__:  webhook rules are evaluated, and if a match if found, the webhook event is fired. 

* __WebHook Call__: Once the event occurs, the Hornbill service sends an HTTP request to the URL specified for the webhook. 

* __Custom Application__: Your custom web application that receives the webhook can then take action based on the data received in real-time.  Webhooks deliver relevant data to other applications, meaning you get data immediately. The endpoints (URLs) are specific to each webhook and are registered to receive callbacks.

* __Real Time__: WebHooks enable enables real-time processing and reactions to events as they allow applications to get real-time data without relying on any time of polling mechanisms. Webhooks are more efficient than polling, where an application would need to continually check for new data.

* __Secure__: Webhooks should ensure that data is encrypted during transit using HTTPS to maintain data confidentiality.
Webhooks are widely used due to their efficiency, real-time processing capabilities, and ease of implementation. They are crucial in enabling integrations between disparate systems in today's highly connected digital ecosystem.

## Events
Entity events originate before and after general database operations related to entities when the operations are record-oriented. It is possible to plug in your own custom pre-and-post handlers using expressive rules that enabled you to extend and customize the way in which simple database operations work. There are two classes of webhook events, referred to as __pre__ and __post__ which indicates when in the transaction the webhook is fired.  In addition to the two classes of events, there are different types of event, including __create__, __update__ and __delete__ which unsurprisingly are fired when a database record is being created, updated or deleted. 

The concepts of pre and post events are important. Pre-events allow you to act on the event *before* anything is committed to the database.  The classic use case for this type of webhook would be to provide customized input data validation.  For example, supposed you hooked the event for adding a customer record, you could create a custom WebHook that may, for example, look up some of the details that have been provided by the user in another system, for example, your CRM system, and verify the input data quality or some other means. For pre-event hooks, your WebHook script can return a non-200 HTTP response code which will prevent the database action from taking place, returning the error you throw back to the user.  For pre-event hooks, the event includes a number of properties including access to the incoming data. 

For post events, this happens *after* the data has been committed to the database. There are various use cases here, but one example might be, on creation you want to get the primary key value for the record that has just been created, in order to synchronize with another system, or maybe make an API call back into your Hornbill instance to perform another action. Unlike a pre-event, returning a non-200 error code from the post event hook will not prevent the transaction from completing

The table lists the event names that are available as webhook events

|Property|Pre/Post|Description|
|:--|:--|:--|
|create`|`pre`|When a new record is about to be created, this event fires before the record is added to the database.  You can prevent creation by returning a non-200 response code in your WebHook script|
|`created`|`post`|After a new record has been created, you can hook this event, you will get all new data for this record in the event.|
|`update`|`pre`|When an existing record is about to be updated, this event is fired.  You can validate any data thats about to get applied to the database before its written to the database|
|`updated`|`post`|After a record has been updated, you will get all of the updated data for this record|
|`delete`|`pre`|Before a record is deleted, you will receive the current record data|
|`deleted`|`post`|After a record is deleted, you will receive the record data that has now been deleted from the database|




## WebHook Expressions
WebHook expressions make use of [Hornbills ExpressLogic](/esp-fundamentals/reference-guides/express-logic) expression engine. In addition to the common ExpressLogic functions, the properties of the __onEntityEvent__ payload (see below) are accessible for your expressions to determine when you want to fire a WebHook. 

For example, if you were hooking the __create__ event when adding a Contact and wanted to make sure that if the Users first name started with 'G' and an email address was not being provided, you could write an expression like...

```sql
LEFT(h_name) = 'G' AND h_email NOT NULL
```

is a simple example of how a WebHook expression would work.  

:::note
WebHook HTTP calls are expensive in terms of time to complete, which does directly influence the responsiveness of the user experience, the performance relates to the typical latency involved in making API calls over the Internet.  WebHook rule expressions on the other had are very fast to evaluate, so you should always aim to create a rule that only triggers your web hook when its needed, instead of always firing the webhook to your script and then using your script to determine if you should be acting on the web hook.  
:::



## Webhook Payload
When a webhook is called, an HTTP POST is made to your UTL endpoint, and the payload of that POST request will include a JSON or XML object called __onEntityEvent__ that includes the following properties: -

|Property|Description|
|:--|:--|
|`eventSource`|The name of the event source is a URN in the format __urn:webhook:entity:{table}:{event-name}__ see __Event Sources__ for more details.|
|`eventTime`|The date/time this event was fired|
|`actionBy`|The User ID of the person who carried out the action that invoked this WebHook|
|`actionByName`|The display name of the person who carried out the action that invoked this WebHook|
|`entity`|The name of the entity this event relates to|
|`table`|The name of the database table that this entity event relates to|
|`record`.*|The list of record values relating to the database table for this event.  The [*] means all of the columns that contains a value that are from the __table__ being operated on|

