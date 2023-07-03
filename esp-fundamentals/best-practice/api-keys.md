# Using API Keys Securely

When using API keys, security is an important consideration which should not be overlooked.  Its important that you keep your API keys secure, API keys in may respects should be treated like pass codes. Exposing API keys to an extended audience can result in the associated user account being compromised, which could lead to many security issues including unauthorized access and data theft/loss.  To keep your API keys secure, follow these best practices:

* Do not embed API keys directly in code: API keys that are embedded in code can be accidentally exposed to the public, for example, if you forget to remove the keys from code that you share. Instead of embedding your API keys in your applications, store them in environment variables or in files outside of your application's source tree.
* Do not store API keys in files inside your application's source tree: If you store API keys in files, keep the files outside your application's source tree to help ensure your keys do not end up in your source code control system. This is particularly important if you use a public source code management system such as GitHub.
* Do not show your API keys in videos, documents or other sharable content. If you do need to show screens where your API key appears, use your graphics tools to redact the specific key identifiers. 
* Restrict your API keys to be used by only the IP addresses that need them: By restricting the IP addresses that can use each key, you can significantly reduce the likelihood API key misuse. You should specify the hosts and/or network ranges that are valid for each.
* Restrict your API keys to be usable only for specific APIs: If the use case for  your API requires a number of API's, restrict the API key to only be able to invoke only those specific APIs.
* Delete unused API keys: To minimize your exposure to attack, delete any API keys that you no longer need.
* Rotate your API keys periodically: The longer an API key is in use, the more known it may become. Its always a good idea to rotate your APi keys periodically by creating a new key beside the existing one, updating the integration/use of the key, and then deleting the old key. 

## Recommended Hornbill Platform API Key Use

The following guidance sets our Hornbill's recommendations for best practice when using API Keys with the Hornbill platform.

### Always one user account for each API Key project

Because the Hornbill platform allows you to create multiple API keys associated with a single user account, its tempting to create one account and then create all of your API's on that account.  While this works, its generally not a good idea for a number of reasons.

* The account you create would need a superset of all rights needed by all API keys/use cases.  
* You would lose the ability to maintain a traceable audit trail of activity carried out in the context of a specific API key because on the Hornbill platform, audits
and trace logging is tied into the user account objects.
* Following the best-practice principle of minimal required rights/privileges is impossible to achieve when you are effectively sharing one account amongst multiple API key use cases/projects. 

Sometimes there is a valid reason for having more than one API key on an account, especially when you have, for example multiple, related data imports.  You may want each one on a separate API key, but they are a group of import scripts/functions running as "the nightly import". However, it should be noted that the primary purpose of allowing more than one API key per account is to facilitate seamless API key cycling and testing etc. 

### Always apply IP Address restriction rules.

Almost every use case for an API key is for some form of integration, data import or automation and as a general rule you would know exactly where these processes/tools are running.  By limiting the use of the API key to a specific IP address (or group of IP addresses) you will be limited in the ability for the API key to be abused, even if the key its self has been compromised. 

  :::note
  IP Address restriction rules are only available for platform build 3755 and above
  :::

### Always create API Filter Rules to limit APIs that can be Invoked

Most integrations or tools that will make use of API keys will typically only need to invoke a very small handful of API methods on the Hornbill platform.  You should always create specific API Filter rules on each API key, limiting the ability for the API Key use case to invoke API methods you were not expecting. 

### Never use the 'admin' account, or any user account that has super-user right granted for API Keys

While its tempting to create API's on all-powerful user accounts, this is not recommended and should be avoided.  The default 'admin' account on your Hornbill instances is a very powerful account, the privilege level applied to these super-user accounts bypass a lot of security checks and other security controls.  While its technically possible to create one or more API keys on the 'admin' account, or other super-user designated account, even with the IP Address Rules and API Filter Rules in place, its simply not a good idea to make a non-interactive super-user account so easily accessible with a simple key.

### Cycle your API keys.  

You should consider cycling your API keys periodically.  Hornbill provides an option to have an API key expire on a future date you specify.  Its a good idea to set yourself a periodic reminder to achieve this.  This is especially true as individuals move in and out of your organization, make sure you cycle any API keys that person may have had site of, or cause to work with. 

