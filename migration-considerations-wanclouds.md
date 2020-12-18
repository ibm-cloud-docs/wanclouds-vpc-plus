---

copyright:
  years: 2020
lastupdated: "2020-12-15"

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
* CentOS 7.x
* Debian 9.x
* Red Hat 7.x
* Ubuntu Linux 18.04 Bionic Beaver
* Ubuntu Linux 16.04 Xenial Xerus
* Windows 2012, 2012R2, 2016

If you have virtual servers that are not using one of the supported operating systems, you need to migrate them to a supported level before migration.

Virtual servers must be cloud-init enabled and have Virtio drivers. For Linux images that do not meet this criteria, see [Creating a Linux custom image](/docs/vpc?topic=vpc-create-linux-custom-image) to prepare the image. For Windows images that do not meet this criteria, see [Creating a Windows custom image](/docs/vpc?topic=vpc-create-windows-custom-image). As an option, you can run a script to validate if your Linux or Windows image meets the minimum OS requirements, is cloud-init enabled, and has Virtio drivers. For script details, visit https://github.com/IBM/vpc-migration. 
{: important}

Additionally, virtual servers must meet the following requirements:
* No add-ons
* Stock OS image
* Primary volume size doesn't exceed 100 GB
* Supported operating systems

The {{site.data.keyword.vpc-plus-migration}} tool does not log in to your virtual server instances nor does it have access to them. {{site.data.keyword.vpc-plus-migration}}, which is managed by Wanclouds, follows industry best practices to ensure that their application tool is secure and protects your sensitive information.
{: note}

### Dedicated virtual servers
{: #dedicated-virtual-servers}

Virtual servers in VPC are all IBM-managed, multi-tenant virtual server deployments, similar to public virtual servers in classic. In VPC, there is not an equivalent to dedicated virtual servers. During migration, all dedicated virtual servers in your classic environment are migrated, but do not have the characteristics of a dedicated virtual server.

### Supported virtual server profiles
{: #profiles}
Not all compute profiles are supported in VPC. For example, quadratic profiles such as C1.2x2, C1.4x4, C1.8x8 are not supported. See [VPC profiles](/docs/vpc?topic=vpc-profiles#compute) for a full list of supported profiles.

If the VPC+ tool encounters a profile during discovery that doesn't match a supported profile, the closest matching profile is selected. You can change the selection when editing the discovered resources.

{{site.data.keyword.vpc-plus-migration}} does not currently support GPU profiles.
{: note}

### Instance groups for auto scaling
{: #auto-scale}

The VPC+ tool discovers virtual server instances that are associated with instance groups. You can migrate these instances with the VPC+ tool, but the tool does not set up auto scale policies in VPC. It's recommended that you migrate only one virtual server instance that is associated with an instance group and then set up auto scale policies with that virtual server instance. For more information, see [Creating an instance group for auto scaling](/docs/vpc?topic=vpc-creating-auto-scale-instance-group).

## Considerations for attached, block, and file storage
{: #storage}

The VPC+ tool can discover the three types of storage used by virtual server instances: attached, block, and file storage; however, the VPC+ tool can only migrate attached storage as part of the virtual server migration. 

If the virtual server instance that you want to migrate has block and file storage volumes, then the data on the block or file volumes needs to be migrated to VPC by your tool of choice (scp, rsync, or other third-party tools).

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
