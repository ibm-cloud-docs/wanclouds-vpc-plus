---

copyright:
  years: 2020
lastupdated: "2020-09-22"

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

# Planning for migration
{: #planning-for-migration}

To get the best results from your VPC migration, spend time analyzing your classic environment and learning how the VPC+ tool will handle different components of your environment. Use the following information to start planning your migration journey.
{:shortdesc}

## Preparing for differences in classic and VPC environments
{: #review-tasks}

Task | Details
--- | ---
1. Review [quotas and service limits](/docs/wanclouds-vpc-plus?topic=vpc-quotas) | Ensure that your {{site.data.keyword.cloud}} classic infrastructure components that you are migrating are within the VPC quotas and service limits.
2. Review [migration considerations](/docs/wanclouds-vpc-plus?topic=wanclouds-vpc-plus-migration-considerations) | Review information about specific infrastructure components.
3. Review [comparisons between infrastructure environments](/docs/cloud-infrastructure?topic=cloud-infrastructure-compare-infrastructure) | Some components of your classic infrastructure might not exist in VPC such as dedicated virtual servers, available server profiles, and IPv6 addressing.
4. Review [VPC pricing](https://www.ibm.com/cloud/vpc/pricing){: external} | Pricing might vary between {{site.data.keyword.cloud_notm}} classic and VPC infrastructures.
{: caption="Table 1. Review tasks" caption-side="top"}

## Granting permissions and access
{: #grant-permissions-and-access}

Task | Details
--- | ---
1. Permissions for classic and VPC | Contact your account administrator for permissions.
2. Grant access between VPC Image Services and {{site.data.keyword.cos_full_notm}} | Grant this access if you want to migrate your primary boot volume, secondary volumes, and images from classic infrastructure. For more information, see [Granting access between services](/docs/vpc?topic=vpc-object-storage-prereq).
{: caption="Table 2. Permissions and access tasks" caption-side="top"}

## Gathering {{site.data.keyword.cloud_notm}} account information
{: #gather-account-information}

Account information | Details
--- | ---
1. Username | Create a username specifically for {{site.data.keyword.vpc-plus-migration}}. In the {{site.data.keyword.cloud_notm}} console, select **Manage > Access (IAM) > Users.** Select **Users** and then click **Invite user**, supplying the email address name of the user. This allows you to delete the username after your migration is complete. For more information, see [Inviting users to an account](/docs/account?topic=account-iamuserinv).
2. API keys | You need a classic infrastructure API key. You will also need to create an  {{site.data.keyword.cloud_notm}} API key (VPC API key) specifically for {{site.data.keyword.vpc-plus-migration}}. Your {{site.data.keyword.cloud_notm}} API key must have “Reader, Writer” access. You can verify the level of access in {{site.data.keyword.cloud_notm}} console by clicking **Manage > Access (IAM)** and selecting **Authorizations**. For more information, see [Managing classic infrastructure API keys](/docs/account?topic=account-classic_keys) and [Managing user API keys](/docs/account?topic=account-userapikey).
3. {{site.data.keyword.cos_full_notm}} and resource instance ID (service credentials)| Your {{site.data.keyword.cos_short}} bucket is used to store your images and volumes during the migration process and its resource instance ID allows {{site.data.keyword.vpc-plus-migration}} to access your {{site.data.keyword.cos_full_notm}} and import the images that you want to migrate. For more information, see [{{site.data.keyword.cos_full_notm}} getting started tutorial](/docs/cloud-object-storage?topic=cloud-object-storage-getting-started-cloud-object-storage) and [Service credentials](/docs/services/cloud-object-storage/iam?topic=cloud-object-storage-service-credentials).
4. (Optional) VRA (Vyatta 5600) configuration file | If you want to migrate your Access Control Lists, VPN gateways, and public gateways, you need a VRA set command configuration file in `txt` format. JSON format is not supported.
{: caption="Table 3. Required {{site.data.keyword.cloud_notm}} account information" caption-side="top"}

## Establishing connection between classic and VPC
{: #establish-connection-classic-vpc}

In some cases, resources in VPC still might need to access resources back in classic, such as databases or interprocess communication. In these cases, creating a transit gateway provides a bridge between the two environments. The VPC+ tool can help create the transit gateway, or you can create it through the {{site.data.keyword.cloud_notm}}. If you want to learn more, see [About {{site.data.keyword.tg_full_notm}}](/docs/transit-gateway?topic=transit-gateway-about).

Review the [Planning for {{site.data.keyword.tg_full_notm}}](/docs/wanclouds-vpc-plus?topic=transit-gateway-helpful-tips) information if you want to establish a connection between your VPC and classic infrastructure.

For {{site.data.keyword.tg_full_notm}} use cases, check out the following information:
* [Interconnect one or more VPCs in the same MZR and an IBM classic network](/docs/transit-gateway?topic=transit-gateway-about#use-case-3-interconnect-one-or-more-vpcs-in-the-same-mzr-and-an-ibm-classic-network)
* [Interconnect VPCs and an IBM classic network to access all your resources across all MZRs](/docs/transit-gateway?topic=transit-gateway-about#use-case-4-interconnect-vpcs-and-an-ibm-classic-network-to-access-all-your-resources-across-all-mzrs)

## Migration process overview
{: #migration-process-overview}

The following table outlines the end-to-end process of your migration journey by using the {{site.data.keyword.vpc-plus-migration}} tool.

Migration task | Details
--- | ---
1. [Create an instance of {{site.data.keyword.vpc-plus-migration}} through the {{site.data.keyword.cloud_notm}} catalog](/docs/wanclouds-vpc-plus?topic=wanclouds-vpc-plus-getting-started-tutorial#step-3-create) | Create an instance of {{site.data.keyword.vpc-plus-migration}} through the {{site.data.keyword.cloud_notm}} catalog so that you have access to the VPC+ tool.
2. [Access the {{site.data.keyword.vpc-plus-migration}} tool](/docs/wanclouds-vpc-plus?topic=wanclouds-vpc-plus-getting-started-tutorial#step-4-access) | Log in by using your IBMid.
3. [Add your {{site.data.keyword.cloud_notm}} account to {{site.data.keyword.vpc-plus-migration}}](/docs/wanclouds-vpc-plus?topic=wanclouds-vpc-plus-getting-started-tutorial#step-5-add-account) | In order for {{site.data.keyword.vpc-plus-migration}} to access details of your {{site.data.keyword.cloud_notm}} configuration, you must add your {{site.data.keyword.cloud_notm}} accounts information.
4. [Discover your {{site.data.keyword.cloud_notm}} classic infrastructure](/docs/wanclouds-vpc-plus?topic=wanclouds-vpc-plus-migrate-discovery) | After you add your {{site.data.keyword.cloud_notm}} accounts to {{site.data.keyword.vpc-plus-migration}}, the VPC+ tool can discover your classic infrastructure resources that can be migrated.
5. [Edit your discovered resources](/docs/wanclouds-vpc-plus?topic=wanclouds-vpc-plus-edit-resources) | {{site.data.keyword.vpc-plus-migration}} creates a workspace after discovering your environment. In the workspace you can add, delete, or edit any section of your VPC.
6. [Provision your resources in VPC](/docs/wanclouds-vpc-plus?topic=wanclouds-vpc-plus-migrate-provision) | You can either provision your entire VPC or select the components that you want to provision, allowing you to migrate the rest at a later time.
7. [Validate your resources in VPC](/docs/wanclouds-vpc-plus?topic=wanclouds-vpc-plus-migrate-validate) | After you provision your VPC environment, and before you make your VPC live, you will want to validate your VPC environment to ensure it is ready for production.
8. (Optional) Create a transit gateway | If you want to establish a connection between your VPC and classic infrastructure, you can create a transit gateway. Refer to [Establishing connection between classic and VPC](/docs/wanclouds-vpc-plus?topic=wanclouds-vpc-plus-planning-for-migration#establish-connection-classic-vpc).
{: caption="Table 4. Migration process overview" caption-side="top"}

## Next steps
{: #planning-next-steps}

Refer to [Getting started with {{site.data.keyword.vpc-plus-migration}}](/docs/wanclouds-vpc-plus?topic=wanclouds-vpc-plus-getting-started-tutorial) to start your migration journey.
