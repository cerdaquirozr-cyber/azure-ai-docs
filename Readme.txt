# https://feedback.azure.com/d365community/forum/79b1327d-d925-ec11-b6e6-000d3a4f06a4
layout: Conceptual
title: Microsoft Foundry Models quotas and limits - Microsoft Foundry | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/azure/foundry/foundry-models/quotas-limits
breadcrumb_path: ../../breadcrumb/azure-ai/toc.json
feedback_help_link_url: https://learn.microsoft.com/answers/tags/133/azure
feedback_help_link_type: get-help-at-qna
feedback_product_url: https://feedback.azure.com/d365community/forum/79b1327d-d925-ec11-b6e6-000d3a4f06a4
feedback_system: Standard
permissioned-type: public
recommendations: true
recommendation_types:
- Training
- Certification
uhfHeaderId: azure-ai-foundry
ms.suite: office
learn_banner_products:
- azure
ms.update-cycle: 90-days
ms.service: azure-ai-foundry
description: Learn about quotas, rate limits, and best practices for Foundry Models, including per-model token and request limits, client timeouts, and how to request increases.
ai-usage: ai-assisted
author: msakande
ms.subservice: azure-ai-foundry-model-inference
ms.custom:
- ignite-2024, github-universe-2024
- classic-and-new
- doc-kit-assisted
ms.topic: concept-article
ms.date: 2026-02-20T00:00:00.0000000Z
ms.author: mopeakande
ms.reviewer: haakar
reviewer: haakar
locale: en-us
document_id: 39754562-9c90-b534-a102-c37731dd5bac
document_version_independent_id: e0225227-41a6-b931-eb58-06b23a3ba97b
updated_at: 2026-03-20T06:04:00.0000000Z
original_content_git_url: https://github.com/MicrosoftDocs/azure-ai-docs-pr/blob/live/articles/foundry/foundry-models/quotas-limits.md
gitcommit: https://github.com/MicrosoftDocs/azure-ai-docs-pr/blob/cc37c00d2f73894ee94b4b90626a667de2b04bee/articles/foundry/foundry-models/quotas-limits.md
git_commit_id: cc37c00d2f73894ee94b4b90626a667de2b04bee
site_name: Docs
depot_name: Learn.azure-ai
page_type: conceptual
toc_rel: ../toc.json
word_count: 824
asset_id: foundry/foundry-models/quotas-limits
moniker_range_name: 
monikers: []
item_type: Content
source_path: articles/foundry/foundry-models/quotas-limits.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/cbd33d8f-e9af-440e-8f1e-fc69e07b902b
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/8a6e4dad-7050-4ce7-83f9-eb4123577a54
- https://authoring-docs-microsoft.poolparty.biz/devrel/68ec7f3a-2bc6-459f-b959-19beb729907d
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3820371b-086e-47fb-9d1f-b215f569127a
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/0a5fc323-00ce-4c20-9095-41948f54c83f
- https://authoring-docs-microsoft.poolparty.biz/devrel/90370425-aca4-4a39-9533-d52e5e002a5d
platformId: b1fb4085-2537-88e8-6b4b-5c2e9352c500
---

# Microsoft Foundry Models quotas and limits - Microsoft Foundry | Microsoft Learn

This article provides a quick reference and detailed description of the quotas and limits for [Foundry Models sold directly by Azure](concepts/models-sold-directly-by-azure). For quotas and limits specific to the Azure OpenAI in Foundry Models, see [Quotas and limits in Azure OpenAI](../openai/quotas-limits).

## Quotas and limits reference

The following sections provide a quick guide to the default quotas and limits that apply to Foundry Models:

### Resource limits (per Azure subscription, per region)

| Limit name | Limit value |
| --- | --- |
| Foundry resources per region per Azure subscription | 100 |
| Max projects per resource | 250 |
| Max deployments per resource (model deployments within a Foundry resource) | 32 |

### Rate limits

The following table lists limits for Foundry Models for the following rates:

- Tokens per minute
- Requests per minute
- Concurrent request

