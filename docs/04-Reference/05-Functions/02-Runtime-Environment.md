---
alias: lah7reidae
description: Graphcool Functions can run either inline or using a remote webhook.
---

# Runtime Environment

## Runtime environment for managed functions

**Managed functions** can be specified using the functions editor in the Console. They run on a node runtime and **all npm modules are available for import**.

<InfoBox type=warning>

Notice that the **maximum execution time of a managed function is 15 seconds**.

</InfoBox>

### Node runtime

Currently, node version `4.8.4` is the runtime environment, but we're looking [to upgrade that to version 8 soon](https://github.com/graphcool/feature-requests/issues/237). By default, ES5 is supported. By starting a function with the line `'use latest'` however, you get access to ES6 features.

### Function containers

Inline functions are managed in separate containers. For performance reasons, all functions within a project are executed in the same container, but there is no way for functions in different projects to interact with each other. As such, secret API Keys or other confidential information is kept secure when included in a function.

### Environment variables

A centralized way to organize environment variables or secrets is planned and being discussed in [this feature request](https://github.com/graphcool/feature-requests/issues/229). Chime in to share your thoughts!

## Webhooks

Functions can also be deployed as **webhooks** using Function-as-a-service providers such as [Serverless](https://serverless.com/) and [AWS Lambda](https://aws.amazon.com/lambda/), [Google Cloud Functions](https://cloud.google.com/functions/), [Microsoft Azure Functions](https://azure.microsoft.com/) or by hosting the function yourself. Then you need to provide the webhook URL.

## About callbacks and promises

All functions should return a promise, that will be resolved by the Graphcool Functions Engine. Callbacks are not supported and need to be converted to Promises (as shown [in this  guide](https://egghead.io/lessons/javascript-convert-a-callback-to-a-promise)).

