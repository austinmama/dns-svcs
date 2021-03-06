---

copyright:
  years: 2020
lastupdated: "2020-06-02"

keywords: IBM Cloud DNS Services, DNS Activity Tracker events

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


# Auditing events for {{site.data.keyword.dns_short}}
{: #at_events}

As a security officer, auditor, or manager, you can use the Activity Tracker service to track how users and applications interact with the {{site.data.keyword.dns_full}} service in {{site.data.keyword.cloud}}.
{: shortdesc}

{{site.data.keyword.at_full_notm}} records user-initiated activities that change the state of a service in {{site.data.keyword.cloud_notm}}. You can use this service to investigate abnormal activity and critical actions and to comply with regulatory audit requirements. In addition, you can be alerted about actions as they happen. The events that are collected comply with the Cloud Auditing Data Federation (CADF) standard. For more information, see the [getting started tutorial for {{site.data.keyword.at_full_notm}}](/docs/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-getting-started#getting-started).

Names for auditing events will change on July 1, 2020. The change replaces all underscore (_) characters in the names with dash (-) characters. See the following tables for the changes to each action name, and adjust your {{site.data.keyword.at_full_notm}} views and alerts as needed.
{:important}

## List of events: DNS zones
{: #events_dns_zones}

The following table lists the actions that are related to DNS zones and generate an event.

|Action (until July 1, 2020)| Action (starting July 1, 2020)|Description|
|---|---|---|  
|dns-svcs.zones.read  |dns-svcs.resource-records.read|Get a DNS zone.   |
|dns-svcs.zones.create|dns-svcs.resource-records.create|Create a DNS zone.|
|dns-svcs.zones.update|dns-svcs.resource-records.update|Update a DNS zone.|
|dns-svcs.zones.delete|dns-svcs.resource-records.delete|Delete a DNS zone.|

## List of events: resource records
{: #events_resource_record}

The following table lists the actions that are related to resource records and generate an event.

|Action (until July 1, 2020)| Action (starting July 1, 2020)|Description|
|---|---|---|
|dns-svcs.resource_records.read  ||Get a resource record.   |
|dns-svcs.resource_records.create||Create a resource record.|
|dns-svcs.resource_records.update||Update a resource record.|
|dns-svcs.resource_records.delete||Delete a resource record.|

## List of events: permitted networks
{: #events_permitted_networks}

The following table lists the actions that are related to permitted networks and generate an event.

|Action (until July 1, 2020)| Action (starting July 1, 2020)|Description|
|---|---|---|  
|dns-svcs.permitted_networks.read  |dns-svcs.permitted-networks.read|Get a permitted network from DNS zone.|
|dns-svcs.permitted_networks.create|dns-svcs.permitted-networks.create|Add a permitted network to DNS zone.|
|dns-svcs.permitted_networks.delete|dns-svcs.permitted-networks.delete|Remove a permitted network from DNS zone.|

## Viewing events
{: #ui}

The {{site.data.keyword.dns_short}} {{site.data.keyword.cloudaccesstrailshort}} events are available in the {{site.data.keyword.cloudaccesstrailshort}} instance in the {{site.data.keyword.cloud_notm}} **Frankfurt** region.

## Requesting additional information for an event
{: #info}

While monitoring {{site.data.keyword.cloudaccesstrailshort}} events that are generated by the {{site.data.keyword.dns_full_notm}}, if you identify an API request for which you need additional information, then check the `requestData` field in the event. Through June 30, 2020, open an IBM Support case and include the value of the field **X-CORRELATION-ID** that is available in `requestData`. Starting July 1, 2020, open an IBM support case and include the value of the field **requestId** that is available in `requestData`.
