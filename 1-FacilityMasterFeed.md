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
- Active
- facilityGoLiveDate
- facilityGoDownDate
- IsSatellitefacility
- Isvirtualfacility
- ParentfacilityID
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
 <link rel="self" type="application/atom+xml" href="https://uat.221.134.198.28.xip.io/feeds/facility/recent" />
 <link rel="via" type="application/atom+xml" href="https://uat.221.134.198.28.xip.io/feeds/facility/1" />
 <author>
   <name>Atomfeed</name>
 </author>
 <id>+1</id>
 <generator uri="https://github.com/ICT4H/atomfeed">Atomfeed</generator>
 <updated>2013-09-13T05:37:05Z</updated>
 <entry>
   <title>Facility</title>
   <category term="facility" />
   <id>tag:atomfeed.ict4h.org:d39c0eec-4395-4396-aaa7-65897a57f8cc</id>
   <updated>2013-09-13T05:37:05Z</updated>
   <content type="application/vnd.atomfeed+xml"><![CDATA[{"code":"F10","name":"Village Dispensary","type":"Warehouse",  
   "description":"IT department","mainPhone":"9876234981","fax":"fax","address1":"A","address2":"B","geographicZone":  
   "District1","catchmentPopulation":333,"latitude":22.1,"longitude":1.2,"altitude":3.3,"operatedBy":"NGO",  
   "coldStorageGrossCapacity":9.9,"coldStorageNetCapacity":6.6,"suppliesOthers":true,"sdp":true,  
   "hasElectricity":true,"online":true,"hasElectronicSCC":true,"hasElectronicDAR":true,"active":false,  
   "goLiveDate":1352572200000,"goDownDate":1352572200000,"satelliteFacility":false,"virtualFacility":false,  
   "comments":"fc","enabled":true,"gln":"G7645"}]]></content>
 </entry>
</feed>
