# Policy-Shortcut-Chain
Sample policy set to show how you can use multiple policies in tandem to create a complete policy or service.  

## Description

The Axway API Gateway gives you the ability to greatly reuse components. Rather than building a monolithic policy with all logic contained, if you compartmentalize logic as modular components, it makes it much easier to reuse logic across multiple policies and makes these components easily interchangeable as requirements modernize or change. The policy shortcut filter allows you to easily call multiple policies, each containing their own policy logic subset, to make a new complete policy or service. This policy set uses data from three separate policies that independently do not provide complete value, and integrates them together to create a complete solution.

![alt text](https://github.com/Axway-API-Management-Plus/Policy_Shortcut_Chain_Example/blob/master/example/src/policyView.png "Policy Building")

The three component policies, "ShortcutChain_Policy[1-3]", contain the following:
- **Set Attribute Filter**: This filter, renamed as "Set value[1-3] Attribute Filter", creates an attribute when the policy is executed and assigns it a value.

![alt text](https://github.com/Axway-API-Management-Plus/Policy_Shortcut_Chain_Example/blob/master/example/src/setAttribute.png "Set Attribute")

The core policy, "ShortcutChain_Aggregator", flow is as follows:

- **Policy Shortcut Chain**: This filter allows you to call a number of policies in sequence. As each policy executes, the created attributes as defined above will be available to the core policy.

![alt text](https://github.com/Axway-API-Management-Plus/Policy_Shortcut_Chain_Example/blob/master/example/src/shortcutChainFilter.png "Shortcut Chain")

- **Set Message massage Filter**: This filter, renamed "Concat Attributes From Policies", takes the attributes from the three policies called in the shortcut chain and uses them to dynamically populate a message.
- **Reflect Message Filter**: This reflects the message to the requestor.

This policy set is meant to be a very basic example of how you can build modular policy logic, and use the shortcut chain filter to execute these policies in sequence to realize new value.


## API Management Version Compatibility
This artefact was successfully tested for the following versions:
- V7.5.3


## Install

- Download the PolicyShortchutChain*.xml policy file set.
- There are several options to import this file, including Team Development, REST API, and sample scripted options included with the Axway solution. The simplest way however is to open Policy Studio and select 'File --> Import --> Import Configuration Fragment'.

Import Dialog:

![alt text](https://github.com/Axway-API-Management-Plus/Policy_Shortcut_Chain_Example/blob/master/example/src/importFrag.png "Import Fragment")

## Usage

- Set an endpoint for the core policy and deploy.
- Send a sample request message to the policy.

![alt text](https://github.com/Axway-API-Management-Plus/Policy_Shortcut_Chain_Example/blob/master/example/src/exampleOutput.png "Sample Output")

- Review Traffic Monitor (https://apihost:8090) and view the policy execution, with each component tracked as part of the whole execution.

![alt text](https://github.com/Axway-API-Management-Plus/Policy_Shortcut_Chain_Example/blob/master/example/src/shortcutChainExecution.png "Traffic Monitor Execution")


## Bug and Caveats

N/A


## Contributing

Please read [Contributing.md](https://github.com/Axway-API-Management/Common/blob/master/Contributing.md) for details on our code of conduct, and the process for submitting pull requests to us.


## Team

![alt text][Axwaylogo] Axway Team

[Axwaylogo]: https://github.com/Axway-API-Management/Common/blob/master/img/AxwayLogoSmall.png  "Axway logo"

Contact - Daniel Wille: dwille@axway.com

## License
[Apache License 2.0](/LICENSE)
