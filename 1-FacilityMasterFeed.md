# Facility ATOM Feed

### Communication Type

- HTTP GET, Atom feed published by OpenLMIS

### Feed Content

- facilityCode
- facilityName
- facilityType
- facilityDescription
- GLN
- facilityMainPhone
- facilityFax
- facilityAddress1
- facilityAddress2
- geographicZone
- catchmentPopulation
- facilityLAT
- facilityLONG
- facilityAltitude
- facilityOperatedBy
- coldstorageGrossCapacity
- coldstorageNetCapacity
- facilitySuppliesOthers
- facilityIsSDP
- facilityHasElectrity
- facilityIsOnline
- facilityHasElectronicSCC
- facilityHasElectronicDAR
- facilityIsActive
- facilityGoLiveDate
- facilityGoDownDate
- facilityIsSatellite
- facilityIsvirtual
- ParentfacilityCode
- facilityComments
- Enabled
- LastModifiedDate

### Notes

This feed updates CommTrack about creation of new facilities and updates on existing facilities supported by MoH.
TBD: How will we bootstrap the list of facilities in CommTrack as part of the initial co-deployment?  

### Example Feed
```xml
<?xml version="1.0" encoding="UTF-8"?>
<feed xmlns="http://www.w3.org/2005/Atom">
  <title>Event feed</title>
  <link rel="self" type="application/atom+xml" href="https://uat.221.134.198.28.xip.io/feeds/facility/2" />
  <link rel="via" type="application/atom+xml" href="https://uat.221.134.198.28.xip.io/feeds/facility/2" />
  <link rel="next-archive" type="application/atom+xml" href="https://uat.221.134.198.28.xip.io/feeds/facility/3" />
  <link rel="prev-archive" type="application/atom+xml" href="https://uat.221.134.198.28.xip.io/feeds/facility/1" />
  <author>
    <name>Atomfeed</name>
  </author>
  <id>+2</id>
  <generator uri="https://github.com/ICT4H/atomfeed">Atomfeed</generator>
  <updated>2013-10-10T07:36:36Z</updated>
  <entry>
    <title>Facility</title>
    <category term="facility" />
    <id>tag:atomfeed.ict4h.org:464b594e-e0f8-4095-bcb8-3755dbaf22bc</id>
    <updated>2013-10-10T07:35:17Z</updated>
    <content type="application/vnd.atomfeed+xml"><![CDATA[{"code":"F33","name":"Zonal Hospital","type":"Lvl3 Hospital","description":"IT department","mainPhone":"9876234981","fax":"fax","address1":"A","address2":"B","geographicZone":"District3","catchmentPopulation":333,"latitude":22.3,"longitude":1.2,"altitude":3.3,"operatedBy":"FBO","coldStorageGrossCapacity":9.9,"coldStorageNetCapacity":6.6,"suppliesOthers":true,"sdp":true,"hasElectricity":true,"online":true,"hasElectronicSCC":true,"hasElectronicDAR":true,"active":true,"goLiveDate":1352572200000,"goDownDate":1352572200000,"satelliteFacility":false,"virtualFacility":false,"comments":"fc","enabled":true,"gln":"G7646"}]]></content>
  </entry>
  <entry>
    <title>Facility</title>
    <category term="facility" />
    <id>tag:atomfeed.ict4h.org:b4ba5480-9b5f-4a81-af65-801fd6aa9b24</id>
    <updated>2013-10-10T07:35:27Z</updated>
    <content type="application/vnd.atomfeed+xml"><![CDATA[{"code":"F10C","name":"Facility10C","type":"Lvl3 Hospital","description":"Village Clinic","mainPhone":"9876234981","fax":"fax","address1":"A","address2":"B","geographicZone":"District5","catchmentPopulation":70000,"latitude":22.3,"longitude":1.2,"altitude":3.3,"operatedBy":"FBO","coldStorageGrossCapacity":9.9,"coldStorageNetCapacity":6.6,"suppliesOthers":true,"sdp":true,"hasElectricity":true,"online":true,"hasElectronicSCC":true,"hasElectronicDAR":true,"active":true,"goLiveDate":1352572200000,"goDownDate":1352572200000,"satelliteFacility":false,"virtualFacility":false,"comments":"fc","enabled":true,"gln":"G7646"}]]></content>
  </entry>
</feed>
```
