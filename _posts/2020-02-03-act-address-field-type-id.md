---
layout: post
title: Act! Address Field Type ID Values
permalink: /2020-02-03-act-address-field-type-id
published: true
---
Doing a data extract from an [Act!](https://www.act.com/) database, and the address fields are kept in a MSSQL database table called `TBL_ADDRESS` and the address types are differentiated by the `TBL_ADDRESS.TYPEID` field.<!--more-->

The following table gives the `TYPEID`, what it is in plain English and the table and field.


| **TYPEID**                           | **Plain English**        | **Table.Field**      |
|:-------------------------------------|:-------------------------| ---------------------|
| 31BD07D5-4CB7-4038-9505-D2347AA530A1 | Contact Primary Address  | `TBL_CONTACT.TYPEID` |
| 47E09CBD-4218-411B-8B59-E838B13E2CCF | Contact Home Address     | `TBL_CONTACT.TYPEID` |
| 31BD07D5-4CB7-4038-9505-D2347AA530A1 | Company Primary Address  | `TBL_COMPANY.TYPEID` |
| 99E19E51-0C31-44EE-A9CD-2B55FB401384 | Company Billing Address  | `TBL_COMPANY.TYPEID` |
| ABECED80-4C4F-410E-949D-612C311AF3E6 | Company Shipping Address | `TBL_COMPANY.TYPEID` |

Note that the primary address has the same `TYPEID` for both `TBL_CONTACT.TYPEID` and `TBL_COMPANY.TYPEID`.
