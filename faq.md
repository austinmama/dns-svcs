---

copyright:
  years: 2019
lastupdated: "2019-11-08"

keywords: dns-svcs, DNS Services, Private DNS

subcollection: dns-svcs

---


{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:external: target="_blank" .external}
{:DomainName: data-hd-keyref="DomainName"}
{:note: .note}
{:tip: .tip}
{:important: .important}
{:deprecated: .deprecated}
{:faq: data-hd-content-type='faq'}
{:generic: data-hd-programlang="generic"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:download: .download}

# FAQs
{: #frequently-asked-questions}

{{site.data.keyword.cloud}} DNS Services is in Experimental Release. At this time the service is available to whitelisted customers only.
{: important}

The following section answers some frequently asked questions (FAQs) about DNS Services.
{:shortdesc}

## How is private DNS different from public DNS?
{: faq}

Private DNS permits name resolution only from Permitted VPCs within your {{site.data.keyword.cloud}} account. The DNS zone is not resolvable on the Internet.

## Can I manage publicly available DNS records with this service?
{: faq}

No, DNS Services only offers private DNS at the moment. Use {{site.data.keyword.cis_full_notm}} for public DNS. [{{site.data.keyword.cis_short_notm}} documentation](/docs/infrastructure/cis?topic=cis-getting-started#getting-started)

## Is DNSSec supported with zones managed by DNS Services?
{: faq}

DNSSec allows resolvers to cryptographically verify the data received from authoritative servers. DNS services resolvers support DNSSec for public domains, for which requests are forwarded to public resolvers that support DNSSec. For private zones, since the authority is within {{site.data.keyword.cloud_notm}}, records are fetched using secure protocols, and are guaranteed to have the same level of privacy and security that DNSSec provides for public zones.

## Is DNS services regional or global?
{: faq}

DNS services is a global service and can be used from permitted networks in any {{site.data.keyword.cloud_notm}} region.

## How do I update my Virtual Server Instance to use Private DNS for Name resolution?
{: faq}

This is operating system specific. For example, on some Linux distributions the `/etc/resolv.conf` file contains the IP address of the DNS resolver. This file should be updated with the IP address of the Private DNS Name Servers, `161.26.0.7` and `161.26.0.8`. The configuration can also be updated through Cloud Init, where supported. Consult your operating system manuals for instructions on how to update DNS resolvers. See [Detailed steps](/docs/dns-svcs?topic=dns-svcs-updating-dns-resolver) to learn how to update configuration to use Private DNS Resolvers, for different distros.

## When creating a DNS zone, what is the purpose of the 'Label' field?
{: faq}

A given instance can have multiple DNS zones with the same name. The label helps to differentiate zones with name collisions.

## How many private zones are supported?
{: faq}

10 per service instance

## How many permitted networks are supported?
{: faq}

10 per DNS zone

## How many DNS records are supported?
{: faq}

3500 per DNS zone

## How do I delete my DNS Services instance?
{: faq}

- Navigate to the Resource List in the [{{site.data.keyword.cloud_notm}} console](https://{DomainName}/){: new_window}.
- Click the "overflow" menu ![overflow menu icon](/icons/actions-icon-vertical.svg "overflow menu icon") in the final column and select "Delete".

## Why can't I delete a DNS Services instance?
{: faq}

If a DNS zone has been added to the DNS Services instance, the instance cannot be deleted.

## Why can't I delete a DNS zone?
{: faq}

If a network has been added to a zone, the zone cannot be deleted until the permitted network is deleted from the zone.

## What happens if I delete my VPC?
{: faq}

If the VPC is deleted, the corresponding Permitted Network will also be deleted from the DNS zones of your instance.


## What do the different zone states mean?
{: faq}
### Pending_Network_Add or Pending (UI)
When a DNS zone is added to the instance it will be in PENDING_NETWORK_ADD. In this state Resource Records can be added, deleted or updated. Since the zone does not have any permitted networks, the zone will not be served by the resolvers in any region.

### Active
When a Domain has one or more permitted networks added then the domain state changes to ACTIVE and the domain will be served by the resolver from all the regions.

### Disabled
In this state the zone will not be served and all control path operations will be disabled except deleting the zone.


## Can I use any arbitrary name for the zone?
{: faq}

In general, yes. Certain IBM owned or IBM specific DNS Zone names are restricted, in other words, they can't be created in Private DNS. This includes `ibm.com`, `bluemix.net`, `softlayer.com`, `appdomain.cloud` and a few others. The zone names must be 2-level deep (for example, `example.com`). Once the zone has been added, hostnames within the zone can be multiple levels deep, per your needs (for example, you will be able to add records for `hostname.example.com`, or `hostname.subdomain.example.com`, etc.).

## Can I create two DNS zones with the same name?
{: faq}

Creating two DNS Zones with the same name is allowed. Use label and description to differentiate between the two.

## Can I add the same permitted network (for example, a VPC) to two DNS Zones of the same name?
{: faq}

Adding the same VPC to two DNS Zones of the same name is not allowed.


## What are the authoritative servers for the private DNS zones? Can I resolve the private DNS zones iteratively?
{: faq}

Unlike public DNS zones, the DNS service does not expose authoritative servers for private DNS zones. Clients must send their recursive DNS queries to the DNS resolvers that the service provides. The service does not allow iterative resolution of private DNS zones.
