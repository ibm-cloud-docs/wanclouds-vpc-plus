---

copyright:
  years: 2020
lastupdated: "2020-09-03"

keywords: 

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

# Migrating a virtual server instance to an existing VPC
{: #migrate-vsi-existing-vpc}

With {{site.data.keyword.vpc-plus-migration}}, you have the option to migrate a virtual server instance to an existing VPC that you've created either through the {{site.data.keyword.cloud}} console or {{site.data.keyword.vpc-plus-migration}}. 

Before you begin migrating a virtual server instance to an existing VPC, review the following requirements and considerations:

* You need an existing VPC environment.
* Your destination VPC needs to have available limits to accommodate the new virtual server instance (for example, IP address, security group network interface membership, etc.).
* Review the migration considerations for [virtual server instances](/docs/wanclouds-vpc-plus?topic=wanclouds-vpc-plus-migration-considerations#virtual-server-instances).

To start the process, select the **Manage VPCs** option in the {{site.data.keyword.vpc-plus-migration}} navigation menu, then select **Virtual Server Instances > Create Virtual Server Instance**. 
