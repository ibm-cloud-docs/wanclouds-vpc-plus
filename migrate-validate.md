---

copyright:
  years: 2020
lastupdated: "2020-08-31"

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

# Validating your resources in VPC
{: #migrate-validate}

After you provision your VPC environment, and before you make your VPC live, you will want to validate the components to ensure they are ready for production. You will perform this validation in [{{site.data.keyword.cloud}} console](https://cloud.ibm.com/vpc-ext/vpcLayout){: external}.

Use the following information as a guideline for validating components. These lists are a starting point. There might be other configurations that you need to validate.

**Network**
- Validate the number of subnets and the addressing scheme
- Validate that the subnet gateways are configured for the correct subnets
- Validate your firewall rules
- Validate your security groups
- Validate your load balancers. Are the parameters and server pools configured correctly?
- Validate your VPN. Are the parameters are set correctly? Work with your network administrator to ensure that your VPN gateway is configured correctly for peering to be established.

**Compute**
- Are security groups applied correctly?
- Were the SSH keys moved or created correctly?
- Are virtual servers created and placed in the right subnet?
- Are virtual servers accessible and have access to the correct resources?
- Are virtual servers properly denied access to resources that they should not have access to?
- Can you validate the primary and secondary volumes on virtual servers?

**Operating systems**

Validate operating system configurations.
* IP addresses
* Route tables
* IP filters
* User access

**Applications**

* Application configuration files

## Next steps
{: #validate-next-steps}

1. As a security best practice, when you are finished using {{site.data.keyword.vpc-plus-migration}}, delete the username and API key that you created specifically for VPC+. For more information, see [Deleting an API key](/docs/account?topic=account-userapikey#delete_user_key) and [Removing users from an account](/docs/account?topic=account-remove).

2. You need a plan for making VPC live. This includes tasks such as:
  * Updating your DNS server
  * If your data syncs between classic and VPC, you will need to resync after provision.
  * {{site.data.keyword.vpc-plus-migration}} does not shut down or delete any of the resources that were been migrated to VPC. So, you will have two active environments. You will need to close the resources in your classic environment.
  * Moving any traffic that is currently active in classic to VPC.
  * If your instance has a public interface, you need to manually attach a floating IP in VPC. The VPC+ tool does not do this for you.
