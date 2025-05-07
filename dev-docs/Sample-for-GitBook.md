---
title: Sample for GitBook
slug: qCqT-sample
createdAt: 2025-05-05T10:21:54.153Z
updatedAt: 2025-05-07T10:30:17.256Z
---

Multi-source Company data is designed to be used for **s****ales tech, m****arket research, investment, and risk assessment**.

| ----------------------------------------- | ------------------------------------------------------------------------------------------ |
| **Save engineering resources** | Our Multi-source company data is cleaned, enriched, filtered, and ready to use. |


| ----------------------------------------- | ------------------------------------------------------------------------------------------ |
| **Comprehensive multi-source dataset** | Multiple sources are integrated to provide a complete company overview. |


| ----------------------------------------- | ------------------------------------------------------------------------------------------ |
| **Optimized file sizes and formats ** | JSONL, Parquet, and CSV formats and smaller file sizes for faster download. |


| ----------------------------------------- | ------------------------------------------------------------------------------------------ |
| **Leverage historical data** | Track changes in company metrics over time with aggregated historical data. |


***

## Summary

| Feature            | Details                                                  |
| ------------------ | -------------------------------------------------------- |
| Record count       | 39,417,865+                                              |
| Available via      | Flat files/API                                           |
| Available formats  | Parquet, JSONL, and CSV                                  |
| Delivery frequency | Monthly and quarterly                                    |
| Delivery methods   | Direct download link or file upload to a cloud server.\* |

\* We can provide a link and credentials for you to download the dataset, or we can upload the data directly to your cloud server (S3, Azure, Google Cloud, etc.).

***

## Data overview

The Multi-source Companies dataset contains information from various sources organized into different sections. Here's an overview of what's included in each section:

{% hint style="info" %}
The data points might differ depending on your chosen data format (API or flat file data).
{% endhint %}

## Aggregated data: Multi-source company dataset

Currently, we offer one aggregated dataset: the <a href="https://docs.coresignal.com/source-documentation/multi-source-company-dataset" target="_blank">**Multi-source company dataset**</a>. It contains comprehensive profiles of about 35 million global companies.

You can find all the relevant information by following the links below:

::::LinkArray
:::LinkArrayItem{headerType="IMAGE" headerImage="https://archbee-image-uploads.s3.amazonaws.com/MGWNg74I8iHIMOnqORYtE-k8VdDP_7MiqngxP4-T9yz-20240909-141237.png"}
### [Data dictionary](https://docs.coresignal.com/source-documentation/multi-source-company-data-dictionary)

Review all data points, their descriptions, and data types
:::

:::LinkArrayItem{headerType="IMAGE" headerImage="https://archbee-image-uploads.s3.amazonaws.com/MGWNg74I8iHIMOnqORYtE-Lt0n4qDyX3mK7vS1cEzTD-20240909-141247.png"}
### [Data sample](https://docs.coresignal.com/source-documentation/multi-source-company-data-sample)

Take a closer look at the data sample – review it as a JSON file
:::
::::

# Database APIs

Database APIs are an umbrella term for our endpoint clusters, which retrieve Professional Network Employee, Company, and Job posting data.

More information on our APIs:

::::LinkArray
:::LinkArrayItem{headerImage headerColor}
### [General information on  Database API](https://docs.coresignal.com/api/database-apis-overview-page)
:::

:::LinkArrayItem{headerImage headerColor}
### [General information on Employee API](https://docs.coresignal.com/api/employee-api-overview-page)
:::
::::

:::::ExpandableHeading
## Employee API endpoints

Use Employee API to collect the Professional Network Employee. Follow the links to read about Employee API endpoints:

::::LinkArray
:::LinkArrayItem{headerImage headerColor}
### [Search filters endpoint](https://docs.coresignal.com/api/employee-api-search-filters-endpoint)
:::

:::LinkArrayItem{headerImage headerColor}
### [Elasticsearch endpoint](https://docs.coresignal.com/api/employee-api-esdsl-endpoint)
:::
::::
:::::

:{% hint style="success" %}
**Try out the data for free**

Our data speaks for itself, and we are excited to show it to you. 

Once you create your account, you will have 14 days to explore the data.
{% endhint %}CtaButton{url="https://dashboard.coresignal.com/sign-up" label="Start now"}

:::
::::



| ----------------------------------------- | ------------------------------------------------------------------------------------------ |
| ## Certified by Ethical Web Data Collection Initiative

Coresignal is a founding member of the Ethical Web Data Collection Initiative (EWDCI), an organization that advocates for responsible web data collection and protection of personal data.

