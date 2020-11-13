---
title: Azure SDK for JavaScript (November 2020)
layout: post
tags: javascript typescript
sidebar: releases_sidebar
repository: azure/azure-sdk-for-js
---

The Azure SDK team is pleased to make available the November 2020 client library release.

#### GA

- _REMEMBER TO ADD YOUR GA PACKAGES_
- Azure Identity.
- Azure Tables.

#### Updates

- _REMEMBER TO ADD YOUR UPDATE PACKAGES_

#### Beta

- _REMEMBER TO ADD YOUR BETA PACKAGES_
- Azure Service Bus.

## Installation Instructions

To install the packages, copy and paste the below into a terminal.

```bash
$> npm install @azure/identity
$> npm install @azure/tables
$> npm install @azure/service-bus@next
```

## Feedback

If you have a bug or feature request for one of the libraries, please post an issue at the [azure-sdk-for-js repository](https://github.com/azure/azure-sdk-for-js/issues)

## Release highlights

---

=== COPY THIS AND ADD THE INFORMATION OF YOUR PACKAGE: ===

Keep in mind that:

- Including the package name in the headers makes the URL links work for multiple packages.
- The format of this file will be cleaned up once all of your proposals are in.

---

### _Project name_ 

#### @azure/_package-name_@_version_ [Changelog](https://github.com/Azure/azure-sdk-for-js/blob/master/sdk/<service-folder>/<package-folder>/CHANGELOG.md)

(leave blank)

##### Breaking Changes on @azure/_package-name_@_version_

- _Add one or more, or remove the "Breaking Changes on ..." entire section._

##### New Features on @azure/_package-name_@_version_

- _Add one or more, or remove the "New Features on ..." section._

##### Major Fixes on @azure/_package-name_@_version_

- _Add one or more, or remove the "Major Fixes on ..." section._

---

### Identity

We're glad to announce a new major release of our Identity package. This release includes standardized `ManagedIdentityCredential` support across languages, as well as improvements to `VisualStudioCodeCredential`, `DeviceCodeCredential` and `InteractiveBrowserCredential`.

#### @azure/identity@1.2.0 [Changelog](https://github.com/Azure/azure-sdk-for-js/blob/master/sdk/identity/identity/CHANGELOG.md#120-2020-11-11)

##### New Features on @azure/identity@1.2.0

- A new dependency has been added: the Microsoft Authentication Library (MSAL). MSAL allows us to provide secure and reliable implementations for `InteractiveBrowserCredential` and `DeviceCodeCredential`. 
- `InteractiveBrowserCredential` now works for Node, which spawns the user's browser and connects via a browser-based auth code flow.
- With 1.2, we've added support for Azure Arc to our Managed Identity credential.
- Identity now supports Subject Name/Issuer (SNI) as part of authentication for ClientCertificateCredential.
- Added Active Directory Federation Services authority host support to the node credentials.
- Added support for multiple clouds on `VisualStudioCodeCredential`.

##### Major Fixes on @azure/identity@1.2.0

- Added support for authenticating with user assigned identities on Azure App Service.

### Azure Tables

We're releasing a new preview of our Azure Tables library. This update provides more idiomatic names to the system properties for `odata.etag` and `Timestamp`.

#### @azure/data-tables@1.0.0-beta3 [Changelog](https://github.com/Azure/azure-sdk-for-js/blob/master/sdk/tables/data-tables/CHANGELOG.md)

##### Major fixes on @azure/data-tables@1.0.0-beta3

Renamed system properties `odata.etag` and `Timestamp` to provide more idiomatic property names. Queried entities now get the properties `etag` and `timestamp` instead of `odata.etag` and `Timestamp`,

### Service Bus

This is the last preview version of the Azure Service Bus client library before releasing it for general availability later this month, this release includes improvements in error handling, various interface/method/type updates and internal improvements in terms of memory consumption.

#### @azure/service-bus@7.0.0-preview.8 [Changelog](https://github.com/Azure/azure-sdk-for-js/blob/master/sdk/servicebus/service-bus/CHANGELOG.md#700-preview8-2020-11-04)

##### Breaking Changes on @azure/service-bus@7.0.0-preview.8

- The `processError` passed to `Receiver.subscribe` now receives a `ProcessErrorArgs` instead of just an error. This parameter provides additional context that can make it simpler to distinguish errors that were thrown from your callback (via the `errorSource` member of `ProcessErrorArgs`) as well as giving you some information about the entity that generated the error.
- The methods to complete, abandon, defer and deadletter a message along with the method to renew message lock have been moved from the message to the receiver. With this, we now have additional validation to ensure that a peeked message cannot be used with these methods.
- Returned responses from the methods under the `ServiceBusAdministrationClient` now use a generic type `WithResponse<T>` for a cleaner API surface. The raw responses(`_response`) have been updated to return only the `{request, status, headers}`, properties such as `parsedHeaders`, `parsedBody` have been removed.
- Removed `AmqpAnnotatedMessage`, `AmqpMessageHeaders`, `AmqpMessageProperties` interfaces in favour of the ones from `@azure/core-amqp`. This is part of the move from `@azure/core-amqp` version update from 1.1.x to 2.0.0. As part of this, `userId` will not be made available as part of `AmqpMessageProperties` until its type is fixed in the upstream `rhea` library.
- Many other updates to methods, interfaces, types, and names based on user studies and internal reviews, more info at [Changelog](https://github.com/Azure/azure-sdk-for-js/blob/master/sdk/servicebus/service-bus/CHANGELOG.md#700-preview8-2020-11-04)

##### New Features on @azure/service-bus@7.0.0-preview.8

- A helper method parseServiceBusConnectionString has been added which validates and parses a given connection string for Azure Service Bus. You can use this to extract the namespace and entityPath details from the connection string.
- Tracing, using [@azure/core-tracing](https://github.com/Azure/azure-sdk-for-js/blob/master/sdk/core/core-tracing/README.md), has been added for sending and receiving of messages.

##### Major fixes on @azure/service-bus@7.0.0-preview.8

- Internal improvements that would affect memory consumption for the operations depending on `$management` link such as peeking into messages or message lock renewals or session lock renewals: 
  - If made parallel requests before the link initialization, it would have resulted in a warning such as `MaxListenersExceededWarning: Possible EventEmitter memory leak detected. 11 sender_error listeners added to [Sender]. Use emittr.setMaxListeners() to increase limit(same for receiver_error)`. This has been improved such that the listeners are reused to avoid the issue of adding many event listeners.
  - With many ongoing outstanding requests, warning such as `MaxListenersExceededWarning: Possible EventEmitter memory leak detected. 11 message listeners added to [Receiver]. Use emittr.setMaxListeners() to increase limit` is observed. The issue has been fixed in the dependency `@azure/core-amqp` by making the requests to reuse the listeners, this is part of the move from `@azure/core-amqp` version update from 1.1.x to 2.0.0.

## Latest Releases

View all the latest versions of JavaScript packages [here][js-latest-releases].

{% include refs.md %}
