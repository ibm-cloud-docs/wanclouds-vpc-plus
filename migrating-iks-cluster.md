---

copyright:
  years: 2021, 2022
lastupdated: "2022-11-11"

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

# Migrating classic {{site.data.keyword.cloud_notm}} Kubernetes Service or {{site.data.keyword.redhat_openshift_notm}} cluster to VPC
{: #migrate-classic-kubernetes-red-hat-openshift-cluster}

You can migrate your classic {{site.data.keyword.containerlong}} or {{site.data.keyword.redhat_openshift_full}} cluster to VPC by using the {{site.data.keyword.vpc-plus-migration}} tool for clusters that are deployed in a single data center. You can also migrate multiple data centers to a multizone region. {{site.data.keyword.vpc-plus-migration}} discovers both the classic and {{site.data.keyword.containerlong_notm}} or {{site.data.keyword.redhat_openshift_notm}} resources and components. Along with the other resources and workloads running within Kubernetes, see the following list for some of the components and resources that are discovered:

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

As part of the migration, the {{site.data.keyword.vpc-plus-migration}} tool creates a new cluster in a VPC single availability zone, and backs up and restores the Kubernetes workload resources to your new VPC environment.

## Before you begin
{: #before-you-begin}

Before you begin migrating your classic {{site.data.keyword.containerlong_notm}} or {{site.data.keyword.redhat_openshift_notm}} cluster to VPC by using the {{site.data.keyword.vpc-plus-migration}} tool, review the following requirements:

1. Be familiar with the [Considerations for {{site.data.keyword.containerlong_notm}} and {{site.data.keyword.redhat_openshift_notm}} migration](/docs/wanclouds-vpc-plus?topic=wanclouds-vpc-plus-migration-considerations#kubernetes-migration).
2. Make sure that the {{site.data.keyword.containerlong_notm}} or {{site.data.keyword.redhat_openshift_notm}} Administrator role is assigned to your user account. 
3. You need both a classic infrastructure API key and {{site.data.keyword.vpc_short}} API key. 
4. HMAC keys (_Access Key ID_ and _Secret Access Key_) are required when you add a VPC account for workload backup and restore. 

## Limitations
{: #limitations}

Review the following limitations:

* Private clusters cannot be migrated.
* Only PVC with **_BLOCK STORAGE_** is supported for migration.
* For any services that rely on IPs, the IPs must be updated post-migration (for example, DNS, load balancers, security rules, etc.).

## Supported PVCs
{: #supported-pvcs}

Following PVCs storage types are supported for Migration
* Block Storage


## Migrating to VPC
{: #migrate-kubernetes-cluster}

1.  Log in to the {{site.data.keyword.vpc-plus-migration}} tool.
2.  Add your classic and VPC accounts.
3.  Select the Manage VPCs option in the {{site.data.keyword.vpc-plus-migration}} interface, and click {{site.data.keyword.cloud_notm}}.
4.  Select your IBM VPC, and then select any destination Region.
5.  Click on the Kubernates Cluster and then click on Migrate Cluster.
5.  Select the **Migrate Infrastructure** option in the {{site.data.keyword.vpc-plus-migration}} interface, and click **Discover**. 
6.  Select the Classic Cloud account and click on the discover clusers. Once discovery is completed, select the cluster which one you want to migrate. After that choose the option to migrate the cluster in the existing VPC or create a new VPC.
7.  You can now select the resource group where you want to migrate in VPC (Provide VPC name incase of creating new VPC), Cloud Object Storage, Bucket (Where the data will be stored) Cloud Object Storage Creds (An access key with HMAC value as true and manager role is required for migration). 
8.  Review the requirements and considerations for the following components:
     * Address prefix - Classic address prefixes are not supported in VPC. Make sure to create a new address prefix and enable the public gateway.
     * {{site.data.keyword.containerlong_notm}} or {{site.data.keyword.redhat_openshift_notm}} cluster name - The cluster name must be a new and unique.
     * Worker nodes - Classic worker pool flavors are not supported in VPC. Should be updated with available VPC flavour. 
9.  After you select the appropriate resources and components, you can migrate your cluster to VPC. 
10. After you migrate your clusters, verify and validate the clusters. You might need to do some fixes or redeployments on the migrated clusters, especially for {{site.data.keyword.redhat_openshift_notm}} clusters if you are using tooling specific to {{site.data.keyword.redhat_openshift_notm}}, such as internal image registry or operators.

## Data Migration
{: #data-migration}

{{site.data.keyword.vpc-plus-migration}} allows seamless, direct data transfer from your source to target environment—no additional storage medium required.
This applies to both **Virtual Machine (VM) and Bare Metal** environments. The system automatically syncs changes every 10 seconds(default value is 10 sec also can adjust on demand), and during the next data migration, it only transfers the incremental changes—ensuring faster and more efficient data movement.

**To learn more about the process:**
   * Log in to wanclouds {{site.data.keyword.vpc-plus-migration}}.
   * Navigate to Disaster Recovery.
   * Select Virtual Machine.
   * Click on Setup Backup Manager > Data Sync.
   * Follow the on-screen instructions to set up the agent and begin data migration.
