---
description: Explore detailed field definitions for Coresignal's Base Company data, including company profiles, industry classifications, organizational attributes and much more.
---

Contains explanations and examples of all data fields available in the **Base Company **dataset.

{% hint style="info" %}
All company information mentioned in this data dictionary is fictional and is solely intended for illustrative purposes.
{% endhint %}

{% tabs %}
{% tab title="Updated tables" %}
1. [Company information](setup-guide.md)
2. [Affiliated](setup-guide.md)
3. [Also viewed](setup-guide.md)
4. [Financial website info](setup-guide.md)
5. [Featured employees](setup-guide.md)
6. [Investors](setup-guide.md)
7. [Funding rounds](setup-guide.md)
8. [Locations](setup-guide.md)
9. [Similar companies](setup-guide.md)
10. [Specialties](setup-guide.md)
11. [Stock info](setup-guide.md)
12. [Company updates](setup-guide.md)
{% endtab %}

{% tab title="Legacy tables" %}
**This dataset contains legacy tables that are either no longer filled or have low fill rates. **

1. [Also viewed](https://docs.coresignal.com/source-documentation/professional-network-companies-data-dictionary#EZ_sX)
{% endtab %}

{% endtabs %}

**

## Company information

<details>

<summary>Repeat fields</summary>

| Data point     | Description                                                                                                                                                                                                   | Data type        | Example values        |
| -------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------- | --------------------- |
| `id`           | Identification key for a company profile record.&#xA;<br />Each record in the dataset has its ID value.&#xA;&#xA;**ID** in the company table becomes **company\_id** later in the other tables of the dataset | number (integer) | *62195*               |
| `company_id`   | Company record ID assigned in the database                                                                                                                                                                    | number (integer) | *30707*               |
| `created`      | The time and date when we **first** scraped the record                                                                                                                                                        | string           | *2019-12-07 22:07:18* |
| `last_updated` | The time and date when we **last** scraped the record                                                                                                                                                         | string           | *2020-09-06 04:51:48* |
| `deleted`      | One of two values - **1 **or **0**<br />`1` - the last time we scraped the company page, *the Page not found *was returned<br />`0` - we successfully scraped the company profile                             | boolean          | *deleted: 0*          |


</details>

| Data point                      | Description                                                                                                                                 | Data type |
| ------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------- | --------- |
| `url`                           | Company's profile on the professional network                                                                                               | String    |
| `hash`                          | Profile URL processed by the MD5 algorithm                                                                                                  | String    |
| `name`                          | Name                                                                                                                                        | String    |
| `website`                       | Website                                                                                                                                     | String    |
| `size`                          | Size category                                                                                                                               | String    |
| `industry`                      | Associated industry                                                                                                                         | String    |
| `description`                   | Description                                                                                                                                 | String    |
| `followers`                     | Profile follower count                                                                                                                      | Integer   |
| `founded`                       | Founding year                                                                                                                               | Integer   |
| `headquarters_city`             | Headquarters location (city)&#xA;&#xA;**Note**: legacy field that is rarely filled                                                          | String    |
| `headquarters_country`          | Headquarters location (country)&#xA;&#xA;**Note**: legacy field that is rarely filled                                                       | String    |
| `headquarters_state`            | Headquarters location (state)&#xA;&#xA;**Note**: legacy field that is rarely filled                                                         | String    |
| `headquarters_street1`          | Headquarters location (street address)&#xA;&#xA;**Note**: legacy field that is rarely filled                                                | String    |
| `headquarters_street2`          | Headquarters location (street address)&#xA;&#xA;**Note**: legacy field that is rarely filled                                                | String    |
| `headquarters_zip`              | Headquarters location (zip code)&#xA;&#xA;**Note**: legacy field that is rarely filled                                                      | String    |
| `logo_url`                      | Logo URL                                                                                                                                    | String    |
| `last_response_code`            | Response code to the last scraping request                                                                                                  | Integer   |
| `type`                          | Company type                                                                                                                                | String    |
| `headquarters_new_address`      | Newly exposed company headquarters address                                                                                                  | String    |
| `employees_count`               | Number of employees on the professional network who associated their experience with the company                                            | Integer   |
| `headquarters_country_restored` | Country the company is based in (from our restored database)&#xA;&#xA;**Note**: legacy field that is rarely filled                          | String    |
| `headquarters_country_parsed`   | Country the company is based in (as parsed by our in-house country parser)                                                                  | String    |
| `company_shorthand_name`        | Dynamic part of the URL used to update the profile and identify companies                                                                   | String    |
| `company_shorthand_name_hash`   | Shorthand name of the company processed by the MD5 algorithm                                                                                | String    |
| `canonical_url`                 | Most recent profile URL                                                                                                                     | String    |
| `canonical_hash`                | `Canonical_url` processed by the MD5 algorithm                                                                                              | String    |
| `canonical_shorthand_name`      | Dynamic part of a `canonical_url`, used to identify companies&#xA;&#xA;(the part of the professional network URL that has the company name) | String    |
| `canonical_shorthand_name_hash` | Canonical shorthand name processed by the MD5 algorithm                                                                                     | String    |
| `last_updated_ux`               | Date and time when the record was last updated (Unix timestamp)                                                                             | Integer   |
| `source_id`                     | In-house company ID (static) on the professional network                                                                                    | Integer   |

**The main company table data sample:**

{% code title="Main company data" %}
```json
{
    "id": 111371,
    "url": "https://www.professional-network.com/company/luxury-store-brand",
    "hash": "83627f1b6ccb868ce2450d63124a1562",
    "name": "Luxury store brand",
    "website": "http://www.luxury-store-brand.com",
    "size": "1,001-5,000 employees",
    "industry": "Retail Apparel and Fashion",
    "description": "Luxury store brand is the go-to destination for chic, contemporary fashion. The brand evokes a mindset - an attitude, not an age. It's a true original, always defining fashion's next stride forward. Designed for the confident, sexy, modern woman, Luxury store brand is a global label that embodies a sensual, sophisticated lifestyle.\n\nChairman and Founder John Doe opened the first Luxury store brand boutique in 1980 in San Francisco. Recognizing a demographic that was neither junior nor bridge, Manny created the first contemporary fashion brand. Over 35 years later, Luxury store brand has established itself as one of the world's top fashion retailers.\n\nLuxury store brand STORES\n\nWithin its stores and on luxurystorebrand.com, Luxury store brand seeks to create an upscale, visually stimulating boutique environment while providing top-notch service to ensure an exceptional shopping experience. Stylists are knowledgeable, passionate about fashion and skilled at addressing clients' styling needs. Luxury store brand also offers a line of merchandise branded with the distinctive Luxury store brand logo for those who love to wear the Luxury store brand name.\n\nLuxury store brand markets its merchandise under the Luxury store brand and Luxury store brand outlet names through more than 200 retail stores, more than 100 international-licensee operated stores and luxury-store-brand.com. \n\nluxury-store-brand.com\nLaunched in 1998, luxury-store-brand.com continues the Luxury store brand store experience and provides a complete assortment of Luxury store brand merchandise to clients in the United States and internationally.",
    "followers": 23288,
    "founded": 1976,
    "headquarters_city": null,
    "headquarters_country": null,
    "headquarters_state": null,
    "headquarters_street1": null,
    "headquarters_street2": null,
    "headquarters_zip": null,
    "logo_url": "https://media.prof-ntwk.com/dms/image/C560BAQFmmRv6bZ4u_A/company-logo_200_200/0/1519856046980?e=2147483647&v=beta&t=PihtlecPzQHcPSUJFPYlpCI_KxUnwqOvzJqWgkr7StY",
    "created": "2016-06-17 20:08:21",
    "last_updated": "2023-09-09 18:08:29",
    "last_response_code": 200,
    "type": "Public Company",
    "headquarters_new_address": "Los Angeles, California",
    "employees_count": 1246,
    "headquarters_country_restored": "United States",
    "headquarters_country_parsed": "United States",
    "company_shorthand_name": "luxury-store-brand",
    "company_shorthand_name_hash": "44584e20693d123abce7729e4a2b9acb",
    "canonical_url": "https://www.professional-network.com/company/luxury-store-brand",
    "canonical_hash": "83627f1b6ccb868ce2450d63124a1562",
    "canonical_shorthand_name": "luxury-store-brand",
    "canonical_shorthand_name_hash": "44584e20693d123abce7729e4a2b9acb",
    "deleted": 0,
    "last_updated_ux": 1694282909,
    "source_id": 16753,
```
{% endcode %}

## **Affiliated **

<details>

<summary>Repeat fields</summary>

| Data point     | Description                                                                                                                                                                       | Data type        | Example values        |
| -------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------- | --------------------- |
| `id`           | Identification key for the record                                                                                                                                                 | number (integer) | *62195*               |
| `company_id`   | Company record ID assigned in the database                                                                                                                                        | number (integer) | *30707*               |
| `created`      | The time and date when we **first** scraped the record                                                                                                                            | string           | *2019-12-07 22:07:18* |
| `last_updated` | The time and date when we **last** scraped the record                                                                                                                             | string           | *2020-09-06 04:51:48* |
| `deleted`      | One of two values - **1 **or **0**<br />`1` - the last time we scraped the company page, *the Page not found *was returned<br />`0` - we successfully scraped the company profile | boolean          | *deleted: 0*          |


</details>

| Data point                      | Description                                                                                                    | Data type        |
| ------------------------------- | -------------------------------------------------------------------------------------------------------------- | ---------------- |
| `company_affiliated_collection` | Profiles of affiliated companies                                                                               | Array of objects |
| `affiliated_company_url`        | Affiliate company profile URL                                                                                  | String           |
| `affiliated_company_id`         | Identification key relating to the**company**table for the affiliate company&#xA;&#xA;**Note: **legacy field | Integer          |

**Affiliated table data sample:**

{% code title="Afiiliated table" %}
```json
"company_affiliated_collection": [
    {
        "id": 735765,
        "company_id": 7410562,
        "affiliated_company_url": "https://www.professional-network.com/company/rental-company",
        "affiliated_company_id": 7125453,
        "created": "2020-02-04 08:32:23",
        "last_updated": "2022-09-21 08:16:07",
        "deleted": 1
    }
],
```
{% endcode %}

## Also viewed

<details>

<summary>Repeat fields</summary>

| Data point     | Description                                                                                                                                                                       | Data type        | Example values        |
| -------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------- | --------------------- |
| `id`           | Identification key for the record                                                                                                                                                 | number (integer) | *62195*               |
| `company_id`   | Company record ID assigned in the database                                                                                                                                        | number (integer) | *30707*               |
| `created`      | The time and date when we **first** scraped the record                                                                                                                            | string           | *2019-12-07 22:07:18* |
| `last_updated` | The time and date when we **last** scraped the record                                                                                                                             | string           | *2020-09-06 04:51:48* |
| `deleted`      | One of two values - **1 **or **0**<br />`1` - the last time we scraped the company page, *the Page not found *was returned<br />`0` - we successfully scraped the company profile | boolean          | *deleted: 0*          |


</details>

{% hint style="info" %}
A legacy table that is no longer filled.
{% endhint %}

| Data point                       | Description                                                                 | Data type        |
| -------------------------------- | --------------------------------------------------------------------------- | ---------------- |
| `company_also_viewed_collection` | Company profiles that were viewed in tandem with the record company profile | Array of objects |
| `viewed_company_url`             | Company profile URL                                                         | String           |
| `viewed_company_id`              | Identification key relating tothe **company**table                        | Integer          |

**Also viewed table data sample:**

{% code title="Also viewed table" %}
```json
"company_also_viewed_collection": [
        {
            "id": 448146,
            "company_id": 111371,
            "viewed_company_url": "https://www.professional-network.com/company/fashion-brand",
            "viewed_company_id": null,
            "created": "2016-06-17 20:08:21",
            "last_updated": "2019-11-14 01:07:39",
            "deleted": 1
        }
   ],
```
{% endcode %}

## Financial website info

<details>

<summary>Repeat fields</summary>

| Data point     | Description                                                                                                                                                                       | Data type        | Example values        |
| -------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------- | --------------------- |
| `id`           | Identification key for the record                                                                                                                                                 | number (integer) | *62195*               |
| `company_id`   | Company record ID assigned in the database                                                                                                                                        | number (integer) | *30707*               |
| `created`      | The time and date when we **first** scraped the record                                                                                                                            | string           | *2019-12-07 22:07:18* |
| `last_updated` | The time and date when we **last** scraped the record                                                                                                                             | string           | *2020-09-06 04:51:48* |
| `deleted`      | One of two values - **1 **or **0**<br />`1` - the last time we scraped the company page, *the Page not found *was returned<br />`0` - we successfully scraped the company profile | boolean          | *deleted: 0*          |


</details>

| Data point                                  | Description                               | Data type        |
| ------------------------------------------- | ----------------------------------------- | ---------------- |
| `company_financial_website_info_collection` | Company  profile on the financial website | Array of objects |
| `financial_website_url`                     | Profile URL on the financial website      | String           |

**Financial website info table data sample:**

{% code title="Financial website info" %}
```json
 "company_financial_website_url_info_collection": [
        {
            "id": 258123,
            "company_id": 111371,
            "financial_website_url": "https://www.financial-website.com/organization/luxury-store-brand",
            "created": "2023-02-06 14:06:55",
            "last_updated": "2023-09-09 18:08:29",
            "deleted": 0
        }
    ],
```
{% endcode %}

## Featured employees

<details>

<summary>Repeat fields</summary>

| Data point     | Description                                                                                                                                                                       | Data type        | Example values        |
| -------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------- | --------------------- |
| `id`           | Identification key for the record                                                                                                                                                 | number (integer) | *62195*               |
| `company_id`   | Company record ID assigned in the database                                                                                                                                        | number (integer) | *30707*               |
| `created`      | The time and date when we **first** scraped the record                                                                                                                            | string           | *2019-12-07 22:07:18* |
| `last_updated` | The time and date when we **last** scraped the record                                                                                                                             | string           | *2020-09-06 04:51:48* |
| `deleted`      | One of two values - **1 **or **0**<br />`1` - the last time we scraped the company page, *the Page not found *was returned<br />`0` - we successfully scraped the company profile | boolean          | *deleted: 0*          |


</details>

| Data point                              | Description                  | Data type        |
| --------------------------------------- | ---------------------------- | ---------------- |
| `company_featured_employees_collection` | List of associated employees | Array of objects |
| `url`                                   | Employee profile URL         | String           |

**Featured employees table data sample:**

{% code title="Featured employees table&#x20;" %}
```json
"company_featured_employees_collection": [
        {
            "id": 26392978,
            "company_id": 111371,
            "url": "https://www.professional-network.com/john-doe",
            "created": "2019-11-14 01:07:39",
            "last_updated": "2020-02-22 12:17:32",
            "deleted": 1
        }
  ],
```
{% endcode %}

## Investors

<details>

<summary>Repeat fields</summary>

| Data point     | Description                                                                                                                                                                       | Data type        | Example values        |
| -------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------- | --------------------- |
| `id`           | Identification key for the record                                                                                                                                                 | number (integer) | *62195*               |
| `company_id`   | Company record ID assigned in the database                                                                                                                                        | number (integer) | *30707*               |
| `created`      | The time and date when we **first** scraped the record                                                                                                                            | string           | *2019-12-07 22:07:18* |
| `last_updated` | The time and date when we **last** scraped the record                                                                                                                             | string           | *2020-09-06 04:51:48* |
| `deleted`      | One of two values - **1 **or **0**<br />`1` - the last time we scraped the company page, *the Page not found *was returned<br />`0` - we successfully scraped the company profile | boolean          | *deleted: 0*          |


</details>

| Data point                              | Data point                                                             | Data type        |
| --------------------------------------- | ---------------------------------------------------------------------- | ---------------- |
| `company_featured_investors_collection` | Consists of&#xA;record metadata and*company\_investors\_list*objects | Array of objects |
| `investor_id`                           | Identification key relating to the*company\_investors\_list*table    | Integer          |
| `round_id`                              | Identification key relating to the*company\_funding\_rounds*table    | Integer          |
| `company_investors_list`                | List of company investors                                              | Object           |
| `name`                                  | Investor's name                                                        | String           |
| `hash`                                  | Investor's name processed by the MD5 algorithm                         | String           |
| `financial_website_url`                 | Investor's profile URL on the financial website                        | String           |

**Featured investors table data sample:**

{% code title="Featured investors table" %}
```json
 "company_featured_investors_collection": [
        {
            "id": 812666,
            "company_id": 111371,
            "investor_id": 5311,
            "round_id": 1822807,
            "created": "2021-11-29 16:02:04",
            "last_updated": "2021-12-28 09:06:11",
            "deleted": 1,
            "company_investors_list": {
                "id": 5311,
                "name": "The Investor Company",
                "hash": "7b1fcd743ad2e20a8f72819749131678",
                "financial_website_url": "https://www.financial-website.com/organization/the-investor-company",
                "created": "2020-09-10 00:02:42",
                "last_updated": "2022-02-07 10:32:06"
            }
        }
    ],
```
{% endcode %}

## Funding rounds

<details>

<summary>Repeat fields</summary>

| Data point     | Description                                                                                                                                                                       | Data type        | Example values        |
| -------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------- | --------------------- |
| `id`           | Identification key for the record                                                                                                                                                 | number (integer) | *62195*               |
| `company_id`   | Company record ID assigned in the database                                                                                                                                        | number (integer) | *30707*               |
| `created`      | The time and date when we **first** scraped the record                                                                                                                            | string           | *2019-12-07 22:07:18* |
| `last_updated` | The time and date when we **last** scraped the record                                                                                                                             | string           | *2020-09-06 04:51:48* |
| `deleted`      | One of two values - **1 **or **0**<br />`1` - the last time we scraped the company page, *the Page not found *was returned<br />`0` - we successfully scraped the company profile | boolean          | *deleted: 0*          |


</details>

| Data point                          | Description                                                    | Data type        |
| ----------------------------------- | -------------------------------------------------------------- | ---------------- |
| `company_funding_rounds_collection` | Last funding round details                                     | Array of objects |
| `last_round_investors_count`        | Number of investors who have participated in the funding round | Integer          |
| `total_rounds_count`                | Total number of completed funding rounds                       | Integer          |
| `last_round_type`                   | Last funding round type                                        | String           |
| `last_round_date`                   | Last funding round date                                        | String           |
| `last_round_money_raised`           | Amount of money raised in the last funding round               | String           |
| `financial_website_url`             | Funding round record URL on financial website                  | String           |

**Funding rounds table data sample:**

{% code title="Funding rounds table" %}
```json
"company_funding_rounds_collection": [
        {
            "id": 2,
            "last_round_investors_count": 0,
            "total_rounds_count": 4,
            "last_round_type": "Seed",
            "last_round_date": "2016-06-01 00:00:00",
            "last_round_money_raised": "US$ 224.2K",
            "financial_website_url": "https://www.financial-website.com/funding_round/software-company-seed--92e35c7f",
            "created": "2020-09-07 13:01:57",
            "last_updated": "2020-09-26 16:29:54",
            "deleted": 1
        }
    ],
```
{% endcode %}

## Locations

<details>

<summary>Repeat fields</summary>

| Data point     | Description                                                                                                                                                                       | Data type        | Example values        |
| -------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------- | --------------------- |
| `id`           | Identification key for the record                                                                                                                                                 | number (integer) | *62195*               |
| `company_id`   | Company record ID assigned in the database                                                                                                                                        | number (integer) | *30707*               |
| `created`      | The time and date when we **first** scraped the record                                                                                                                            | string           | *2019-12-07 22:07:18* |
| `last_updated` | The time and date when we **last** scraped the record                                                                                                                             | string           | *2020-09-06 04:51:48* |
| `deleted`      | One of two values - **1 **or **0**<br />`1` - the last time we scraped the company page, *the Page not found *was returned<br />`0` - we successfully scraped the company profile | boolean          | *deleted: 0*          |


</details>

| Data point                     | Description                                                                                                              | Data type        |
| ------------------------------ | ------------------------------------------------------------------------------------------------------------------------ | ---------------- |
| `company_locations_collection` | Company locations                                                                                                        | Array of objects |
| `location_address`             | Company address                                                                                                          | String           |
| `is_primary`                   | Denotes if the location is the company's primary location <br />`0` - not a primary location<br />`1` - primary location | Boolean          |

**Locations table data sample:**

{% code title="Locations table" %}
```json
"company_locations_collection": [
        {
            "id": 11612582,
            "company_id": 111371,
            "location_address": "Los Angeles, California, US",
            "is_primary": 1,
            "created": "2019-11-14 01:07:39",
            "last_updated": "2023-09-09 18:08:29",
            "deleted": 0
        },
        {
            "id": 11612583,
            "company_id": 111371,
            "location_address": "New York, US",
            "is_primary": 0,
            "created": "2019-11-14 01:07:39",
            "last_updated": "2023-09-09 18:08:29",
            "deleted": 0
        }
    ],
```
{% endcode %}

## Similar companies

<details>

<summary>Repeat fields</summary>

| Data point     | Description                                                                                                                                                                       | Data type        | Example values        |
| -------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------- | --------------------- |
| `id`           | Identification key for the record                                                                                                                                                 | number (integer) | *62195*               |
| `company_id`   | Company record ID assigned in the database                                                                                                                                        | number (integer) | *30707*               |
| `created`      | The time and date when we **first** scraped the record                                                                                                                            | string           | *2019-12-07 22:07:18* |
| `last_updated` | The time and date when we **last** scraped the record                                                                                                                             | string           | *2020-09-06 04:51:48* |
| `deleted`      | One of two values - **1 **or **0**<br />`1` - the last time we scraped the company page, *the Page not found *was returned<br />`0` - we successfully scraped the company profile | boolean          | *deleted: 0*          |


</details>

| Data point                   | Description                             | Data type        |
| ---------------------------- | --------------------------------------- | ---------------- |
| `company_similar_collection` | Companies similar to the record company | Array of objects |
| `url`                        | Similar company profile URL             | String           |

**Similar table data sample:**

{% code title="Similar table" %}
```json
 "company_similar_collection": [
        {
            "id": 45310284,
            "company_id": 111371,
            "url": "https://www.professional-network.com/company/luxury-clothing-brand",
            "created": "2019-11-14 01:07:39",
            "last_updated": "2021-06-22 02:08:26",
            "deleted": 0
        }
   ],
```
{% endcode %}

## Specialties

<details>

<summary>Repeat fields</summary>

| Data point     | Description                                                                                                                                                                       | Data type        | Example values        |
| -------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------- | --------------------- |
| `id`           | Identification key for the record                                                                                                                                                 | number (integer) | *62195*               |
| `company_id`   | Company record ID assigned in the database                                                                                                                                        | number (integer) | *30707*               |
| `created`      | The time and date when we **first** scraped the record                                                                                                                            | string           | *2019-12-07 22:07:18* |
| `last_updated` | The time and date when we **last** scraped the record                                                                                                                             | string           | *2020-09-06 04:51:48* |
| `deleted`      | One of two values - **1 **or **0**<br />`1` - the last time we scraped the company page, *the Page not found *was returned<br />`0` - we successfully scraped the company profile | boolean          | *deleted: 0*          |


</details>

| Data point                       | Description                 | Data type        |
| -------------------------------- | --------------------------- | ---------------- |
| `company_specialties_collection` | List of company specialties | Array of objects |
| `specialty`                      | Specialty                   | String           |

**Specialties table data sample:**

{% code title="Specialties table" %}
```json
"company_specialties_collection": [
        {
            "id": 160305,
            "company_id": 111371,
            "specialty": "Luxury store brand stores",
            "created": "2016-06-17 20:08:21",
            "last_updated": "2022-07-25 04:42:17",
            "deleted": 1
        }
    ],
```
{% endcode %}

## Stock info
<details>

<summary>Repeat fields</summary>

| Data point     | Description                                                                                                                                                                       | Data type        | Example values        |
| -------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------- | --------------------- |
| `id`           | Identification key for the record                                                                                                                                                 | number (integer) | *62195*               |
| `company_id`   | Company record ID assigned in the database                                                                                                                                        | number (integer) | *30707*               |
| `created`      | The time and date when we **first** scraped the record                                                                                                                            | string           | *2019-12-07 22:07:18* |
| `last_updated` | The time and date when we **last** scraped the record                                                                                                                             | string           | *2020-09-06 04:51:48* |
| `deleted`      | One of two values - **1 **or **0**<br />`1` - the last time we scraped the company page, *the Page not found *was returned<br />`0` - we successfully scraped the company profile | boolean          | *deleted: 0*          |


</details>

| Data point                      | Filter name     | Data type        |
| ------------------------------- | --------------- | ---------------- |
| `company_stock_info_collection` | Stock details   | Array of objects |
| `ticker`                        | Stock ticker    | String           |
| `exchange`                      | Stock exchange  | String           |

**Stock info table data sample:**

{% code title="Stock info table" %}
```json
"company_stock_info_collection": [
        {
            "id": 2789,
            "company_id": 111371,
            "ticker": "LSB",
            "exchange": "OTCM",
            "created": "2020-05-07 14:38:14",
            "last_updated": "2020-07-19 09:39:38",
            "deleted": 1
        }
    ],
```
{% endcode %}

## Company updates

<details>

<summary>Repeat fields</summary>

| Data point     | Description                                                                                                                                                                       | Data type        | Example values        |
| -------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------- | --------------------- |
| `id`           | Identification key for the record                                                                                                                                                 | number (integer) | *62195*               |
| `company_id`   | Company record ID assigned in the database                                                                                                                                        | number (integer) | *30707*               |
| `created`      | The time and date when we **first** scraped the record                                                                                                                            | string           | *2019-12-07 22:07:18* |
| `last_updated` | The time and date when we **last** scraped the record                                                                                                                             | string           | *2020-09-06 04:51:48* |
| `deleted`      | One of two values - **1 **or **0**<br />`1` - the last time we scraped the company page, *the Page not found *was returned<br />`0` - we successfully scraped the company profile | boolean          | *deleted: 0*          |


</details>

| Data point                      | Description                                                       | Data type        |
| ------------------------------- | ----------------------------------------------------------------- | ---------------- |
| `company_updates_collection`    | Company's posts/updates on professional network                   | Array of objects |
| `urn`                           | String-based identifier                                           | String           |
| `followers`                     | Number of followers                                               | Integer          |
| `date`                          | Publish date&#xA;(e.g., 1 month ago)                              | String           |
| `description`                   | Published text&#xA;**Note:**may contain control characters       | String           |
| `reactions_count`               | Number of reactions on the post                                   | Integer          |
| `comments_count`                | Number of comments on the post                                    | Integer          |
| `reshared_post_author`          | Reshared post author                                              | String           |
| `reshared_post_author_url`      | Profile URL of the reshared post author                           | String           |
| `reshared_post_author_headline` | Headline of the reshared post author                              | String           |
| `reshared_post_description`     | Reshared post text                                                | String           |
| `reshared_post_followers`       | The number of followers of the reshared post author               | Integer          |
| `reshared_post_date`            | Date the reshared post was published&#xA;&#xA;(e.g., 1 month ago) | String           |

**Company updates table data sample:**

{% code title="Company updates table" %}
```json
"company_updates_collection": [
      {
        "id": 193,
        "company_id": 12695930,
        "urn": "urn:li:activity:6991335602751201281",
        "followers": 1371,
        "date": "1mo",
        "description": "We are delighted to share with you our success at the Expo 2022. Prime Minister spent the highest time in the expo at our Virtual Reality Aircraft Simulator, took an entire sortie on the virtual ALH MK III, experienced it to the fullest. \n\nKudos to the entire team of the Tech Company for this remarkable achievement ! Hands down by far the best show we've ever had !",
        "reactions_count": 22,
        "comments_count": 2,
        "reshared_post_author": "John Doe",
        "reshared_post_author_url": "https://www.professional-network.com/john-doe",
        "reshared_post_author_headline": "Co-Founder at Tech Company, VR/AR Training Facilitator, TEDx & Keynote Speaker",
        "reshared_post_description": "We are delighted to share with you our success at the Expo 2022. Prime Minister spent the highest time in the expo at our Virtual Reality Aircraft Simulator, took an entire sortie on the virtual ALH MK III, experienced it to the fullest. \n\nKudos to the entire team of the Tech Company for this remarkable achievement ! Hands down by far the best show we've ever had !",
        "reactions_count": 22,
        "reshared_post_followers": 30,
        "reshared_post_date": "1mo",
        "last_updated": "2023-01-04 10:09:34",
        "deleted": 1
      }
    ],
```
{% endcode %}



