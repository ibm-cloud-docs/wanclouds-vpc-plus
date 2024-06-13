---

copyright:
  years: 2020
lastupdated: "2020-03-12"

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

# Editing your migration workspace
{: #workspace-edit}

After creating your workspace with either [Migrating with discovery](/docs/wanclouds-vpc-plus?topic=wanclouds-vpc-plus-migrate-discovery) or [Migrating with templates](/docs/wanclouds-vpc-plus?topic=wanclouds-vpc-plus-migrating-using-template), you can make changes to the workspace before you provision .

The following list includes examples of configurations you can edit:
* Subnets
* Public gateways
* Virtual server instances
* VPN gateways
* Load balancers
* Access control lists
* Security groups

## Step 1 - Log in and confirm your {{site.data.keyword.cloud_notm}} information

1. Log in to {{site.data.keyword.wanclouds}}.
2. Select **Manage VPCs** from the navigation menu to open your VPC workspace. By default, the Region field is set to All, showing all values in each category for the regions in your workspace.
3. The default view is tabular. To change to a graphical view of your workspace, click the Tabular/Graphical switch.
4. Select the region in which you need to make changes.
5. Starting with VPC Networks, click through the tabs to verify the current information in your workspace.
6. In each tab, you have editing options. You can create or delete configuration element. In some cases you can edit an existing configuraion element.

## Step 2 - Subnet information
1. Verify your subnet information. You can also change your subnet information.
2. To connect to your classic environment, enable the toggle switch next to **I need to Connect to {{site.data.keyword.cloud_notm}} Classic**. You might need to change your subnetting information to avoid any IP conflicts.
3. Click Next.

## Step 3 - Edit your discovery list
You can remove components from your discovery list that you do not want to migrate.
1. From the list on the right, select any items to exclude from the migration and click the trash icon. You can use the **Bulk Selection** option to select multiple components from the tabular menu on the right or the visual pane on the left.
3. Click Next.

## Step 4 - Edit your VPC workspace
Identify items in the left navigation to add to your workspace and click the Add icon.

Any change you make is reflected in the left pane to visually assist you in the editing of your VPC.

## Editing instances
In your {{site.data.keyword.wanclouds}} workspace, you can edit individual instances.
1. Select the {{site.data.keyword.wanclouds}} workspace.
2. Expand the Instances section.
3. Click the edit icon in the instance you want to edit.
4. Confirm or edit the Name and Zone information and click Next.
3. Select any available configuration components to make changes.

### Instance profile
Virtual server instance profiles in {{site.data.keyword.vpc_short}} are different from the {{site.data.keyword.cloud_notm}} classic infrastructure profiles. {{site.data.keyword.wanclouds}} matches your current instance profiles to the closest matching profiles available in VPC. You can change this default selection from the provided menu and select from the available instance [profiles](/docs/vpc?topic=vpc-profiles) in VPC.

### Images
You can choose to boot your instances using any of the given images or select a custom image present in your COS bucket. Once you have selected the image, you can add new data volumes, network interfaces, and SSH keys for your instance.

### Adding custom images
To import a custom image to {{site.data.keyword.vpc_short}}, you must have the image in your IBM Cloud Object Storage bucket. For more information, see [Importing and managing custom images](/docs/vpc?topic=vpc-managing-images).

1. Load your custom images into IBM Cloud Object Storage.
2. ??Select Custom in the images menu?
3. Select your custom images from the drop-down menu.

### Select boot and secondary volumes
To select your primary and secondary boot volumes, click the icons right next to your instance.

## Specifying subnets for VPN gateways
It is necessary to specify the subnet for each VPN gateway in your VPC since {{site.data.keyword.wanclouds}} cannot do that automatically. You can do so by expanding the VPN Gateways section and clicking the Edit button next to your desired VPN gateway.

## Editing Access Control Lists
We access ACLs from the Virtual Interface (VIF) of your Vyatta 5600 configuration file. You will need to manually edit them here according to your security parameters. To see the details of your firewalls, you can click the Firewalls icon:

You can configure/add your firewalls, rules and add subnets to these Access Control Lists. You can also edit or add rules for your VPC environment.

## Next steps
{: #editing-next-steps}

[Provision your VPC](https://test.cloud.ibm.com/docs/wanclouds-vpc-plus?topic=wanclouds-vpc-plus-edit-resources)

Saving your workspace as a template
