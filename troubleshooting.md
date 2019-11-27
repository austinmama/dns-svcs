---

copyright:
  years: 2019
lastupdated: "2019-11-25"

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
{:generic: data-hd-programlang="generic"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:download: .download}

# Troubleshooting DNS Services
{: #troubleshooting-dns-services}

{{site.data.keyword.cloud}} DNS Services is in Experimental Release. At this time the service is available to whitelisted customers only.
{: important}

Troubleshooting is a systematic approach to solving a problem. The goal of troubleshooting is to determine why something does not work as expected and to find a solution that resolves the problem. In many cases, you can recover from a problem by following a few easy steps.
{:shortdesc}

## Unable to perform name resolution with NXDOMAIN error.
{:#unable-to-perform-name-resolution-with-nxdomain-error}
  * Verify the server you are sending the request from is configured to use one of these DNS resolvers: `161.26.0.7` or `161.26.0.8`.
  * Verify the server you are sending the request from is part of a VPC that has been added as a permitted network to the DNS zone.
  * Verify the FQDN for which name resolution is attempted has a Resource Record in the DNS zone.
  * Verify the DNS request is using the correct Resource Record type in the query.

## Adding permitted network gave an error that VPC does not have Cloud Service Endpoint (CSE) enabled.
{:#adding-permitted-network-cse-not-enabled}
  * By default, only VPCs created on or after 10/09/2019 are enabled to use with Private DNS.
  * For VPCs created as a permitted network before that date, review https://www.ibm.com/support/pages/node/1086243 to contact IBM Support and get the VPC CSE enabled. You are then able to add this VPC for your DNS zone.

## Unable to add permitted network
{:#unable-to-add-permitted-network}
You cannot add duplicate zone and networks combinations. Verify that you are trying to add unique zone and networks combinations.

For example:

- Create zone1.com with network-1
  - Create zone1.com is successful
  - Add network-1 is successful

- Create duplicate zone1.com with network-1
  - Create zone1.com is successful
  - Add network-1 fails
