---

copyright:
  years: 2022

lastupdated: "2022-11-11"

keywords: 

subcollection: wanclouds-vpc-plus

content-type: release-note

---

{{site.data.keyword.attribute-definition-list}}
{:external: target="_blank" .external}
{:release-note: data-hd-content-type='release-note'}

# Release notes for VPC+ Cloud Migration
{: #release-notes}

Use these release notes to learn about the latest updates to {{site.data.keyword.vpc-plus-migration}} that are grouped by date.
{: shortdesc}

## November 2022
{: #vpc-plus-migration-nov22}
{: release-note}

Multizone region (MZR) - {{site.data.keyword.containerfull_notm}} and {{site.data.keyword.redhat_openshift_notm}} migration (GA)
:   The ability to discover and migrate your {{site.data.keyword.containerfull_notm}} or {{site.data.keyword.redhat_openshift_notm}} clusters from multiple data centers to a multizone region (MZR) in VPC is now generally available.

## September 2022
{: #vpc-plus-migration-sept22}
{: release-note}

Placement groups
:   You can now migrate placement groups with attached virtual server instances to {{site.data.keyword.vpc_short}} by using the VPC+ tool.

Single availability zone (SAZ) - {{site.data.keyword.containerfull_notm}} and {{site.data.keyword.redhat_openshift_notm}} migration (GA)
:   The ability to migrate your {{site.data.keyword.containerfull_notm}} and {{site.data.keyword.redhat_openshift_notm}} clusters from a single data center to a single availability zone in VPC is now generally available. For more information, see [Migrating classic {{site.data.keyword.containerfull_notm}} or {{site.data.keyword.redhat_openshift_notm}} to VPC](/docs/wanclouds-vpc-plus?topic=wanclouds-vpc-plus-migrate-classic-kubernetes-red-hat-openshift-cluster).

Support for multiple {{site.data.keyword.containerfull_notm}} or {{site.data.keyword.redhat_openshift_notm}} cluster migrations
:   You can now migrate multiple {{site.data.keyword.containerfull_notm}} or {{site.data.keyword.redhat_openshift_notm}} clusters at the same time with the VPC+ tool.

## June 2022
{: #vpc-plus-migration-jun22}
{: release-note}

Multizone region (MZR) - {{site.data.keyword.containerfull_notm}} and {{site.data.keyword.redhat_openshift_notm}} migration (Experimental)
:   Experimental users can now discover and migrate their {{site.data.keyword.containerfull_notm}} or {{site.data.keyword.redhat_openshift_notm}} clusters from multiple data centers to a multizone region (MZR) in VPC. This is an experimental feature that is available for evaluation and testing purposes and might change without notice. There are no warranties, SLAs, or support provided, and experimental features are not intended for production use. For more information, see [Considerations for {{site.data.keyword.containerfull_notm}} and {{site.data.keyword.redhat_openshift_notm}} migration](/docs/wanclouds-vpc-plus?topic=wanclouds-vpc-plus-migration-considerations#kubernetes-migration).

## December 2021
{: #vpc-plus-migration-dec21}
{: release-note}

Single availability zone (SAZ) - {{site.data.keyword.containerfull_notm}} and {{site.data.keyword.redhat_openshift_notm}} migration (Experimental)
:   Experimental users can now discover and migrate their {{site.data.keyword.containerfull_notm}} or {{site.data.keyword.redhat_openshift_notm}} clusters in single data center to a single availability zone (SAZ) in VPC. This is an experimental feature that is available for evaluation and testing purposes and might change without notice. There are no warranties, SLAs, or support provided, and experimental features are not intended for production use. For more information, see [Considerations for {{site.data.keyword.containerfull_notm}} and {{site.data.keyword.redhat_openshift_notm}} migration](/docs/wanclouds-vpc-plus?topic=wanclouds-vpc-plus-migration-considerations#kubernetes-migration).

## June 2021
{: #vpc-plus-migration-jun21}
{: release-note}

Dedicated hosts
:   When you migrate a classic virtual server instance from a dedicated host to {{site.data.keyword.vpc_short}}, you now have the option to continue to migrate it as a single-tenant model (dedicated host) or change it to a shared-tenant model (public). For more information, see [Dedicated hosts](/docs/wanclouds-vpc-plus?topic=wanclouds-vpc-plus-migration-considerations#dedicated-hosts).

Data migration for block and file storage
:   You can now migrate classic block and file storage to {{site.data.keyword.vpc_short}} with the VPC+ tool. For more information, see [Data storage considerations for attached, block, and file storage](/docs/wanclouds-vpc-plus?topic=wanclouds-vpc-plus-migration-considerations#storage).

## March 2021
{: #vpc-plus-migration-mar21}
{: release-note}

VMDK image conversion
:   You can now migrate a VMDK-formatted image from {{site.data.keyword.cloud_notm}} classic infrastructure to {{site.data.keyword.vpc_short}} by using the VPC+ tool. For more information, see [VMDK image conversion](docs/wanclouds-vpc-plus?topic=wanclouds-vpc-plus-migration-considerations#vmdk-image-conversion).

## December 2020
{: #vpc-plus-migration-dec20}
{: release-note}

Instance groups for auto scaling
:   You can now discover virtual server instances that are associated with instance groups. For more information, see [Instance groups for auto scaling](/docs/wanclouds-vpc-plus?topic=wanclouds-vpc-plus-migration-considerations#auto-scale).

Secondary attached storage
:   Support is now available to migrate secondary attached storage for virtual server instances. For more information, see [Data storage considerations for attached, block, and file storage](/docs/wanclouds-vpc-plus?topic=wanclouds-vpc-plus-migration-considerations#storage).

Bug fix
:   Fixes were applied related to the issue with RHEL 7.x 25 G boot image instances.

## September 2020
{: #vpc-plus-migration-sept20}
{: release-note}

Manage existing VPC 
:   You can now create or delete resources in an existing VPC from the VPC+ tool. For more information, see [Migrating a virtual server instance to an existing VPC](/docs/wanclouds-vpc-plus?topic=wanclouds-vpc-plus-migrate-vsi-existing-vpc).

Create instance from image template or qcow2 image 
:   You can create a virtual server instance from an image template or qcow2 image that is stored in {{site.data.keyword.cos_full_notm}} from the VPC+ tool.

{{site.data.keyword.tg_full_notm}}
:   With the VPC+ tool, you can now create a transit gateway between your classic and VPC environments. For more information, see [Establishing connection between classic and VPC](/docs/wanclouds-vpc-plus?topic=wanclouds-vpc-plus-planning-for-migration#establish-connection-classic-vpc).

SSO with existing {{site.data.keyword.cloud_notm}} account
:   You can now sign in to the VPC+ tool with your existing {{site.data.keyword.cloud_notm}} account credentials.

## June 2020
{: #vpc-plus-migration-jun20}
{: release-note}

Introducing {{site.data.keyword.vpc-plus-migration}}
:   You can now use {{site.data.keyword.vpc-plus-migration}} to migrate your {{site.data.keyword.cloud_notm}} classic infrastructure to {{site.data.keyword.cloud_notm}} Virtual Private Cloud (VPC). For more information, see [About {{site.data.keyword.vpc-plus-migration}}](/docs/wanclouds-vpc-plus?topic=wanclouds-vpc-plus-about-wanclouds).

