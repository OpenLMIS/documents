# Facility ATOM Feed

### Communication Type

- HTTP GET, Atom feed published by OpenLMIS

### Feed Content

- facilityCode
- facilityName
- facilityTypeID
- facilityDescription
- GLN
- facilityMainPhone
- facilityFax
- facilityAddress1
- facilityAddress2
- geographicZoneID
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
- IsActive
- facilityGoLiveDate
- facilityGoDownDate
- IsSatellitefacility
- SetelliteParentID
- facilityComments
- DataReportable
- LastModifiedDate

### Notes

This feed updates CommTrack about creation of new facilities and updates on existing facilities supported by MoH.
TBD: How will we bootstrap the list of facilities in CommTrack as part of the initial co-deployment?  

### Example Feed

<?xml version="1.0" encoding="UTF-8"?>

<feed xmlns="http://www.w3.org/2005/Atom">
  <title>Event feed</title>
  <link rel="self" type="application/atom+xml" href="XXXX" />
  <link rel="via" type="application/atom+xml" href="XXXX" />
  <link rel="prev-archive" type="application/atom+xml" href="XXXXX" />
  <author>
    <name>Atomfeed</name>
  </author>
  <id>+2</id>
  <generator uri="https://github.com/ICT4H/atomfeed">Atomfeed</generator>
  <updated>2013-05-31T05:13:38Z</updated>
  <entry>
    <title>Facility</title>
    <category />
    <id>tag:atomfeed.ict4h.org:2c961832-3983-4e85-896b-da5730fb386b</id>
    <updated>2013-05-31T05:13:25Z</updated>
    <content type="application/vnd.atomfeed+xml"><![CDATA[{"id":5,"code":"FCcode20130531-104312","name":"FCname20130531-104312","typeId":2,"description":"Testing description","mainPhone":"9711231305","fax":"9711231305","address1":"Address1","address2":"Address2","geographicZoneID":4,"catchmentPopulation":500000,"latitude":-555.5555,"longitude":444.4444,"altitude":4545.4545,"operatedBy":"MoH","coldStorageGrossCapacity":3434.3434,"coldStorageNetCapacity":3535.3535,"suppliesOthers":true,"hasElectricity":true,"hasElectronicSCC":true,"hasElectronicDAR":true,"active":true,"goLiveDate":1369420200000,"goDownDate":1369506600000,"satelliteFacility":false,"satelliteParentID":null,"comments":"Comments","doNotDisplay":false,"modifiedDate":1369977205038,"online":true,"sdp":true,"gln":"Testing Gln"}]]></content>
  </entry>
  <entry>
    <title>Facility</title>
    <category />
    <id>tag:atomfeed.ict4h.org:fd8fcee9-db67-465d-b9eb-5da1faf91b51</id>
    <updated>2013-05-31T05:13:32Z</updated>
    <content type="application/vnd.atomfeed+xml"><![CDATA[{"id":5,"code":"FCcode20130531-104312","name":"FCname20130531-104312","typeId":2,"description":"Testing description","mainPhone":"9711231305","fax":"9711231305","address1":"Address1","address2":"Address2","geographicZoneID":4,"catchmentPopulation":500000,"latitude":-555.5555,"longitude":444.4444,"altitude":4545.4545,"operatedBy":"MoH","coldStorageGrossCapacity":3434.3434,"coldStorageNetCapacity":3535.3535,"suppliesOthers":true,"hasElectricity":true,"hasElectronicSCC":true,"hasElectronicDAR":true,"active":false,"goLiveDate":1369420200000,"goDownDate":1369506600000,"satelliteFacility":false,"satelliteParentID":null,"comments":"Comments","doNotDisplay":false,"modifiedDate":1369977212205,"online":true,"sdp":true,"gln":"Testing Gln"}]]></content>
  </entry>
  <entry>
    <title>Facility</title>
    <category />
    <id>tag:atomfeed.ict4h.org:0f77f2e2-57b1-4c13-8dd6-aa76ff525c91</id>
    <updated>2013-05-31T05:13:38Z</updated>
    <content type="application/vnd.atomfeed+xml"><![CDATA[{"id":5,"code":"FCcode20130531-104312","name":"FCname20130531-104312","typeId":2,"description":"Testing description","mainPhone":"9711231305","fax":"9711231305","address1":"Address1","address2":"Address2","geographicZoneID":4,"catchmentPopulation":500000,"latitude":-555.5555,"longitude":444.4444,"altitude":4545.4545,"operatedBy":"MoH","coldStorageGrossCapacity":3434.3434,"coldStorageNetCapacity":3535.3535,"suppliesOthers":true,"hasElectricity":true,"hasElectronicSCC":true,"hasElectronicDAR":true,"active":true,"goLiveDate":1369420200000,"goDownDate":1369506600000,"satelliteFacility":false,"satelliteParentID":null,"comments":"Comments","doNotDisplay":false,"modifiedDate":1369977218399,"online":true,"sdp":true,"gln":"Testing Gln"}]]></content>
  </entry>
</feed>
