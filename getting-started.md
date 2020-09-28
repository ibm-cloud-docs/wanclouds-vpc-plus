---

copyright:
  years: 2020
lastupdated: "2020-09-22"

keywords: migration, virtual servers migration, migrating to virtual private cloud

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

# Getting started with VPC+ Cloud Migration
{: #getting-started-tutorial}

Use {{site.data.keyword.vpc-plus-migration}} to migrate your {{site.data.keyword.cloud}} classic infrastructure to {{site.data.keyword.cloud_notm}} Virtual Private Cloud (VPC).
{:shortdesc}

## Step 1. Learn more about {{site.data.keyword.vpc-plus-migration}}
{: #step-1-learn}

Before you begin migrating your classic infrastucture to VPC, learn more about {{site.data.keyword.vpc-plus-migration}} and which classic resources can be migrated. To learn more, see [About {{site.data.keyword.vpc-plus-migration}}](/docs/wanclouds-vpc-plus?topic=wanclouds-vpc-plus-about-wanclouds).

## Step 2. Plan for your migration 
{: #step-2-plan}

To get the best results from your VPC migration, spend time analyzing your classic environment and learning how the {{site.data.keyword.vpc-plus-migration}} tool will handle different components of your environment. For more information, see [Planning for migration](/docs/wanclouds-vpc-plus?topic=wanclouds-vpc-plus-planning-for-migration).

## Step 3. Create an instance of {{site.data.keyword.vpc-plus-migration}} through the {{site.data.keyword.cloud_notm}} catalog
{: #step-3-create}

Complete the following steps to create an instance of {{site.data.keyword.vpc-plus-migration}} through the {{site.data.keyword.cloud_notm}} catalog. 

1. Log in to the [{{site.data.keyword.cloud_notm}} catalog](https://cloud.ibm.com/catalog#services){: external} by using your unique credentials.
2. In the _Category_ section, select **Migration Tools**. 
3. Select the **{{site.data.keyword.vpc-plus-migration}}** tile. 
4. On the **{{site.data.keyword.vpc-plus-migration}}** page in the _Configure your resource_ section, enter a service name for your instance of {{site.data.keyword.vpc-plus-migration}}. 
5. Click **Create**. 

## Step 4. Access the {{site.data.keyword.vpc-plus-migration}} tool
{: #step-4-access}

After you create an instance of {{site.data.keyword.vpc-plus-migration}} through the {{site.data.keyword.cloud_notm}} catalog, you can access the {{site.data.keyword.vpc-plus-migration}} tool. 

1. On the service details page of your {{site.data.keyword.vpc-plus-migration}} instance, select the **Manage** tab. 
2. When you are ready to access the tool, click **Migrate**.
3. Log in to {{site.data.keyword.vpc-plus-migration}} by using your IBMid.

After you log in to the {{site.data.keyword.vpc-plus-migration}} tool, you can access the _User Guide_ and _Tutorial Videos_ that were developed by Wanclouds. These resources are located in the Help menu in the {{site.data.keyword.vpc-plus-migration}} interface.
{: tip}

## Step 5. Add your {{site.data.keyword.cloud_notm}} account to {{site.data.keyword.vpc-plus-migration}}
{: #step-5-add-account}

In order for {{site.data.keyword.vpc-plus-migration}} to access details of your {{site.data.keyword.cloud_notm}} configuration, you must add your {{site.data.keyword.cloud_notm}} accounts information. Complete the following steps to add your {{site.data.keyword.cloud_notm}} accounts.

1. In the {{site.data.keyword.vpc-plus-migration}} interface, click **Get Started**.
2. On the **{{site.data.keyword.cloud_notm}} Classic** tab, provide account information for your {{site.data.keyword.cloud_notm}} classic infrastructure environment. This information is used to discover your current environment.
3. On the **{{site.data.keyword.cloud_notm}} VPC** tab, provide account information for your VPC environment. See [Gathering {{site.data.keyword.cloud_notm}} account information](/docs/wanclouds-vpc-plus?topic=wanclouds-vpc-plus-planning-for-migration#gather-account-information) for information on where to get these values.

## Next steps
{: #cloud-account-next-steps}

After you add your {{site.data.keyword.cloud_notm}} accounts to {{site.data.keyword.vpc-plus-migration}}, you are now ready to discover the resources in your classic infrastructure. See [Discovering your {{site.data.keyword.cloud_notm}} classic infrastructure](/docs/wanclouds-vpc-plus?topic=wanclouds-vpc-plus-migrate-discovery).
