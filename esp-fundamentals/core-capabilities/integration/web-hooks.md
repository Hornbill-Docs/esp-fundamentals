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

### Syncronious vs. Asyncronious
When creating a webhook trigger you can set its __POST mode__. The POST mode referres to the way in which the webhook you call interoperates with the Hornbill platform.  Because webhooks are remote web API calls, these can be slow, depending what you want to achieve you may not want any slowness to be reflected in the interaction of the user with the system.   To give you more control over this, there are three modes of operation for a WebHook which control how Hornbill ESP makes the network calls, which are: -

|POST mode|Description|
|:--|:--|
|Asyncronious|You can think of this as a fire-and-forget scheme, much like sending an email, the system will compose the webhook payload, and add that post rquest into a queue, immaediately returning control back to the server.  This means that, if the WebHook being invoked is slow, this will not impact the performance of the transaction in Hornbill that trigggered the webhook.|
|Syncronous|In this mode, the Hornbill service will wait for the WebHook to complete *before* returning contol back to whatever triggered the webhook.  Lets say a new record is being added, this triggers a WebHook which makes a call to a web service, and that web service takes 5 seconds to return, then the user adding this record will *perceive* the delay of the WebHook as it will take 5 seconds to return control to the user.  If the webhook succeeds or fails, the users operation will still complete successfully, but on failure, an entry will be written to the log file indicating the WebHook failed.|
|Syncronous Critical|This is the same basic behavior as __Synconoous__ but in addtion has the ability to prevent the users operation and optionally return a user-presented error message. If the WebHook returns a non-success (2xx) response code, then the WebHook will have been considered to fail, and in this mode, the users operation would also fail.  The typical use case for this mode would be to use in combination with a __pre__ hook event to validate user input.  For example, supposed one of your input fields contaons an employee number, and, you want to verify that employee number is valid, but your employee numbers are maintained on your Workday HR system.  Your webhook code can make a call to your Workday HR system, look up the employee number, do what ever checks you need, and either return success or failure to the Hornbill webhook trigger.<br><br>You can optionally return a user-presented error message back to the user.  In order to do this you must ensure the following conditions are met: - <ul><li>Return the HTTP reposnse code __403__ from your WebHook</li><li>Set the __Content-Type__ response header to __text/plain__</li><li>Return the error message text you want to be presented to the user in the WebHook response body</li></ul>|


A webhook event originates before and after general database operations related to entities when the operations are record-oriented actions. It is possible to plug in your own custom pre-and-post handlers using expressive rules that enable you to extend and customize the way in which simple database operations work. There are two classes of webhook events, referred to as __pre__ and __post__, which indicate when in the transaction the webhook is fired.  In addition to the two classes of events, there are different types of events, including __create__, __update__, and __delete__, which unsurprisingly are fired when a database record is being created, updated, or deleted. 

### Pre and Post Event Hooks

The concepts of __pre__ and __post__ events are important. Pre-events allow you to act on the event *before* anything is committed to the database.  The classic use case for this type of webhook would be to provide customized input data validation.  For example, suppose you hooked the event for adding a customer record. You could create a custom webhook that may, for example, look up some of the details that have been provided by the user in another system, for example, your CRM system, and verify the input data quality. For pre-event hooks, your webhook script can return a non-200 HTTP response code that will prevent the database action from taking place, returning the error you throw back to the user.  For pre-event hooks, the event includes a number of properties including access to the incoming data. 

:::warning
In order for a pre-event hook to inhibit a user or even action, you must make sure that you use the __Synconous Critical__ POST mode and follow the basic guidance provoded for this mode.
:::

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
:::info
Webhook HTTP calls are expensive in terms of time to complete, which can directly influence the responsiveness of the user experience if you are usiong one of the Synconous POST modes. The performance relates to the typical latency involved in making API calls over the Internet.  Webhook rule expressions, on the other hand, are very fast to evaluate, so you should always aim to create a rule that only triggers your webhook when it is needed, instead of always firing the webhook to your script and then using your script to determine if you should be acting on the webhook.  
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

