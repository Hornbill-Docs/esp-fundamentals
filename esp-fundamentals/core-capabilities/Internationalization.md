# Internationalization
The Hornbill platform and its applications are built from the ground up with internationalization in mind.  Every aspect of our technology stack uses Unicode ensuring that both user interface elements as well as content can support and work with any language

Some of the key features of Hornbill that support internationalization include: 

- __Language Context__: The Hornbill platform allows users to use different languages at the same time. As well as a default language to be defined against each user profile, a user can switch languages at any time, where the UI will refresh and the new language setting will be applied. 
- __In-app UI Translation__: With sufficient rights, a user may enter into translation mode, allowing them to translates any/all UI elements into one or more different languages.  This allows easy translation of UI elements from directly within the UI. 
- __Bulk Translations__: It is possible for a user to bulk-translate UI elements using external translation services, for example using Google translate
- __Smart Content Translations__: The system understands the language content is written in, and where there is a difference between the origin language and the users current language, options are presented that allow the user to translate the content dynamically, facilitating international working.

# Localization
User profiles allow the setting on date, time, dateTime and timezone display formats as well as local time representation of global times. 

# International Universal Time System
Behind the scenes, the Hornbill platform implements all date/times in Universal Coordinated Time (UTC), ensuring that our customers that have users or customers that span timezones and international boundaries are all working to the same times, with date/time storage in UTC, where required, each user can see that date/time in a local time representation 