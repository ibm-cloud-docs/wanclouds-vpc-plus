---

copyright:
  years: 2022
lastupdated: "2022-08-11"

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
{:experimental: .experimental}
{:table: .aria-labeledby="caption"}

# Migrating classic IBM Cloud Kubernetes Service or Red Hat OpenShift cluster to VPC
{: #migrate-classic-kubernetes-red-hat-openshift-cluster}

Migrating multiple data centers to a multi-zone region is an experimental feature that is available for evaluation and testing purposes and might change without notice. There are no warranties, SLAs, or support provided, and experimental features are not intended for production use.
{: experimental}

You can migrate your classic {{site.data.keyword.containerlong}} or {{site.data.keyword.redhat_openshift_full}} cluster to VPC by using the VPC+ tool for clusters that are deployed in a single data center. VPC+ discovers both the classic and {{site.data.keyword.containerlong_notm}} or {{site.data.keyword.redhat_openshift_notm}} resources and components. Along with the other resources and workloads running within Kubernetes, see the following list for some of the components and resources that are discovered:

* Worker nodes and pools
* PODs
* Namespaces
* Secrets
* StatefulSets
* DaemonSet
* Deployments
* ConfigMaps
* Custom resource definitions
* PVC

As part of the migration, the VPC+ tool creates a new cluster in a VPC single availability zone, and backs up and restores the Kubernetes workload resources to your new VPC environment.

## Before you begin
{: #before-you-begin}

Before you begin migrating your classic {{site.data.keyword.containerlong_notm}} or {{site.data.keyword.redhat_openshift_notm}} cluster to VPC by using the VPC+ tool, review the following requirements:

1. Be familiar with the [Considerations for {{site.data.keyword.containerlong_notm}} and {{site.data.keyword.redhat_openshift_notm}} migration](/docs/wanclouds-vpc-plus?topic=wanclouds-vpc-plus-migration-considerations#kubernetes-migration).
2. Make sure that the {{site.data.keyword.containerlong_notm}} or {{site.data.keyword.redhat_openshift_notm}} Administrator role is assigned to your user account. 
3. You need both a classic infrastructure API key and {{site.data.keyword.vpc_short}} API key. 
4. HMAC keys (_Access Key ID_ and _Secret Access Key_) are required when you add a VPC account for workload backup and restore. 

### Limitations
{: #limitations}

Review the following limitations:

* Private clusters cannot be migrated.
* Only PVC with block storage is supported.
* For any services that rely on IPs, the IPs must be updated post-migration (for example, DNS, load balancers, security rules, etc.).

## Migrating to VPC
{: #migrate-kubernetes-cluster}

1. Log in to the VPC+ tool.
2. Add your classic and VPC accounts. When you add your VPC account, make sure to provide the _Access Key ID_ and _Secret Access Key_, which are required to migrate your cluster. 
3. Select the **Migrate Infrastructure** option in the {{site.data.keyword.vpc-plus-migration}} interface, and click **Discover**. 
4. Select your {{site.data.keyword.cloud_notm}} classic account, and then click **Create VPC Migration Workspace**.
5. You can now select the resource group, region, and zone where you want to migrate in VPC and the {{site.data.keyword.containerlong_notm}} or {{site.data.keyword.redhat_openshift_notm}} cluster that needs to be migrated. 
6. Review the requirements and considerations for the following components:
    * Address prefix - Classic address prefixes are not supported in VPC. Make sure to create a new address prefix and enable the public gateway.
    * {{site.data.keyword.containerlong_notm}} or {{site.data.keyword.redhat_openshift_notm}} cluster name - The cluster name must be a new and unique.
    * Worker nodes - Classic worker pool flavors are not supported in VPC. 
7. After you select the appropriate resources and components, you can migrate your cluster to VPC. 
8. After you migrate your clusters, verify and validate the clusters. You might need to do some fixes or redeployments on the migrated clusters, especially for {{site.data.keyword.redhat_openshift_notm}} clusters if you are using tooling specific to {{site.data.keyword.redhat_openshift_notm}}, such as internal image registry or operators.


