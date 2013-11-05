# Requisition Status ATOM Feed

#### Communication Type

- HTTP GET on
	- [/feeds/requisition-status/recent](#)
	- [/feeds/requisition-status/**\<pageNumber\>**](#)


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
  <link rel="self" type="application/atom+xml" href="http://localhost:9091/feeds/requisition-status/2" />
  <link rel="via" type="application/atom+xml" href="http://localhost:9091/feeds/requisition-status/2" />
  <link rel="next-archive" type="application/atom+xml" href="http://localhost:9091/feeds/requisition-status/3" />
  <link rel="prev-archive" type="application/atom+xml" href="http://localhost:9091/feeds/requisition-status/1" />
  <author>
    <name>Atomfeed</name>
  </author>
  <id>+2</id>
  <generator uri="https://github.com/ICT4H/atomfeed">Atomfeed</generator>
  <updated>2013-11-05T07:51:32Z</updated>
  <entry>
    <title>Requisition Status</title>
    <category term="requisition-status" />
    <id>tag:atomfeed.ict4h.org:4741cfad-2d5e-4ed0-b3a1-b9c89112b592</id>
    <updated>2013-11-05T07:50:24Z</updated>
    <content type="application/vnd.atomfeed+xml"><![CDATA[{"requisitionId":1,"requisitionStatus":"RELEASED","emergency":false,"startDate":1354300200000,"endDate":1356978599000}]]></content>
  </entry>
  <entry>
    <title>Requisition Status</title>
    <category term="requisition-status" />
    <id>tag:atomfeed.ict4h.org:b08c56cc-c40f-49f2-9719-994e3b959555</id>
    <updated>2013-11-05T07:50:24Z</updated>
    <content type="application/vnd.atomfeed+xml"><![CDATA[{"requisitionId":1,"requisitionStatus":"RELEASED","emergency":false,"startDate":1354300200000,"endDate":1356978599000,"orderId":1,"orderStatus":"IN_ROUTE"}]]></content>
  </entry>
  <entry>
    <title>Requisition Status</title>
    <category term="requisition-status" />
    <id>tag:atomfeed.ict4h.org:fe01a32d-5209-4dd9-9c97-9aca699ad472</id>
    <updated>2013-11-05T07:50:25Z</updated>
    <content type="application/vnd.atomfeed+xml"><![CDATA[{"requisitionId":1,"requisitionStatus":"RELEASED","emergency":false,"startDate":1354300200000,"endDate":1356978599000,"orderId":1,"orderStatus":"TRANSFER_FAILED"}]]></content>
  </entry>
  <entry>
    <title>Requisition Status</title>
    <category term="requisition-status" />
    <id>tag:atomfeed.ict4h.org:f1c0d68c-326a-4616-8362-9f8ccbd3214e</id>
    <updated>2013-11-05T07:51:24Z</updated>
    <content type="application/vnd.atomfeed+xml"><![CDATA[{"requisitionId":2,"requisitionStatus":"INITIATED","emergency":false,"startDate":1356978600000,"endDate":1359656999000}]]></content>
  </entry>
  <entry>
    <title>Requisition Status</title>
    <category term="requisition-status" />
    <id>tag:atomfeed.ict4h.org:91c10344-1b21-42fe-ad16-76822f6293c0</id>
    <updated>2013-11-05T07:51:32Z</updated>
    <content type="application/vnd.atomfeed+xml"><![CDATA[{"requisitionId":2,"requisitionStatus":"SUBMITTED","emergency":false,"startDate":1356978600000,"endDate":1359656999000}]]></content>
  </entry>
</feed>

```
