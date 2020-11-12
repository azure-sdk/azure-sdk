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
- Azure Core AMQP.
- Azure Service Bus.

## Installation Instructions

To install the packages, copy and paste the below into a terminal.

```bash
$> npm install @azure/package-name
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

#### @azure/identity@1.2.0 [Changelog](https://github.com/Azure/azure-sdk-for-js/blob/master/sdk/identity/identity/CHANGELOG.md#120-2020-11-11)

We're glad to announce a new major release of our Identity package. This release includes standardized `ManagedIdentityCredential` support across languages, as well as improvements to `VisualStudioCodeCredential`, `DeviceCodeCredential` and `InteractiveBrowserCredential`.

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

#### @azure/data-tables@1.0.0-beta3 [Changelog](https://github.com/Azure/azure-sdk-for-js/blob/master/sdk/tables/data-tables/CHANGELOG.md)

We're releasing a new preview of our Azure Tables library. This update provides more idiomatic names to the system properties for `odata.etag` and `Timestamp`.

##### Major fixes on @azure/data-tables@1.0.0-beta3

Renamed system properties `odata.etag` and `Timestamp` to provide more idiomatic property names. Queried entities now get the properties `etag` and `timestamp` instead of `odata.etag` and `Timestamp`,

## Latest Releases

View all the latest versions of JavaScript packages [here][js-latest-releases].

{% include refs.md %}
