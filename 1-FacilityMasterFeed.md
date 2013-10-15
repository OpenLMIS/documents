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
- coldStorageGrossCapacity
- coldStorageNetCapacity
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
- facilityIsVirtual
- parentfacilityCode
- facilityComments
- enabled
- lastModifiedDate

### Notes

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
  <updated>2013-10-15T15:20:16Z</updated>
  <entry>
    <title>Facility</title>
    <category term="facility" />
    <id>tag:atomfeed.ict4h.org:f83756db-efa1-413d-ba9f-cce907e25dbe</id>
    <updated>2013-10-15T14:49:59Z</updated>
    <content type="application/vnd.atomfeed+xml"><![CDATA[{"facilityCode":"F50","facilityName":"Zonal Hospital","facilityType":"Lvl3 Hospital","facilityMainPhone":"9999999999","facilityFax":"12345","facilityAddress1":"Address1","facilityAddress2":"Address2","geographicZone":"Ngorongoro","catchmentPopulation":12345,"facilityLAT":22.3,"facilityLONG":22.4,"facilityAltitude":3.3,"facilityOperatedBy":"NGO","coldStorageGrossCapacity":34.0,"coldStorageNetCapacity":50.0,"facilitySuppliesOthers":true,"facilityIsSDP":true,"facilityHasElectricity":true,"facilityIsOnline":true,"facilityHasElectronicSCC":true,"facilityHasElectronicDAR":true,"facilityIsActive":true,"facilityGoLiveDate":1380565800000,"facilityIsVirtual":false,"enabled":true}]]></content>
  </entry>
  <entry>
    <title>Facility</title>
    <category term="facility" />
    <id>tag:atomfeed.ict4h.org:c3a96c5a-af0e-468b-88cf-436d501319ed</id>
    <updated>2013-10-15T14:56:27Z</updated>
    <content type="application/vnd.atomfeed+xml"><![CDATA[{"facilityCode":"F50","facilityName":"Zonal Hospital","facilityType":"Lvl3 Hospital","facilityMainPhone":"9999999999","facilityFax":"12345","facilityAddress1":"Address1","facilityAddress2":"Address2","geographicZone":"Ngorongoro","catchmentPopulation":12345,"facilityLAT":22.3,"facilityLONG":22.4,"facilityAltitude":3.3,"facilityOperatedBy":"NGO","coldStorageGrossCapacity":34.0,"coldStorageNetCapacity":50.0,"facilitySuppliesOthers":true,"facilityIsSDP":true,"facilityHasElectricity":true,"facilityIsOnline":true,"facilityHasElectronicSCC":true,"facilityHasElectronicDAR":true,"facilityIsActive":false,"facilityGoLiveDate":1380565800000,"facilityIsVirtual":false,"enabled":true}]]></content>
  </entry>
  <entry>
    <title>Facility</title>
    <category term="facility" />
    <id>tag:atomfeed.ict4h.org:ba9e9acd-30a4-4fd9-8add-35b1e2d5a66a</id>
    <updated>2013-10-15T15:20:03Z</updated>
    <content type="application/vnd.atomfeed+xml"><![CDATA[{"facilityCode":"F5","facilityName":"Agent 5","facilityType":"Warehouse","facilityMainPhone":"1122112211","geographicZone":"District1","facilityOperatedBy":"NGO","facilityIsSDP":true,"facilityIsActive":true,"facilityGoLiveDate":1381850403169,"facilityIsVirtual":true,"parentFacilityCode":"F10","enabled":true}]]></content>
  </entry>
  <entry>
    <title>Facility</title>
    <category term="facility" />
    <id>tag:atomfeed.ict4h.org:1e58241b-73b2-49c8-a7d9-7b032356fc2f</id>
    <updated>2013-10-15T15:20:16Z</updated>
    <content type="application/vnd.atomfeed+xml"><![CDATA[{"facilityCode":"F8","facilityName":"Agent 8","facilityType":"Lvl3 Hospital","facilityMainPhone":"1122112211","geographicZone":"Ngorongoro","facilityOperatedBy":"FBO","facilityIsSDP":true,"facilityIsActive":true,"facilityGoLiveDate":1381850416025,"facilityIsVirtual":true,"parentFacilityCode":"F11","enabled":true}]]></content>
  </entry>
</feed>
```
