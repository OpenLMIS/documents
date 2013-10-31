# Requisition Status ATOM Feed

### Communication Type

- HTTP GET, http://localhost:9091/feeds/requisition-status/recent

### Feed Content

- requisitionId
- requisitionStatus  { INITIATED | SUBMITTED | AUTHORIZED | IN_APPROVAL | APPROVED | RELEASED }
- orderID  (Tag will be missing until the requisition has been released as an order)
- orderStatus   (null until the requisition has been released as an order) { RELEASED | READY_TO_PACK | RECIEVED | IN_ROUTE | TRANSFER_FAILED | PACKED }
- emergency { true | false }
- startDate ( in ms format)
- endDate ( in ms format)

### Notes

Atom feed is in xml, data payload is JSON.

### Example Feed 

``` xml
<?xml version="1.0" encoding="UTF-8"?>
<feed xmlns="http://www.w3.org/2005/Atom">
  <title>Event feed</title>
  <link rel="self" type="application/atom+xml" href="http://localhost:9091/feeds/requisition-status/1" />
  <link rel="via" type="application/atom+xml" href="http://localhost:9091/feeds/requisition-status/1" />
  <link rel="next-archive" type="application/atom+xml" href="http://localhost:9091/feeds/requisition-status/2" />
  <author>
    <name>Atomfeed</name>
  </author>
  <id>+1</id>
  <generator uri="https://github.com/ICT4H/atomfeed">Atomfeed</generator>
  <updated>2013-10-29T10:11:50Z</updated>
  <entry>
    <title>Requisition Status</title>
    <category term="requisition-status" />
    <id>tag:atomfeed.ict4h.org:f4fa4edf-60be-4b4b-abfc-624a0d32f3ca</id>
    <updated>2013-10-29T10:11:49Z</updated>
    <content type="application/vnd.atomfeed+xml"><![CDATA[{"requisitionId":28,"requisitionStatus":"INITIATED","emergency":false,"startDate":1358274600000,"endDate":1359570599000}]]></content>
  </entry>
  <entry>
    <title>Requisition Status</title>
    <category term="requisition-status" />
    <id>tag:atomfeed.ict4h.org:55f49690-bde7-4a43-abd1-03866f0e7a84</id>
    <updated>2013-10-29T10:11:49Z</updated>
    <content type="application/vnd.atomfeed+xml"><![CDATA[{"requisitionId":28,"requisitionStatus":"SUBMITTED","emergency":false,"startDate":1358274600000,"endDate":1359570599000}]]></content>
  </entry>
  <entry>
    <title>Requisition Status</title>
    <category term="requisition-status" />
    <id>tag:atomfeed.ict4h.org:2f612f74-7a44-40ef-88c6-65f022f97d3a</id>
    <updated>2013-10-29T10:11:49Z</updated>
    <content type="application/vnd.atomfeed+xml"><![CDATA[{"requisitionId":28,"requisitionStatus":"AUTHORIZED","emergency":false,"startDate":1358274600000,"endDate":1359570599000}]]></content>
  </entry>
  <entry>
    <title>Requisition Status</title>
    <category term="requisition-status" />
    <id>tag:atomfeed.ict4h.org:0ac5b27f-bc65-45d6-9bc8-a3277d39ecd3</id>
    <updated>2013-10-29T10:11:49Z</updated>
    <content type="application/vnd.atomfeed+xml"><![CDATA[{"requisitionId":28,"requisitionStatus":"APPROVED","emergency":false,"startDate":1358274600000,"endDate":1359570599000}]]></content>
  </entry>
  <entry>
    <title>Requisition Status</title>
    <category term="requisition-status" />
    <id>tag:atomfeed.ict4h.org:6364418f-91dc-42d6-a108-36ef39e383c0</id>
    <updated>2013-10-29T10:11:50Z</updated>
    <content type="application/vnd.atomfeed+xml"><![CDATA[{"requisitionId":28,"requisitionStatus":"RELEASED","emergency":false,"startDate":1358274600000,"endDate":1359570599000}]]></content>
  </entry>
</feed>
[CDATA[{"requisitionId":28,"requisitionStatus":"RELEASED","emergency":false,"startDate":1358274600000,"endDate":1359570599000,"orderId":28,"orderStatus":"READY_TO_PACK"}]]></content>
  </entry>
  <entry>
    <title>Requisition Status</title>
    <category term="requisition-status" />
    <id>tag:atomfeed.ict4h.org:4b8eedce-edda-4745-ba66-4c3791c2ce34</id>
    <updated>2013-10-29T10:11:53Z</updated>
    <content type="application/vnd.atomfeed+xml"><![CDATA[{"requisitionId":28,"requisitionStatus":"RELEASED","emergency":false,"startDate":1358274600000,"endDate":1359570599000,"orderId":28,"orderStatus":"RECEIVED"}]]></content>
  </entry>
</feed>
```
