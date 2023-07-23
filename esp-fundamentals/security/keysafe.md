# KeySafe
The Hornbill platform includes a feature called KeySafe. The purpose of the KeySafe feature is to provide a safe and secure way of storing credentials, API keys and other security-sensitive information that needs to be available at the point of use, when making API/Integration calls to other systems. Any enterprise system that takes security seriously, that has to deal with a large numbers of integrations with third-parties, a secure, central store for sensitive security information is required. 

In more typical integration approaches, credentials used for integrations are often just kept in plain text file, on a server, relying on the local administration control of the server itself to secure that information.  Because the Hornbill Platform is a cloud based service, we created a way of safely and securely storing these credentials, API keys, certificates and other sensitive information that ensures that this information is encrypted at rest, locked away, and only used at the exact point of use. 

When working with cloud and on-premise systems in relation to machine-to-machine integrations and automation, there are a number of commonly used authentication standards, such as OAuth, JWT, API Keys, userId/password, private/public keys and many others.  Further more, implementations of these standards have wide variations of implementation detail, but all of these standards ultimately require some level of security identifier/token/password to be stored, simply because machine-to-machine integrations and automation's do not have the benefit of human interaction to verify credentials at the point of use.  In order to cater for the wide range of requirements, KeySafe is essentially a specially encrypted database of KeySafe records.  Hornbill KeySafe includes a large number of pre-configured KeySafe types and templates covering many hundreds of integrates that Hornbill works with.

## Authentication Schemes
KeySafe has the capability of acting as a client being authorized by a third-party identity provider, supporting OAuth 1.1, OAuth 2 and many other variations and product-specific connections. 

## Security
Access to KeySafe is controlled by Hornbill system rights, which means you can configure and control access to KeySafe, locking down access to individuals, groups, teams etc... We have built in multiple layers of security into the KeySafe system to ensure the secret keys and other security assets stored in KeySafe remain safe and secure. 

## KeySafe Record Access Controls
Many pre-built integrations and import tools make use of KeySafe to store credentials, these integrations typically make use of API Keys on the Hornbill platform.  When creating a KeySafe entry, it is possible to restrict the use of individual KeySafe records to a specific user account(s) or API Key(s).

## Limited Security Surface
As well as all KeySafe content being encrypted at rest, and in motion, KeySafe credentials are generally not available for viewing/observing through the administrative user interfaces either, setting a password on a identity record for example is a one-way operation, the administrator configuring the KeySafe entry can set a password credential, but cannot subsequently view it once set. The various integration points that make use of KeySafe entry's, credentials content is transmitted to the point of integration encrypted, we only decrypt and use the credentials at the exact point its needed, and we never store credentials on any local disk files or in any caches, making KeySafe very secure. 

## Encryption
All KeySafe content is encrypted using AES-256 with a combination of a 256-bit private key, which is unique for each Hornbill instance, the encryption uses time-based variability to further strengthen the encryption applied.  

## Use Without Sight of Credentials
One of the key benefits of KeySafe is the ability for someone with higher privilege level to create a valid credential within KeySafe, and then be able to grant limited use-only access to that credential to other users. This makes it possible for, say a business process designer to use the credentials for a specific integration or service, without any possibility of having sight of the credential details. The benefits of this feature include:

- __Controlled Exposure of Sensitive Information__: When configuring an integration point for an organization-wide system like Email for example, you may want various people to make use of integrated email service, but do no want them exposed to the actual credential details (such as knowing the password or API key for a service). 

- __Central Management of Credentials__: When integrating with a system from multiple points of access, you need the ability to manage these access credentials centrally, such that if you have a security event that requires a credentials change, you can make this change in one location, instead of having to keep track of of all the places these credentials are being used, and having to change them in multiple places. 

