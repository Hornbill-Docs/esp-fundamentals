# Single Sign-On (SSO)

The Hornbill platform supports single-sign-on as well as policy-based transparent auto provisioning and data updates of both user and guest accounts thus providing enterprise-class user identity integration with your organizations core IT directory services. 

## What is SAML?
__Security Assertion Markup Language__ (__SAML__, pronounced "sam-el") is the industry-standard scheme used for Single Sign-On (SSO) interoperability between enterprise systems. __SAML__ is an open XML-based standard developed by the Security Services Technical Committee of OASIS, and is designed to facilitate user authentication, entitlement, and attribute information between parties, in particular between an Identity Provider (IdP) systems and Service Provider systems (i.e. Hornbill.)

Here are some useful external references: -

- [SAML at Oasis-Open.org](https://www.oasis-open.org/committees/tc_home.php?wg_abbrev=security)
- [SAML at Wikipedia](http://en.wikipedia.org/wiki/Security_Assertion_Markup_Language)

## SAML and Hornbill
Hornbill makes use of the SAML framework to facilitate two things:
- __Single Sign On (SSO)__: this is the method of access control that enables a user to log in to their organizations network one time, but then have transparent authorization to access resources of multiple software systems without being prompted to log in to each system separately.  In the context of Hornbill, once configured, users may access their Hornbill instance pre-authenticated based on their enterprise desktop or browser login, and/or can use the authentication methods that their identity provider makes available to them. 
- __Auto-provision Hornbill User Accounts__: along with the authorization information needed for Single Sign-On, SAML has the ability to transport additional user directory attributes such as their name, email address ano login ID. The Hornbill platform is capable of processing this additional information contained in the SAML assertion and use it to automatically create a user accounts on your Hornbill instance. This mechanism can remove a significant amount of overhead in terms of system administration when it comes to creating user accounts

:::tip 
While SSO must be set up to utilize auto-provisioning, the auto-provisioning of user accounts in Hornbill is an optional mechanism that can be disabled independently of Single Sign-On. Hornbill provides a range of user import utilities and capabilities that can be used instead of SSO based auto-provisioning. More information on the available user imports can be found here: [Open Integration Tools](https://wiki.hornbill.com/index.php/Hornbill_Open_Integration_Tools)
:::

## How it Works
There are three key actors in any SAML implementation for Single Sign-On, these are the __user__ trying to access the Hornbill Application (via their Web Browser), the __Identity Provider (idP)__ which knows, and has already, or will identify the user, and the application/service provider (Hornbill Cloud Service) which provides the application and/or resources that the user wishes to access. Your Hornbill instance is the service provider, and typically your enterprise directory system, very often Microsoft Active Directory Federated Services (ADFS) or Azure Directory Services acts as your identity provider.

![SAML Flow](/_books/esp-fundamentals/security/images/saml-flow.png)

Once SSO is configured, when an unauthenticated user navigates to your Hornbill instance via one of the Hornbill URLs, the browser will be re-directed to the identity provider with the information needed to request access to the service, this is known as a SAML AuthnRequest. The idP will look at the AuthnRequest and if the user is authorized will return an Assertion back to the browser with a redirect to the service provider (in this case the Hornbill Instance). The Hornbill instance will validate the Assertion checking its authenticity against a known Hornbill SSO profile and if valid will create a session and allow the user to access Hornbill as required.

## SSO Realms
In Hornbill, there are different types of [user accounts](/esp-fundamentals/security/user-accounts), these users access Hornbill through different user interfaces.  For SSO, users logging in through the main user application and/or employee portal can be authenticated using SAML, and external users accessing Hornbill via the customer portal can also (if required) authenticate on the portal using SSO - although this is an unusual use case.

Its important to understand there is a difference between these Realms, because the configuration parameters for each realm are different. 

### Multi-IDP Environments
There is one more complex use case for SSO, often found in larger enterprise companies, where users of a single Hornbill instance, my be on a network where more than one active Identity Provider is being used.   Its possible on Hornbill to configure more than one SSO Profile against the same real which will change the login experience for users.  In the case where there is more than one Identity provider configured, the user will be required to select which Identity Profile to use for authentication, so if this is the configuration you need, you should be mindful of the names you attribute to the SSO Profiles in Hornbill, as these are the names that will be presented to the user when they first log in, so the names should be meaningful to them.

## SSO Metadata
Configuring an IDP and Service Provider can be complicated, but is made simpler by both system accepting some standard format metadata that essentially caries the information required for the other party to be correctly configured.  Both IDP and Service Provider party's will have some way of providing  you with either metadata or the key information needed by the other party for configuration.  When [configuring SSO](/esp-config/security/sso/single-sign-on) for Hornbill, you will need to follow a processes and do things in a specific order.  The exact method of configuring SSO will be different depending on both the IDP you are using, and the way in which your IDP is set up and configured for your organization.

You can access the required metadata and/or key configuration parameters required by going to the __SSO Profiles__ screen in the Hornbill Platform Configuration area of the product.  See [configuring SSO](/esp-config/security/sso/single-sign-on) for more information.

## Interoperability
The Hornbill platform is built on open standards, and our enterprise SSO implementation is no exception. While we do not act as a support function for any third-party IDP system, the following identity providers are known to have been configured and work with the Hornbill platform (we will expand this list as we integrate successfully with other systems).

- [Microsoft Active Directory Federation Services (ADFS 2.0)](http://msdn.microsoft.com/en-GB/library/bb897402.aspx)
- [Microsoft Azure Active Directory](https://docs.microsoft.com/en-us/azure/active-directory/develop/single-sign-on-saml-protocol)
- [Ping Identity](http://www.pingidentity.com/)
- [SSO Circle](https://www.ssocircle.com/en/idp-tips-tricks/ssocircle-how-to/)
- [Shibboleth Identity Provider](https://shibboleth.atlassian.net/wiki/spaces/IDP4/overview)
- [OpenAthens (EduServ)](http://www.openathens.net/)

As you might expect, different vendors may well use different terminology to describe the configuration required in the IDP but typical examples would be __Service Provider Profile__ or __Relying Party Trust__ (see below for Example IDP configurations and references). It is likely that you will need an entry in your IdP to represent each of the Hornbill Realms Service URL's (i.e. user and customer), depending on what you want to configure SSO for.

:::warning
Although Hornbill does have expertise around our own platform and its SAML 2.0 implementation, configuration, and behavior, we use the generic language associated with the SAML 2.0 specification and not the language/terminology adopted by any specific vendors identity provider platforms.  Hornbill's technical staff are __NOT__ experts with the specifics of the various identity provider technologies and platforms in common use, or even IDPs that are known to work with Hornbill.  It is important to understand that Hornbill complies the SAML 2.0 specification to the letter, so if your IDP supports SAML 2.0 then it should work with Hornbill without issue.

Each organization's identity provider implementation, and its configuration will be unique to their organization. When configuring SSO with Hornbill it will be necessary for you to have someone internally within your own organization who has the requisite knowledge and expertise, as well as a working knowledge of your own identity provider and its configuration within your organization, on hand. This is typically someone that has access to your iDP and the authority to make changes to it in order to configure Hornbill as an application your IDP with authenticate for.  You should refer your technical expert to this document, as well as other related configuration documentation which will provide them with the detailed technical information they will need in order to facilitate the planning and configuration of Single Sign-On for your organization.
:::

## SSO Digital Certificates
Digital certificates generated and used by your Identity Provider typically have an expiry date.  Once a digital certificate has expired, and assuming you have not disabled the Time and Cert valid checks (which you should only ever do for troubleshooting), then you will no longer be able to login using SSO.  As it is easily forgotten, your Hornbill instance will run a certificate reminder schedule in advance of your signing certificate expiring, acting as a reminder and prompt for you to update the certificates in your SSO Profile(s). 

### How the Schedule Works
The reminder schedule will send email notifications to your registered Primary and Secondary technical contacts, and will follow a schedule defined in “days before expiry” here: -

::* 30 Days – a courtesy notification letting you know that your certificate will expire in 30 days, subject of the message will be “Your Single Sign-On Certificate will expire in 30 days”
::* 15 Days – first reminder, subject of the message will be “ATTENTION: Your Single Sign-On Certificate will expire in 15 days” 
::* 7 Days – second reminder, subject of the message will be “WARNING: Your Single Sign-On Certificate will expire in 7 days”
::* 1 Day – final reminder, subject of the message will be “URGENT: Your Single Sign-On Signing Certificate will expire tomorrow”

At any point during this 30-day schedule, your SSO Profile(s) certificates are updated with new ones, this schedule will be reset and you will not receive any further notifications.

The schedule message, subject, and content of the email messages are fixed and not customizable.  The email addresses used are those defined as your primary and secondary technical contacts registered against your instance.

### SSO Auto Certificate Renewal
In order to eliminate the manual effort and administrative overhead of updating the SSO certificates manually, it is possible to configure your Hornbill instance to automatically update the public certificates from your SAML identity provider.  This saves you from having to do this manually each time the certificate is renewed on your identity provider. 

By configuring this capability, this certificate renewal automation removes the need for any further maintenance of certificates between your Hornbill instance and your Identity Provider, eliminating situations where someone forgets to update a certificate manually causing a loss of access to your instance while a new certificate is applied manually. 

Many Identity providers that implement SAML 2.0 have a feature whereby the signing certificate used for signing SAML assertions are automatically renewed periodically, typically once a year.  When a new certificate is generated, it is generated some time in advance of the expiry date of the currently active certificate creating an overlap period where both the new and the old certificate are active. This gives system administrators time to update any service providers using SSO with the new certificate information. 

The policies that control the certificate renewal and overlap periods are defined by the identity provider and beyond the scope of this document, you should see the documentation for the Identity Provider you are using to find out more about this.

When configuring Hornbill to use SSO, one of the things you are required to do as part of the SSO configuration is provide your Hornbill instance with the metadata from your Identity Provider, this is typically a URL that when viewed in a browser will return the XML metadata data describing the Identity Provider, its public certificates and so on. 

If this is URL is accessible to the Hornbill instance, our servers will periodically look for new certificates from this trusted URL, and a match is found to any registered SSO profile on your instance, and if there are new public key(s), these will be automatically imported into the Hornbill SSO profile, allowing a seamless switch-over from an existing to a new certificate without any service disruption.  Conversely, expired certificates are automatically removed from your SSO profile(s) once they are no longer in use.  Certificate use counters are maintained in order to facilitate this. 

## User Account Auto Provisioning
One of the features of Single Sing-On is user account auto-provisioning.  When a user authenticates via an IDP using SSO, the identity provider (IDP) can optionally provide additional information about the user logging into the service provider (Hornbill in our case). Information including first name, last name and e-mail address, but through configuration of the IDP and depending on what information is held in the customers directory service, any other information can also be provided.  Hornbill has the ability to use this information, and the fact that the authentication is trusted and verified using a digital certificate, to subsequently create the required user account in Hornbill on first login.  This can be a useful capability that can simplify the process of onboarding users onto the Hornbill platform.

The Hornbill SSO implementation is an enterprise grade, sophisticated capability ensuring almost any SSO need can be met.  The implementation in Hornbill provides a seamless user experience to your Hornbill users once set up correctly, Hornbill SSO implementation is maintenance free, is very reliable and secure way of handling user authentications on Hornbill. 