# Facility ATOM Feed

### Communication Type

- HTTP GET, Atom feed published by OpenLMIS

### Feed Content

- code
- name
- facilityType
- description
- gln
- mainPhone
- fax
- address1
- address2
- geographicZone
- catchmentPopulation
- latitude
- longitude
- altitude
- operatedBy
- coldStorageGrossCapacity
- coldStorageNetCapacity
- suppliesOthers
- sdp
- hasElectricity
- online
- hasElectricity
- hasElectronicDAR
- hasElectronicSCC
- active
- goLiveDate
- goDownDate
- satellite
- virtualFacility
- parentFacility
- comment
- enabled

### Notes   

If the value of field is null is OpenLMIS, that field tag will not be included in the response. It is the standard that will be maintained in all the API responses.

This feed updates CommTrack about creation of new facilities and updates on existing facilities supported by MoH.
TBD: How will we bootstrap the list of facilities in CommTrack as part of the initial co-deployment?  

### Example Feed
```xml
<?xml version="1.0" encoding="UTF-8"?>
<feed xmlns="http://www.w3.org/2005/Atom">
  <title>Event feed</title>
  <link rel="self" type="application/atom+xml" href="https://192.168.34.2/feeds/facility/recent" />
  <link rel="via" type="application/atom+xml" href="https://192.168.34.2/feeds/facility/1" />
  <author>
    <name>Atomfeed</name>
  </author>
  <id>+1</id>
  <generator uri="https://github.com/ICT4H/atomfeed">Atomfeed</generator>
  <updated>2013-10-17T09:56:20Z</updated>
  <entry>
    <title>Facility</title>
    <category term="facility" />
    <id>tag:atomfeed.ict4h.org:3ffdebd1-9f9b-44cc-b122-c3c08640c9e8</id>
    <updated>2013-10-17T09:52:30Z</updated>
    <content type="application/vnd.atomfeed+xml"><![CDATA[{"code":"F10","name":"Village Dispensary","description":"IT department","mainPhone":"9876234981","fax":"fax","address1":"A","address2":"B","geographicZone":"District1","facilityType":"Warehouse","catchmentPopulation":333,"latitude":22.1,"longitude":1.2,"altitude":3.3,"operatedBy":"FBO","coldStorageGrossCapacity":9.9,"coldStorageNetCapacity":6.6,"suppliesOthers":true,"sdp":true,"hasElectricity":true,"online":true,"hasElectronicSCC":true,"hasElectronicDAR":true,"active":true,"goLiveDate":1352572200000,"goDownDate":1352572200000,"satellite":false,"comment":"fc","enabled":true,"virtualFacility":false,"gln":"G7645"}]]></content>
  </entry>
  <entry>
    <title>Facility</title>
    <category term="facility" />
    <id>tag:atomfeed.ict4h.org:0a5c400d-3492-4b0b-ade5-f6e4cf3840b0</id>
    <updated>2013-10-17T09:54:01Z</updated>
    <content type="application/vnd.atomfeed+xml"><![CDATA[{"code":"F11","name":"Central Hospital","description":"IT department","mainPhone":"9876234981","fax":"fax","address1":"A","address2":"B","geographicZone":"Ngorongoro","facilityType":"Lvl3 Hospital","catchmentPopulation":333,"latitude":22.3,"longitude":1.2,"altitude":3.3,"operatedBy":"Private","coldStorageGrossCapacity":9.9,"coldStorageNetCapacity":6.6,"suppliesOthers":true,"sdp":true,"hasElectricity":true,"online":true,"hasElectronicSCC":true,"hasElectronicDAR":true,"active":true,"goLiveDate":1352572200000,"goDownDate":1352572200000,"satellite":false,"comment":"fc","enabled":true,"virtualFacility":false,"gln":"G7646"}]]></content>
  </entry>
  <entry>
    <title>Facility</title>
    <category term="facility" />
    <id>tag:atomfeed.ict4h.org:f273e4d4-9733-4a06-9f3b-924dc6997130</id>
    <updated>2013-10-17T09:56:02Z</updated>
    <content type="application/vnd.atomfeed+xml"><![CDATA[{"code":"F110","name":"Agent 100","mainPhone":"9988776655","geographicZone":"District1","facilityType":"Warehouse","operatedBy":"FBO","sdp":true,"active":true,"goLiveDate":1382003761775,"parentFacility":"F10","enabled":true,"virtualFacility":true}]]></content>
  </entry>
  <entry>
    <title>Facility</title>
    <category term="facility" />
    <id>tag:atomfeed.ict4h.org:834c231a-59b8-4394-905f-61d4de853510</id>
    <updated>2013-10-17T09:56:20Z</updated>
    <content type="application/vnd.atomfeed+xml"><![CDATA[{"code":"F210","name":"Agent 210","mainPhone":"9911221122","geographicZone":"Ngorongoro","facilityType":"Lvl3 Hospital","operatedBy":"Private","sdp":true,"active":true,"goLiveDate":1382003780521,"parentFacility":"F11","enabled":true,"virtualFacility":true}]]></content>
  </entry>
</feed>

```
