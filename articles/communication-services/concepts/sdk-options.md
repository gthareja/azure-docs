---
title: Client libraries and REST APIs for Azure Communication Services
titleSuffix: An Azure Communication Services concept document
description: Learn more about Azure Communication Services SDKs and REST APIs.
author: mikben
manager: jken
services: azure-communication-services

ms.author: mikben
ms.date: 03/10/2021
ms.topic: conceptual
ms.service: azure-communication-services
---
# Client libraries and REST APIs

[!INCLUDE [Public Preview Notice](../includes/public-preview-include.md)]


Azure Communication Services capabilities are conceptually organized into six areas. Some areas have fully open-sourced SDKs. The Calling SDK uses proprietary network interfaces and is currently closed-source, and the Chat library includes a closed-source dependency. Samples and additional technical details for SDKs are published in the [Azure Communication Services GitHub repo](https://github.com/Azure/communication).

## Client libraries

| Assembly               | Protocols             |Open vs. Closed Source| Namespaces                          | Capabilities                                                      |
| ---------------------- | --------------------- | ---|-------------------------- | --------------------------------------------------------------------------- |
| Azure Resource Manager | REST | Open            | Azure.ResourceManager.Communication | Provision and manage Communication Services resources             |
| Common                 | REST | Open               | Azure.Communication.Common          | Provides base types for other SDKs |
| Identity         | REST | Open               | Azure.Communication.Identity  | Manage users, access tokens |
| Phone numbers         | REST | Open               | Azure.Communication.PhoneNumbers  | Managing phone numbers |
| Chat                   | REST with proprietary signaling | Open with closed source signaling package    | Azure.Communication.Chat            | Add real-time text based chat to your applications  |
| SMS                    | REST | Open              | Azure.Communication.SMS             | Send and receive SMS messages |
| Calling                | Proprietary transport | Closed |Azure.Communication.Calling         | Leverage voice, video, screen-sharing, and other real-time data communication capabilities          |

Note that the Azure Resource Manager, Identity, and SMS SDKs are focused on service integration, and in many cases security issues arise if you integrate these functions into end-user applications. The Common and Chat SDKs are suitable for service and client applications. The Calling SDK is designed for client applications. An SDK focused on service scenarios is in development.

### Languages and publishing locations

Publishing locations for individual SDK packages are detailed below.

| Area           | JavaScript | .NET | Python | Java SE | iOS | Android | Other                          |
| -------------- | ---------- | ---- | ------ | ---- | -------------- | -------------- | ------------------------------ |
| Azure Resource Manager | -         | [NuGet](https://www.nuget.org/packages/Azure.ResourceManager.Communication)    |   [PyPi](https://pypi.org/project/azure-mgmt-communication/)    |  -  | -              | -  | [Go via GitHub](https://github.com/Azure/azure-sdk-for-go/releases/tag/v46.3.0) |
| Common         | [npm](https://www.npmjs.com/package/@azure/communication-common)         | [NuGet](https://www.nuget.org/packages/Azure.Communication.Common/)    | N/A      | [Maven](https://search.maven.org/search?q=a:azure-communication-common)   | [GitHub](https://github.com/Azure/azure-sdk-for-ios/releases)            | [Maven](https://search.maven.org/artifact/com.azure.android/azure-communication-common)             | -                              |
| Identity | [npm](https://www.npmjs.com/package/@azure/communication-identity)         | [NuGet](https://www.nuget.org/packages/Azure.Communication.Identity)    | [PyPi](https://pypi.org/project/azure-communication-identity/)      | [Maven](https://search.maven.org/search?q=a:azure-communication-identity)   | -              | -              | -                            |
| Phone Numbers | [npm](https://www.npmjs.com/package/@azure/communication-phone-numbers)         | [NuGet](https://www.nuget.org/packages/Azure.Communication.PhoneNumbers)    | [PyPi](https://pypi.org/project/azure-communication-phonenumbers/)      | [Maven](https://search.maven.org/search?q=a:azure-communication-phonenumbers)   | -              | -              | -                            |
| Chat           | [npm](https://www.npmjs.com/package/@azure/communication-chat)        | [NuGet](https://www.nuget.org/packages/Azure.Communication.Chat)     | [PyPi](https://pypi.org/project/azure-communication-chat/)     | [Maven](https://search.maven.org/search?q=a:azure-communication-chat)   | [GitHub](https://github.com/Azure/azure-sdk-for-ios/releases)  | [Maven](https://search.maven.org/search?q=a:azure-communication-chat)   | -                              |
| SMS            | [npm](https://www.npmjs.com/package/@azure/communication-sms)         | [NuGet](https://www.nuget.org/packages/Azure.Communication.Sms)    | [PyPi](https://pypi.org/project/azure-communication-sms/)       | [Maven](https://search.maven.org/artifact/com.azure/azure-communication-sms)   | -              | -              | -                              |
| Calling        | [npm](https://www.npmjs.com/package/@azure/communication-calling)         | -      | -      | -     | [GitHub](https://github.com/Azure/Communication/releases)     | [Maven](https://search.maven.org/artifact/com.azure.android/azure-communication-calling/)            | -                              |
| Reference Documentation     | [docs](https://azure.github.io/azure-sdk-for-js/communication.html)         | [docs](https://azure.github.io/azure-sdk-for-net/communication.html)      | -      | [docs](http://azure.github.io/azure-sdk-for-java/communication.html)     | [docs](/objectivec/communication-services/calling/)      | [docs](/java/api/com.azure.communication.calling)            | -                              |

## REST APIs

Communication Services APIs are documented alongside other Azure REST APIs in [docs.microsoft.com](/rest/api/azure/). This documentation will tell you how to structure your HTTP messages and offers guidance for using Postman. This documentation is also offered in Swagger format on [GitHub](https://github.com/Azure/azure-rest-api-specs).

## Additional support details

### iOS and Android support details

- Communication Services iOS SDKs target iOS version 13+, and Xcode 11+.
- Android Java SDKs target Android API level 21+ and Android Studio 4.0+

### .NET support details

With the exception of Calling, Communication Services packages target .NET Standard 2.0 which supports the platforms listed below.

Support via .NET Framework 4.6.1
- Windows 10, 8.1, 8 and 7
- Windows Server 2012 R2, 2012 and 2008 R2 SP1

Support via .NET Core 2.0:
- Windows 10 (1607+), 7 SP1+, 8.1
- Windows Server 2008 R2 SP1+
- Max OS X 10.12+
- Linux multiple versions/distributions
- UWP 10.0.16299 (RS3) September 2017
- Unity 2018.1
- Mono 5.4
- Xamarin iOS 10.14
- Xamarin Mac 3.8

## Calling SDK timeouts

The following timeouts apply to the Communication Services Calling SDKs:

| Action           | Timeout in seconds |
| -------------- | ---------- |
| Reconnect/removal participant | 120 |
| Add or remove new modality from a call (Start/stop video or screen sharing) | 40 |
| Call Transfer operation timeout | 60 |
| 1:1 call establishment timeout | 85 |
| Group call establishment timeout | 85 |
| PSTN call establishment timeout | 115 |
| Promote 1:1 call to a group call timeout | 115 |


## API stability expectations

> [!IMPORTANT]
> This section provides guidance on REST APIs and SDKs marked **stable**. APIs marked pre-release, preview, or beta may be changed or deprecated **without notice**.

In the future we may retire versions of the Communication Services SDKs, and we may introduce breaking changes to our REST APIs and released SDKs. Azure Communication Services will *generally* follow two supportability policies for retiring service versions:

- You'll be notified at least three years before being required to change code due to a Communication Services interface change. All documented REST APIs and SDK APIs generally enjoy at least three years warning before interfaces are decommissioned.
- You'll be notified at least one year before having to update SDK assemblies to the latest minor version. These required updates shouldn't require any code changes because they're in the same major version. This is especially true for the Calling and Chat libraries which have real-time components that frequently require security and performance updates. We highly encourage you to keep your Communication Services SDKs updated.

### API and SDK decommissioning examples

**You've integrated the v24 version of the SMS REST API into your application. Azure Communication releases v25.**

You'll get 3 years warning before these APIs stop working and are forced to update to v25. This update might require a code change.

**You've integrated the v2.02 version of the Calling SDK into your application. Azure Communication releases v2.05.**

You may be required to update to the v2.05 version of the Calling SDK within 12 months of the release of v2.05. This should be a simple replacement of the artifact without requiring a code change because v2.05 is in the v2 major version and has no breaking changes.

## Next steps

For more information, see the following SDK overviews:

- [Calling SDK Overview](../concepts/voice-video-calling/calling-sdk-features.md)
- [Chat SDK Overview](../concepts/chat/sdk-features.md)
- [SMS SDK Overview](../concepts/telephony-sms/sdk-features.md)

To get started with Azure Communication Services:

- [Create Azure Communication Resources](../quickstarts/create-communication-resource.md)
- Generate [User Access Tokens](../quickstarts/access-tokens.md)
