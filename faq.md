---

copyright:
  years: 2020
lastupdated: "2020-06-29"

keywords: faqs, Frequently Asked Questions, question, Wanclouds VPC+

subcollection: wanclouds-vpc-plus

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:external: target="_blank" .external}
{:pre: .pre}
{:tip: .tip}
{:important: .important}
{:table: .aria-labeledby="caption"}
{:faq: data-hd-content-type='faq'}


# FAQs for VPC+ Cloud Migration
{: #wanclouds-vpc-plus-faqs}

FAQs for {{site.data.keyword.vpc-plus-migration}} includes questions about {{site.data.keyword.cloud}} migration. To find all FAQs for {{site.data.keyword.cloud_notm}}, see our [FAQ library](/docs/faqs).
{: shortdesc}


## Will there be any business disruption during the migration process?
{: #my-faq-disruption}
{: faq}
Because your virtual server instances are restarted when {{site.data.keyword.vpc-plus-migration}} takes a snapshot of your image, you might have a business disruption if you do not plan for it. You should have a dedicated migration window set to complete your migration.

## What precautions should I take during the migration process?
{: #my-faq-precautions}
{: faq}
Do not delete any resources from your {{site.data.keyword.cloud_notm}} environment during the migration process, such as {{site.data.keyword.cos_full_notm}} and image templates.

## Will migrating IBM Cloud classic environment to IBM Cloud VPC incur more charges?
{: #my-faq-costs}
{: faq}
Pricing might change depending upon your environment, and you are billed according to the {{site.data.keyword.vpc_short}} pricing plan. Also, your VPC environment is charged separately from your classic environment. Migration will not automatically de-provision your existing environment. If you do not want to maintain both accounts, you can de-provision it from {{site.data.keyword.cloud_notm}}.

## Can I access my current IBM Cloud classic environment if I migrate to VPC?
{: #my-faq-access-classic}
{: faq}
Yes, you can establish a link to your existing {{site.data.keyword.cloud_notm}} classic infrastructure when you migrate to VPC. The migration will not disrupt anything from your existing environment.

## Why is my migration process taking so long?
{: #my-faq-migration-taking-too-long}
{: faq}
Migration can take a significant amount of time depending on the number of instances you are migrating, the size of your images, network performance, and the source location (data center) and the destination region (MZR). Wait until the process is complete and keep the {{site.data.keyword.vpc-plus-migration}} tab open. When the migration process is complete, you will see a success message.
