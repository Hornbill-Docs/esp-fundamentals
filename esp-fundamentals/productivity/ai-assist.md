# Text Assist (AI Assist)

In Hornbill there are numerous places you might be writing textual content.  AI Assist is a productivity feature powered by OpenAI that brings generative AI capabilities to your fingertips to help with improving on or expanding your written content, as well as providing you access to non-company-specific generalized knowledge.  These features enhance your ability to write with great clarity, expand on common topics where required and access generic knowledge available to the underlying language model.

AI Assist is in the early stages of development as we consider, observe and better understand how customers make use of this as well as how we might further use Generative AI to enhance the user experience and productivity when using Hornbill. 

## Frequently Asked Questions


#### Can the AI Assist feature be disabled globally? ###
> Yes, there is a global system setting which can be used to enable/disable this feature (just search in admin for `integration.openai.enable` to locate the setting)

#### Who is paying for the OpenAI service?
> For now, Hornbill is picking up the bill for this, so for all customers, the usage of this feature is free of charge.  It is possible for individual customers to provide an API key for their own OpenAI account should they want to track/manage usage via the OpenAI system, you can simply create an OpenAI API key and set it here (search admin for __integration.openai.apiKey__), once set, your instance will use this key for OpenAI related API calls. 

#### Can AI Assist be restricted to defined groups of users?
> No, its either on or off for all full users on your instance, this is not presented to any basic user or contact via the end user portals. 

#### What is the backend system that is powering this AI Assist feature?
> This is being powered by the [OpenAI Service](https://openai.com/), this is the same generative AI system that powers ChatGPT

#### Where is the data being processed?
> For Text Assist (previously AI Assist), the data is being processed on the OpenAI servers is the data the user types in, and/or selects when selecting the assist option, which is why we have provided the ability to disable this if thats not acceptable to your organization. 

#### What assurances do we have that the data isn’t being stored?
> You have the exact same assurances that we do, via the [OpenAI Terms Of Use](https://openai.com/enterprise-privacy/)

#### Has any consideration be given for what might happen if personal data is inputted and processed?
> We do not feel there is a problem based on OpenAI current terms of use, but we recognize thad individual customers may well take a different view.  This is why we provide the ability for individual customers to turn this feature off

#### Can we get any technical documentation and any other statements that Hornbill might have prepared to allay any of the numerous concerns of these types?
> This is in the very early stages of development, today is very simple and does not warrant any significant documentation in its own right, its just a nicely done integration to an existing AI GenAI service. We are still deciding on exactly how this applies and will be used in the long term, we have limited internal technical documentation that would be customer-friendly, so at this time we do not. We would refer you to the [OpenAI API]( https://openai.com/product) documentation which will give you a lot more insight into how the GenAI system works.

#### Does the feature offer insight into any of our Business-Specific process models and offer our users insight into how we can better use the Hornbill product?
> No not at this time, its purely there as an assistive tool to help with generalized writing, grammar and general/generic knowledge access
