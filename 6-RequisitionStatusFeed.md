# Requisition Status ATOM Feed

### Communication Type

- HTTP GET, Atom feed published by OpenLMIS

### Parameters

- Authentication token (Base64 encrypted string containing username:password)
- 
### Feed Content

- requisitionID
- requisitionStatus  { Submitted | Authorized | In Approval | Approved | Released }
- orderID  (null until the requisition has been released as an order)
- orderStatus   { Released | Packed | Received }
- periodID - Optional

### Notes

Atom feed is in xml, data payload is JSON.

### Example Feed ( below JSONs need to be updated )

<?xml version="1.0" encoding="UTF-8"?>
<feed xmlns="http://www.w3.org/2005/Atom">
  <title>Event feed</title>
  <link rel="self" type="application/atom+xml" href="XXX" />
  <link rel="via" type="application/atom+xml" href="XXX" />
  <author>
    <name>Atomfeed</name>
  </author>
  <id>+1</id>
  <generator uri="https://github.com/ICT4H/atomfeed">Atomfeed</generator>
  <updated>2013-05-31T05:10:34Z</updated>
  <entry>
    <title>Requisition</title>
    <category />
    <id>tag:atomfeed.ict4h.org:4cf173a2-5901-4e5c-b8ae-bfc5e27e2e7b</id>
    <updated>2013-05-31T05:10:33Z</updated>
    <content type="application/vnd.atomfeed+xml"><![CDATA[{"requisitionId":1,"facilityId":1,"programId":1,"periodId":2,"requisitionStatus":"INITIATED","externalSystem":"commTrack"}]]></content>
  </entry>
  <entry>
    <title>Requisition</title>
    <category />
    <id>tag:atomfeed.ict4h.org:ffce5273-2bed-4d12-9959-b16274375eb1</id>
    <updated>2013-05-31T05:10:33Z</updated>
    <content type="application/vnd.atomfeed+xml"><![CDATA[{"requisitionId":1,"facilityId":1,"programId":1,"periodId":2,"requisitionStatus":"SUBMITTED","externalSystem":"commTrack"}]]></content>
  </entry>
  <entry>
    <title>Requisition</title>
    <category />
    <id>tag:atomfeed.ict4h.org:f68bb2a2-1021-45ef-bd73-a9f1daa8cb10</id>
    <updated>2013-05-31T05:10:33Z</updated>
    <content type="application/vnd.atomfeed+xml"><![CDATA[{"requisitionId":1,"facilityId":1,"programId":1,"periodId":2,"requisitionStatus":"AUTHORIZED","externalSystem":"commTrack"}]]></content>
  </entry>
  <entry>
    <title>Requisition</title>
    <category />
    <id>tag:atomfeed.ict4h.org:c029ee7d-81dc-46fa-af86-e5e54bc8b739</id>
    <updated>2013-05-31T05:10:34Z</updated>
    <content type="application/vnd.atomfeed+xml"><![CDATA[{"requisitionId":1,"facilityId":1,"programId":1,"periodId":2,"requisitionStatus":"APPROVED","externalSystem":"commTrack"}]]></content>
  </entry>
  <entry>
    <title>Requisition</title>
    <category />
    <id>tag:atomfeed.ict4h.org:ceee1964-01af-402f-9a67-c8e1d76deb7c</id>
    <updated>2013-05-31T05:10:34Z</updated>
    <content type="application/vnd.atomfeed+xml"><![CDATA[{"requisitionId":1,"facilityId":1,"programId":1,"periodId":2,"requisitionStatus":"RELEASED","externalSystem":"commTrack"}]]></content>
  </entry>
</feed>
