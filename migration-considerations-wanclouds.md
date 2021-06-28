---

copyright:
  years: 2020, 2021
lastupdated: "2021-06-28"

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

# Migration considerations
{: #migration-considerations}

The {{site.data.keyword.vpc-plus-migration}} tool duplicates your environment on {{site.data.keyword.vpc_full}} and does not cancel your {{site.data.keyword.cloud_notm}} classic infrastructure. You can cancel your existing classic environment from the {{site.data.keyword.cloud_notm}} console.

## Considerations for virtual server instances
{: #virtual-server-instances}

Virtual server instances must use one of the following operating systems:
* CentOS 7.x, 8.x
* Debian 9.x, 10.x
* Red Hat 7.x, 8.x
* Ubuntu Linux 16.04.x, 18.04.x
* Windows 2012, 2012R2, 2016

If you have virtual servers that are not using one of the supported operating systems, you need to migrate them to a supported level before migration.

Virtual servers must be cloud-init enabled and have Virtio drivers. For Linux images that do not meet this criteria, see [Creating a Linux custom image](/docs/vpc?topic=vpc-create-linux-custom-image) to prepare the image. For Windows images that do not meet this criteria, see [Creating a Windows custom image](/docs/vpc?topic=vpc-create-windows-custom-image). As an option, you can run a script to validate if your Linux or Windows image meets the minimum OS requirements, is cloud-init enabled, and has Virtio drivers. For more information, see the [script details](https://github.com/IBM-Cloud/vpc-migration-tools/tree/main/os-precheck-scripts){: external}. 
{: important}

Additionally, virtual servers must meet the following requirements:
* No add-ons
* Stock OS image
* Primary volume size doesn't exceed 100 GB
* Supported operating systems

The {{site.data.keyword.vpc-plus-migration}} tool does not log in to your virtual server instances nor does it have access to them. {{site.data.keyword.vpc-plus-migration}}, which is managed by Wanclouds, follows industry best practices to ensure that their application tool is secure and protects your sensitive information.
{: note}

### VMDK image conversion
{: #vmdk-image-conversion}

You can migrate a VMDK-formatted image from classic to VPC by using the VPC+ tool. The VPC+ tool converts the VMDK image to qcow2, which is the supported format in VPC. The image must meet the image requirements listed in the [Considerations for virtual server instances](/docs/wanclouds-vpc-plus?topic=wanclouds-vpc-plus-migration-considerations#virtual-server-instances) section:

* Supported operating system
* Cloud-init enabled
* Virtio drivers
* Single vHDD (no secondary) and does not exceed 100 GB

If you decide to use the VPC+ tool to convert and migrate your VMDK image, you must export the image to {{site.data.keyword.cos_full_notm}} before you begin using the tool. For more information, see [Upload data](/docs/cloud-object-storage?topic=cloud-object-storage-upload).
{: important}

As an alternative, you can convert your VMDK image to qcow2 and upload to {{site.data.keyword.cos_short}} yourself. For more information, see [Migrating VMDK or VHD images to VPC](/docs/cloud-infrastructure?topic=cloud-infrastructure-migrating-images-vpc).

### Dedicated hosts
{: #dedicated-hosts}

When migrating a classic virtual server instance from a dedicated host to {{site.data.keyword.vpc_short}}, you have the option to continue to migrate it as a single-tenant model (dedicated host) or change to a shared-tenant model (public). The default is a single-tenant model, and the VPC+ tool will try to match to the closest classic profile that VPC offers for both the dedicated host and virtual server instance. You have the option to change the profile for either the dedicated host or virtual server instance.

When you decide on classic virtual server placement, you can choose either manual (dedicated host) or auto-assign. Whereas in {{site.data.keyword.vpc_short}}, the implementation is slightly different and placement is either to a dedicated host or dedicated host group. If the placement for the classic virtual server instance is manual, then the VPC+ tools honors the placement and provisions the virtual server in {{site.data.keyword.vpc_short}} as such. For auto-assign, due to the different implementation, the server gets auto-assigned within a dedicated host group. For more information, see [Creating dedicated hosts and groups](/docs/vpc?topic=vpc-creating-dedicated-hosts-instances). Similarly, as with profiles, you have the option to change the virtual server placement and dedicated host group.

### Supported virtual server profiles
{: #profiles}
Not all compute profiles are supported in VPC. For example, quadratic profiles such as C1.2x2, C1.4x4, C1.8x8 are not supported. See [VPC profiles](/docs/vpc?topic=vpc-profiles#compute) for a full list of supported profiles.

If the VPC+ tool encounters a profile during discovery that doesn't match a supported profile, the closest matching profile is selected. You can change the selection when editing the discovered resources.

{{site.data.keyword.vpc-plus-migration}} does not currently support GPU profiles.
{: note}

### Instance groups for auto scaling
{: #auto-scale}

The VPC+ tool discovers virtual server instances that are associated with instance groups. You can migrate these instances with the VPC+ tool, but the tool does not set up auto scale policies in VPC. It's recommended that you migrate only one virtual server instance that is associated with an instance group and then set up auto scale policies with that virtual server instance. For more information, see [Creating an instance group for auto scaling](/docs/vpc?topic=vpc-creating-auto-scale-instance-group).

## Data storage considerations for attached, block, and file storage
{: #storage}

The VPC+ tool can discover the three types of storage used by virtual server instances in {{site.data.keyword.cloud_notm}} classic infrastructure:

1. Portable storage
2. Network file storage
3. Network-attached block storage (iSCSI) with file systems 

With VPC+ tool, you have the option to choose which data volumes to migrate. Only the volumes that you select will be migrated. 

If you have a virtual server instance that has already been migrated where you want to migrate secondary data volumes, use the _Content Data Migrator_ in the VPC+ tool.

As an alternative to the _Content Data Migrator_, you can migrate the data on the block or file volumes to VPC by yourself by using `rsync` or other tools of your choice (`scp` or other third-party tools). For more information on using `rsync` to migrate your data, see [Migrating data from {{site.data.keyword.cloud_notm}} classic infrastructure to VPC](/docs/cloud-infrastructure?topic=cloud-infrastructure-data-migration-classic-to-vpc).
{: note}

### Prerequisites for storage migration
{: #prerequisites-storage-migration}

To migrate block and NAS storages to VPC along with the virtual server instance, make sure to review and complete the following prerequisites:

1. Your {{site.data.keyword.cloud_notm}} account should have administrator privileges for both classic and VPC. Storage volumes are created for the account provided within the VPC.
2. You need to download the script that is provided by the VPC+ tool and run it on your classic virtual server instance with the required privileges. Instructions are provided in the script. The script installs the content migration agent that collects the necessary metadata that is needed for migration. The content migration agent collects information on attached storage, for example, name, partition information for block devices, mount points, file system types. The agent uploads the metadata to the VPC+ controller, providing an option later in the tool to select the wanted volumes for migration. For this to happen, your virtual server needs external connectivity to upload metadata files to the VPC+ controller.
3. In the {{site.data.keyword.cloud_notm}} console, navigate to **Menu icon ![Menu icon](../icons/icon_hamburger.svg) > Classic Infrastructure > Devices > your virtual server instance**. Select the _Storage_ tab, and authorize your block and file storage if not listed there.

### Limitations
{: #storage- migration-limitations}

Review the following storage migration limitations: 

* All migrations are limited to a volume size of 2 TB only.
* You can choose only four volumes while provisioning a virtual server instance. Only four attached volumes, in addition to your boot volume, can be migrated. If you have more than four volumes in your classic instance, see [Volume attachment limits](/docs/vpc?topic=vpc-attaching-block-storage#vol-attach-limits) for details and use the _Content Data Migrator_ in the VPC+ tool to migrate the additional volumes.
* Up to four primary partitions or three primary with two logical on the fourth partition can be migrated.
* Migration of block volumes and partitions without file systems is not yet supported.
* A maximum of 10 IOPS/Gb mapping will be done on virtual server instances for VPC.
* Migration of storage attached to Windows is not yet supported.

All three storage types can be migrated if your use case satisfies these limitations.
{: note}

### Storage migration use cases
{: #storage-migration-use-cases}

Consider the following uses cases for storage migration: 

1. Classic virtual server instance has portable storage that is attached with Linux file systems. This is migrated as-is to VPC.
2. Classic virtual server instance has network file storage:
  * An equivalent Linux file system (ext4) is created in VPC and then the contents are copied over.
  * VPC does not yet support NAS storage. Your storage will be on the Linux file system on your VPC instance, and it cannot be shared.
3. Classic virtual server has network block storage (iSCSI devices):
  * The content migration agent will discover the existence of a Linux file system on top of dev mapper devices and will migrate the contents to VPC.
  * Partition information between source and destination will be retained. 
  * File systems on top of the iSCSI luns are copied to the destination instance. Neither multi-pathing nor user-friendly names configured on your source will be available.
  in your destination.
4. Classic virtual instance has portable storage, network file storage, and network block storage. 
## Considerations for SSH keys
{: #ssh-keys}

The VPC+ tool can detect the SSH public keys that were added during the initial ordering process of your classic virtual server instances. If the SSH public keys aren't RSA or were added after you ordered your instances, then the VPC+ tool will require you to add a new SSH key.

## Considerations for secondary volumes
{: #secondary-volumes}

If you want to migrate a virtual server instance with a primary volume and there is a secondary volume that is attached to it, make sure that when you mount your disks in your classic machine it is mounted permanently. Accomplish this by adding the `nofail` in the secondary volume mount entry of the _/etc/fstab_ file.

A typical entry looks like the following:

```
"/dev/disk     /mnt/disk      ext4        defaults,nofail      0       2”
```

You need to add `nofail` next to defaults if it isn’t there already.

{{site.data.keyword.vpc-plus-migration}} only supports a maximum of three secondary volumes for migration.
{: note}

If a server cannot be migrated because it's not configured as cloud-init, you can still migrate the secondary volume of that server. First, create a compatible server in VPC, then migrate the secondary volume by using the previous procedure.

## Considerations for load balancers
{: #load-balancers}

Only {{site.data.keyword.cloud_notm}} {{site.data.keyword.loadbalancer_short}} is supported.

If your {{site.data.keyword.cloud_notm}} classic environment uses configurations in {{site.data.keyword.cloud_notm}} {{site.data.keyword.loadbalancer_short}} that are not available in VPC, {{site.data.keyword.vpc-plus-migration}} sets the closest match to what is available for VPC or uses a default configuration.

## Considerations for gateway appliance
{: #gateway-appliance}

Only VRA (Vyatta 5600) is supported. Within VRA, the following features are supported:
* Gateway (NAT masquerade)
* VPN/IKE
* Stateless ACLs

### ACLs
{: #ACLs}
The VPC+ tool does not translate network or host-based ACL rules. You will need to add these rules when editing your discovered resources or after you provision your VPC environment.

For port-based ACLs that are configured with RFC1918 a network address, the port ACLs are migrated but the address will change to `Any`. For example, the following VRA configuration:

`Allow UDP, Source Address 10.1.1.0/26, Destination Address 172.16.20.0/26 Port 80`

Migrates to VPC as:

`Allow UDP Source Address Any, Destination Address Any, Port 80`

If you have host-based rules /32, consider moving to security groups to preserve ACLs resource usage.

### VRA rule limitations
{: #VRA-rule-limitations}
{{site.data.keyword.cloud_notm}} limits VRA rules to 25. If you have more than 25 rules, {{site.data.keyword.cloud_notm}} selects the first 25. You can manage these rules when editing your discovered resources.

## Gateway configurations not available in VPC
{: #gateway-configurations-not-available-in-vpc}
If your {{site.data.keyword.cloud_notm}} classic environment uses configurations in a gateway that are not available in VPC, {{site.data.keyword.vpc-plus-migration}} sets the closest match to what is available for VPC or uses a default configuration.
