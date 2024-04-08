# Support

## Support Tiers
Hornbill is a cloud native solution designed for mission-critical business use. We provide three tiers of support, the first two tiers are included in your subscription and made available to all customers 24x7x365. The third tier is enhanced support which is optional, provides committed SLAs for a wide range of support needs and us unique to each customer.  Either Hornbill or one of our partners can offer these enhanced support services, depending on your needs.   

__Critical Availability Support:__
> This level of support is available 24x7x365 to all customers.  We monitor all systems at all times and have people on call, as well as an escalation procedure to the top of the Hornbill organization to deal with any critical problems that may arise.  We set ourselves very high standards here, aiming to achieve 99.9% uptime, and we achieve this by ensuring that our infrastructure, systems, processes and automation for detection and self-healing are continuously evolved to the highest possible standard.  While its extremely unusual for our systems to fail in terms of service availability, it can happen, when things do go wrong, we are generally well aware of these types of problems and resolve them before our customers are impacted or aware of the problems. 

__Community Solution Support:__
> This level of support is available to all customers who use Hornbill, this is provided through our community forums, of which our own Hornbill teams are participants.  While this channel does not offer any specific service-level-agreements, its the best channel to ask about non-critical problems and how-to type questions. Its also a great resources to search for solutions to problems you many encounter that have already been solved. 

__Solution Support Services:__
> This level of support is an optional paid-for support service for customers who need support for non-critical problems and how-to type assistance/support.  This service is bespoke to the needs of each customer and is provided by our customer success and support team.

__Getting Support and the Service Availability Checks:__
> To get support you can start by visiting [(https://hornbill.com/support](https://hornbill.com/support) this is the gateway to all support channels.  When you visit this page you are asked to enter your instance ID and your email address.  This information is used to identify you as a known, supported contact in relation to your instance, and once you have been identified, the gateway will run and automated __Instance Service Availability Check__ against your instance.  Based on the results of this check, you will be transferred to the support portal where the various support options available to you are presented.


## Service Availability Check
The Hornbill Service Availability Check is our way of helping you understand how your instance is performing in terms of its availability to you, and is the first step in identifying where any performance issues may be stemming from. This status check is performed from within your browser giving you an indication of instance performance including any network latency from the exact location you are working.

You can use the Hornbill Service Availability Check at any time, by any supported contact associated with your instance. You only need to provide the name of your Hornbill instance (found at the end of the URLs you use to access Hornbill i.e https://live.hornbill.com/mycompany/) and your email address.

![Status Check Image](/_books/esp-fundamentals/in-the-cloud/images/status_check_1.png)

Submitting these details will initiate the instance Service Availability Check. Simultaneously, the page will load details of the Hornbill Success Plan that your organization has and display the available Support options relevant to your plan.

### Interpreting the results of your Hornbill Availability Check

Once the Hornbill Service Availability Check is completed, ideally you will be presented with a series of green ticks. In the unlikely event that something is wrong, you will see a red mark accompanied by a brief description of the issue your instance is experiencing. You can be safe in the knowledge that our Infrastructure team use the same technology here to constantly monitor all of the instances and therefore if you do receive a negative result, it is likely that they are already working to resolve the issue. Regardless of this, please don't hesitate to contact us via the channels offered under your Success plan highlighting this negative result.

![Status Check Image](/_books/esp-fundamentals/in-the-cloud/images/status_check_2.png)

Clicking More Details will expand the Service Availability Check to show the areas that are tested as well as showing additional performance related information.

- __Test:__ The name of the Test Carried Out
- __Transaction:__ The total time taken by your instance to complete the rest, this is taken from first receiving the request to sending back the response.
- __Network:__ This is the total round trip time of the request minus the Transaction time, typically this is the time spend by the request traveling in the network including leaving a customers network navigating the internet to our data center to an instance and then back again. Typically this time should be fairly consistent between tests. High network latency is nearly always the customers network or route (ISP etc) and outside of our control.
- __Total:__ This is the Round Trip time so the total time spend from the browser first making the request to receiving the response.

The colored bars show a percentage indicator of the total time split into Transaction (Green) and Network (Yellow) , the more yellow in the test then the longer the test took traversing the Network and the more green in the test shows that the test spent longer in the Transaction.

<table>
<tr>
    <td width="33.3%">
        <h4 style="text-align: center">Typical Result</h4>
        <img src="/_books/esp-fundamentals/in-the-cloud/images/status_check_3.png" alt="Status Check OK">
        <p>Shows an example of a typical test result where the .</p>
    </td>
    <td width="33.3%">
        <h4 style="text-align: center">High Network Latency Example</h4>
        <img src="/_books/esp-fundamentals/in-the-cloud/images/status_check_3.png" alt="Status Check - Slow Network">
        <p>Shows an example of a very high network latency the overall test times are quite high and as shown by the large block of yellow and the Network time we can see that somewhere there is network latency being introduced and should be investigated further.</p>    </td>
    <td width="33.3%">
        <h4 style="text-align: center">High Transaction Times Example</h4>
        <img src="/_books/esp-fundamentals/in-the-cloud/images/status_check_3.png" alt="Status Check - Slow App Performance">
        <p>This final image gives an example of elevated transaction times and can happen when the instance is under load. Despite being higher than the first check, the times are still in an acceptable range. Its important to note that throughout the day the overall load on your instance will change so the transaction times can very depending on when they are being run.</p>
    </td>
<tr>
</table>