Coresignal has undergone an accreditation process to confirm that we follow the four core principles of ethical web data collection: legality, ethics, ecosystem engagement, and social responsibility.‍

These principles guide Coresignal through every step of data collection – from the data we gather to the partnerships we form with our clients. | ![](https://archbee-image-uploads.s3.amazonaws.com/ncD4eDm2Dzj39qqKM85f5-52bg9Ph4hYhgykRfMiy8b-20241105-115723.png) |


::::Tabs
:::Tab{title="01. Legality"}


We only collect publicly available data that companies and individuals disclose to the general public to facilitate their business and profession-related interests. We strive to ensure our employees are well-informed about personal data protection and the latest developments in privacy regulations. We are supported by legal counsels, who provide expert advice on a range of complex legal matters, including privacy.
:::

:::Tab{title="02. Ethics"}
We follow a strict ethical framework, including ethical principles related to websites, customers, proxies, and data.
:::

:::Tab{title="03. Ecosystem"}
We are in a symbiotic relationship with the free and open Internet ecosystem and strive to engage it collaboratively openly and communicatively.
:::

:::Tab{title="04. Responsibility"}
We pledge to support and collaborate with civil society and governmental organizations for societal benefit.
:::
::::

# Overview

Welcome to our dataset documentation. Coresignal offers three main data categories:

- **Company data** – comprehensive global company profiles for sales tech, industry research, investment, or lead enrichment
- **Employee data **– Up-to-date** **and full** **profiles for recruitment, HR tech, investment, and trend research.
- **Job posting data **– freshly collected jobs for competitive intelligence and market research.

Contains explanations and examples of all data fields available in the **Glassdoor**** ****Salaries**** **dataset.

{% hint style="info" %}
All personal/company information mentioned within this context is entirely fictional and is solely intended for illustrative purposes.
{% endhint %}

::::Tabs
:::Tab{title="Data points by category"}
1. [Data Dictionary](docId:05VpOD4noloTMTpAz0g6K)&#x20;
2. [Data Dictionary](docId:05VpOD4noloTMTpAz0g6K)&#x20;
3. [Data Dictionary](docId:05VpOD4noloTMTpAz0g6K)&#x20;
4. [Data Dictionary](docId:05VpOD4noloTMTpAz0g6K)&#x20;
:::
::::

# Metadata

## Record metadata

| Data point             | Description                                          | Data type                  |
| ---------------------- | ---------------------------------------------------- | -------------------------- |
| `meta`                 | Contains metadata about the record                   | Object                     |
| `created_at_date`      | Date when the record was initially scraped           | Array of numbers (integer) |
| `created_at_timestamp` | Unix timestamp for when the record was first scraped | Float                      |
| `updated_at_date`      | Date when the record was last updated                | Array of numbers (integer) |

### **See a snippet of the dataset for reference:**

:::CodeblockTabs
Meta fields

```json
		"_meta": {
			"created_at_date": [
				2024,
				1,
				1
			],
			"created_at_timestamp": 123456789.987654,
			"updated_at_date": [
				2025,
				1,
				1
			],
			"updated_at_timestamp": 987654321.123456,
			"version_id": "123a4b56",
			"source": "glassdoor",
			"object": "salaries",
			"is_deleted": false
		},
```
:::

:::ExpandableHeading
## Record metadata

| Data point             | Description                                          | Data type                  |
| ---------------------- | ---------------------------------------------------- | -------------------------- |
| `meta`                 | Contains metadata about the record                   | Object                     |
| `created_at_date`      | Date when the record was initially scraped           | Array of numbers (integer) |
| `created_at_timestamp` | Unix timestamp for when the record was first scraped | Float                      |
| `updated_at_date`      | Date when the record was last updated                | Array of numbers (integer) |
:::



- [ ] `updated_at_timestamp`
- [ ] updated\_at\_timestamp

[](https://archbee-doc-uploads.s3.amazonaws.com/AohZQYiaoDRifcp3U9eJu-EFunz1BloxO0GIBrelOTF-20250506-114205.json)

***

::::WorkflowBlock
:::WorkflowBlockItem
1st step

Description 123456789
:::

:::WorkflowBlockItem
2nd step

Description 2 123456789
:::
::::

::Image[]{src="https://archbee-image-uploads.s3.amazonaws.com/AohZQYiaoDRifcp3U9eJu-Pon0gl-9b6xCsd-vUhSu4-20250403-093315.svg" signedSrc size="16" width="140" height="140" position="center" caption}

## Video

::embed[]{url="https://www.youtube.com/watch?v=ZSJ-lYB5E-M"}

