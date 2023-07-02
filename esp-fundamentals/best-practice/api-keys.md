# API Best Practice Guide

When you use API keys to access the Hornbill platform and/or its applications, take care to keep your API keys  secure. Publicly exposing your API keys can result in the associated user account being compromised, which could lead to many security issues including unauthorized access. To keep your API keys secure, follow these best practices:

* Do not embed API keys directly in code: API keys that are embedded in code can be accidentally exposed to the public, for example, if you forget to remove the keys from code that you share. Instead of embedding your API keys in your applications, store them in environment variables or in files outside of your application's source tree.
* Do not store API keys in files inside your application's source tree: If you store API keys in files, keep the files outside your application's source tree to help ensure your keys do not end up in your source code control system. This is particularly important if you use a public source code management system such as GitHub.
* Do not show your API keys in videos, documents or other sharable content. If you do need to show screens where your API key appears, use your graphics tools to redact the specific key identifiers. 
* Restrict your API keys to be used by only the IP addresses that need them: By restricting the IP addresses that can use each key, you can significantly reduce the likelihood API key misuse. You can specify the hosts and/or network ranges that can use each key.
* Restrict your API keys to be usable only for specific APIs: If the use case for  your API requires a number of API's, restrict the API key to only be able to invoke only those specific APIs.
* Delete unneeded API keys: To minimize your exposure to attack, delete any API keys that you no longer need.
Rotate your API keys periodically: To rotate your API keys, call the CreateKey method. After the replacement keys are created, update your applications to use the newly-generated keys and delete the old keys.

## Recommended API Key Use

The following points set our hornbill's recommendations for best practice when using API Keys with the Hornbill platform.

### 1. Always one user account for each API Key project

Because the Hornbill platform allows you to create multiple API keys associated with a single user account, its tempting to create one account and then create all of your API's on that account.  While this works, its generally not a good idea for a number of reasons.

* The account you create would need a superset of all rights needed by all API keys/use cases.  
* You would lose the ability to maintain an traceable audit trail of activity carried out by any individual API use cases
* Following the principle of minimal required rights/privileges is impossible when you are effectively sharing one account amongst multiple API key use cases/projects. 

Sometimes there is a valid reason for having more than one API key on an account, especially when you have, for example multiple, related data imports.  You may want each one on a separate API key, but they are a group of import scripts running as "the nightly import". However, it should be noted that the primary purpose of allowing more than one API key per account is to facilitate seamless API key cycling and testing etc. 

### 2. Always apply IP Address restriction rules.

Almost every use case for an API key is for some form of integration, data import or automation and as a general rule you would know exactly where these processes/tools are running.  By limiting the use of the API key to a specific address (or addresseS) you will be limited in the ability for the API key to be abused, even if it was compromised. 

### 3. Always create API Filter Rules to limit APIs that can be Invoked

Most integrations or tools that will make use of API keys will typically only need to invoke a very small handful of API methods on the Hornbill platform.  You should always create specific API Filter rules on each API key, limiting the ability for the API Key use case to invoke API methods you were not expecting. 

### 4. Never use the 'admin' account, or any super-user account for API Keys

While its tempting to create API's on powerful user accounts, this is not recommended and should be avoided.  The default 'admin' account on your Hornbill instances is a very powerful account, the privilege level applied to these super-user accounts bypass a lot of security checks and other security controls.  While its technically possible to create one or more API keys on 'admin' or other super-user designated account, even with the IP Address Rules and API Filter Rules in place, its simply not a good idea to make a non-interactive super-user account so easily accessible with a simple key.

### 5. Cycle your API keys.  

You should consider cycling your API keys periodically.  Hornbill provides an option to have an API key expire on a future date you specify.  Its a good idea to set yourself a periodic reminder to achieve this.  Alos, as people move in and out of your organization, make sure you cycle any API keys that person my have had site of, or cause to work with. 

