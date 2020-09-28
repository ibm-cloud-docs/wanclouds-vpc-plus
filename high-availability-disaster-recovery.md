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

# High availability and disaster recovery
{: #high-availability-disaster-recovery}

{{site.data.keyword.vpc-plus-migration}} is a third-party service that is managed by Wanclouds. This service is highly available, and it has no backup and restore requirements for disaster recovery.

## High availability
{: #high-availability}

{{site.data.keyword.vpc-plus-migration}} application deployment is based on Kubernetes, which is available both as a single and multi-master. If one master goes down, Kubernetes shifts the control to another master. Furthermore, POD replicas are deployed across different nodes. This service achieves high availability automatically and is apparent to the customer.

## Disaster recovery
{: #disaster-recovery}

For this service, there is no action that you need to take to prepare for an event of a catastrophic failure in a region.  Wanclouds follows best practices for disaster recovery and automatically recovers and restarts after any disaster event.
