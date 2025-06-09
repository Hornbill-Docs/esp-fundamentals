# HAi Services

The Hornbill ESP Platform provides seamless integration with available AI Service Providers, including OpenAI and Azure AI. Hornbill ESP's integration layer makes AI services available to applications and features in Hornbill in a way that is abstracted from any specific AI service provider.  This allows each customer to choose specific AI services providers and in some cases even specific AI models.  The Hornbill ESP platform makes integration with AI service providers a simple point and click exercise, we implement real time result streaming providing modern real-time service integrations for optimal user experience when making use of HAi features.  

## Selecting a HAi Service Provider

By default your Hornbill instance will not be configured with a HAi Service Provider, this effectively disables Generative AI for your Hornbill instance. To enable any of the Generative AI Capabilities, your User Account must be associated with the following roles:

|Role|Application|Description|
|-|-|-|
|HAi Manager|Platform|This role should only be used for managing HAi configurations.|
|Admin Role|Platform|This role provides administrative functionality to the Hornbill platform and should only be granted to an administrator.|

Then use the following steps to enable to change the HAi Service provider:

* Log into Hornbill with the relevant access role.
* Click on the settings gear icon in the lower left of the screen.
* Change the dropdown from My ```Personal Settings``` to ```Platform Configuration```.
* Click on ```HAi Services``` under Administration in the left-hand menu.
* Select the provider required, click Save.

![Hornbill AI Configuration](/_books/esp-fundamentals/core-capabilities/images/hai-services.png)

## HAi Service Providers

The primary difference in HAi Service providers is the geographic location where your data will be processed, both Azure and OpenAI providers utilize the same underlying OpenAI models but Azure allows for tighter controls on the region data is processed in, The Following HAi Service Providers are currently available (as of 11/2024):

|Provider|Usage|Description|
|:--|:--|:--|
|OpenAI (US International)|Free|Data is processed on OpenAI's international servers, which basically means in the US data centers. Hornbill picks up the bill for all usage for this service provider option|
|OpenAI (Customer Provided)|Premium|You can choose to provide credentials to your own registered OpenAI account, which gives you full access to the OpenAI services reporting, statistics and usage restrictions controls that the OpenAI service provides.|
|Microsoft Azure (US)|Premium|Integration with AI Services provided by Microsoft, with all data processing done in US data centers operated by Microsoft. Hornbill picks up the bill for all usage for this service provider option|
|Microsoft Azure (EU)|Premium|Integration with AI Services provided by Microsoft, with all data processing done in EU data centers operated by Microsoft. Hornbill picks up the bill for all usage for this service provider option|
|Microsoft Azure (Customer Provided)|Premium|You can choose to provide credentials to your own registered Microsoft Azure account, which gives you full access to the Microsoft Azure AI services reporting, statistics and usage restrictions controls that the Microsoft Azure AI service provides.|

:::note
HAi Premium services (upcoming) will available for free, on request, only while the HAi Services and features are available in the beta program, please talk to your account manager when these services become available.
:::

## Frequently Asked Questions

#### Can HAi Services feature be disabled globally on my Hornbill instance? 
> Yes, in the Platform Administration area, under Integration there is an option to disable HAi services on your instance, or choose from one of the available AI Service Providers.

#### Who is paying for the HAi Service Provider usage?
> For now, Hornbill is picking up the bill for these services we provide, so for all customers, the usage of this feature is free of charge when using the OpenAI service provider. For HAi Premium option, it is possible to choose regional services from Microsoft Azure, we have UK, EU and USA service providers available for you to choose form.  It is also possible for individual customers to provide an API/Credentials/Settings ror their own OpenAI or Azure account should they wish to track/manage usage via the AI Services independently of Hornbills own tracking, in this case each customer choosing this option will pay for their own AI services from their chose AI service provider.

#### Can HAi Features be restricted to specific groups of users?
> No, at the platform level, your instance is configured to use an HAi Service Provider or not.  However, individual applications on the Hornbill Platform may provide more granular per user/per group access controls for specific HAi features.

#### What is the underpinning service that is powering this HAi Services capability?
> We currently support two specific back end HAi service providers, being [OpenAI](https://openai.com/), which is the same generative AI system that powers ChatGPT, and [Microsoft Azure OpenAI Service](https://azure.microsoft.com/en-us/products/ai-services/openai-service/).  

#### Do you have a Data Processing Agreement with the back end AI service providers?
> Yes we have supplier agreements in place, generally speaking the service providers terms of service directly pass through to you as a Hornbill customer using these services.  

#### Where is the data being processed?
> For any use of HAi Services, the related data is being processed on the back end HAi Service Providers servers. The specific data centers/regions depend on the specific HAi Service Provider selected.

#### What assurances do we have around data being stored?
> You have the exact same assurances that we do, via the selected service providers Terms of Use agreement that applies to the selected service provider. A link to these terms will be available in the administration area when you select your chosen HAi service provider.

#### Has any consideration be given for what might happen if personal data is inputted and processed?
> We do not feel there is a data processing problem based on the currently supported HAi Service Providers, but we do recognize thad individual customers may well take a different view.  For this reason, we provide the ability for individual customers to turn HAi Services off for their instance.

#### Can we get any technical documentation and any other statements that Hornbill might have prepared to allay any of the numerous concerns of these types?
> HAi Services and their use is in the very early stages of development, today is very simple and does not warrant any significant documentation in its own right.  Hornbill is simply providing a nicely done integration to existing Generative AI service providers. We are still deciding on exactly how this applies and will be used in the long term, we have limited internal technical documentation that would be customer-friendly, so at this time we do not. We would refer you to the relevant documentation of the specific HAi Service provider you choose to use.

#### What is Text Assist?
> In Hornbill there are numerous places you may be writing textual content.  Text Assist is a set of productivity feature powered by HAi Services that brings generative AI capabilities to your fingertips to help with improving or expanding your written content, as well as providing you access to non-company-specific generalized AI knowledge.  These features enhance your users ability to write with great clarity, expand on common topics where required and access generic knowledge available to the underlying HAi Service Provider language models.