| Models | Tokens per minute | Requests per minute | Concurrent requests |
| --- | --- | --- | --- |
| Azure OpenAI models | Varies per model and SKU. See [limits for Azure OpenAI](../openai/quotas-limits). | Varies per model and SKU. See [limits for Azure OpenAI](../openai/quotas-limits). | Varies. See [Azure OpenAI limits](../openai/quotas-limits). |
| - DeepSeek-R1- DeepSeek-V3-0324 | 5,000,000 | 5,000 | 300 |
| - Llama 3.3 70B Instruct- Llama-4-Maverick-17B-128E-Instruct-FP8- Grok 3- Grok 3 mini | 400,000 | 1,000 | 300 |
| - Flux.2-Pro | not applicable | - Low (Default): 15  - Medium: 30  - High (Enterprise): 100 | not applicable |
| - Flux-Pro 1.1 - Flux.1-Kontext Pro | not applicable | 2 capacity units (6 requests per minute) | not applicable |
| Rest of models | 400,000 | 1,000 | 300 |

To increase your quota:

- For Azure OpenAI, use [Foundry Service: Request for Quota Increase](https://customervoice.microsoft.com/Pages/ResponsePage.aspx?id=v4j5cvGGr0GRqy180BHbR4xPXO648sJKt4GoXAed-0pUMFE1Rk9CU084RjA0TUlVSUlMWEQzVkJDNCQlQCN0PWcu) to submit your request.
- For other models, see request increases to the default limits.

Due to high demand, limit increase requests are evaluated individually.

### Other limits

| Limit name | Limit value |
| --- | --- |
| Max number of custom headers in API requests^1^ | 10 |

^1^ Current APIs allow up to 10 custom headers, which the pipeline passes through and returns. If you exceed this header count, your request results in an HTTP 431 error. To resolve this error, reduce the header volume. **Future API versions won't pass through custom headers**. Don't depend on custom headers in future system architectures.

## Usage tiers

Global Standard deployments use Azure's global infrastructure to dynamically route customer traffic to the data center with best availability for the customer's inference requests. This infrastructure enables more consistent latency for customers with low to medium levels of traffic. Customers with high sustained levels of usage might see more variabilities in response latency.

The Usage Limit determines the level of usage above which customers might see larger variability in response latency. A customer's usage is defined per model and is the total tokens consumed across all deployments in all subscriptions in all regions for a given tenant.

## Request increases to the default limits

Submit the [quota increase request form](https://aka.ms/oai/stuquotarequest) to request quota increases for [Foundry Models sold directly by Azure](concepts/models-sold-directly-by-azure), Azure OpenAI models, and Anthropic models. Except for Anthropic models, [Models from partners and community](concepts/models-from-partners) don't support quota increases.

Quota increase requests are processed in the order they're received, and priority goes to customers who actively use their existing quota allocation. Requests that don't meet this condition might be denied.

## General best practices to stay within rate limits

To minimize issues related to rate limits, use the following techniques:

- Implement retry logic in your application.
- Avoid sharp changes in the workload. Increase the workload gradually.
- Test different load increase patterns.
- Increase the quota assigned to your deployment. Move quota from another deployment, if necessary.

## Setting client-side timeout

Set the client-side timeout explicitly based on the following guidance.

Note

If not explicitly set, the client side timeout exists as per the library used, and may not be the same limits as above.

- Reasoning models (models that generate intermediate reasoning tokens before producing a summarized response): up to 29 minutes.
- Non-reasoning models:
    - For streaming, up to 60 seconds.
    - For non-streaming requests, up to 29 minutes.

29 minutes here does not mean all requests will take 29 minutes but rather depending on context tokens, generated tokens, and cache hit rates, requests can take up to 29 minutes.

Set a timeout that's less than these values, tuned to your traffic patterns.

For reasoning models including streaming requests, all the reasoning tokens are first generated and then summarized before sending the first response token back to the user.

You can modify the [reasoning effort](../openai/how-to/reasoning) parameter to control the number of reasoning tokens generated in the process.

## Troubleshooting

| Symptom | Cause | Resolution |
| --- | --- | --- |
| HTTP 429 Too Many Requests | Token-per-minute or request-per-minute limit exceeded | Implement retry logic with exponential backoff. Use the `Retry-After` header value. |
| HTTP 431 Request Header Fields Too Large | More than 10 custom headers sent | Reduce custom headers to 10 or fewer. |
| Quota page shows 0 available | Subscription or regional quota fully allocated | Move unused quota from another deployment. To increase your limit, request a quota increase. |
| Model not available in region | Model isn't deployed or supported in the selected region | Check [model availability](concepts/models-sold-directly-by-azure) and choose an available region. |
