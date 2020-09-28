---

copyright:
  years: 2020
lastupdated: "2020-08-31"

keywords:

subcollection: wanclouds-vpc-plus

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:external: target="_blank" .external}
{:pre: .pre}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:table: .aria-labeledby="caption"}

# Discovering your {{site.data.keyword.cloud_notm}} classic infrastructure
{: #migrate-discovery}

The discovery tool in {{site.data.keyword.vpc-plus-migration}} uses account credentials that you provide and searches your existing {{site.data.keyword.cloud_notm}} classic infrastructure to determine what components you have and how they are configured. This includes components such as:
* Address prefixes
* Subnets
* Virtual server instances
* Load balancers
* Security groups
* SSH keys

Optionally, you can also specify a VRA (Vyatta 5600) configuration file to discover additional information, such as:

* Access control lists
* VPN gateways
* Public gateways

To start the discovery process, select the **Migrate Infrastructure** option in the {{site.data.keyword.vpc-plus-migration}} interface.

## Next steps
{: #discover-next-steps}

Refer to [Editing your discovered resources](/docs/wanclouds-vpc-plus?topic=wanclouds-vpc-plus-edit-resources).
