---

copyright:
  years: 2020
lastupdated: "2020-06-29"

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

# Provisioning your resources in VPC
{: #migrate-provision}

After you edit your discovered resources, you can provision that workspace on {{site.data.keyword.cloud}}. You can either provision your entire VPC or select the components that you want to provision, allowing you to migrate the rest at a later time.

1. To select components for provisioning, enable the **Select for Provisioning** option and choose the components that you want to provision and click **Continue**.
2. Click **Provision** to start the provisioning process.

Provisioning can take a significant amount of time depending on the size of your instances and images. There are several processes that run in the background during migration, for example, capturing the images, exporting them to {{site.data.keyword.cos_full_notm}}, converting them to the required VPC format, and then importing them into the VPC infrastructure.

When the provisioning process is complete, you will see a success message.

## Next steps
{: #provision-next-steps}

After your VPC environment is provisioned, see [Validating your resources in VPC](/docs/wanclouds-vpc-plus?topic=wanclouds-vpc-plus-migrate-validate).
