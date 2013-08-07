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

<?xml version="1.0" encoding="UTF-8"?><feed xmlns="http://www.w3.org/2005/Atom">  <title>Event feed</title>  <link rel="self" type="application/atom+xml" href="http://localhost:9091/feeds/facility/recent" />  <link rel="via" type="application/atom+xml" href="http://localhost:9091/feeds/facility/1" />  <author>    <name>Atomfeed</name>  </author>  <id>+1</id>  <generator uri="https://github.com/ICT4H/atomfeed">Atomfeed</generator>  <updated>2013-08-07T06:10:03Z</updated>  <entry>    <title>Facility</title>    <category term="facility" />    <id>tag:atomfeed.ict4h.org:af8a48b2-0e91-4e5a-8f00-2475817e5318</id>    <updated>2013-08-07T06:10:03Z</updated>    <content type="application/vnd.atomfeed+xml"><![CDATA[{"code":"FCcode20130807-113949","name":"FCname20130807-113949","type":"Lvl3 Hospital","description":"Testing description","mainPhone":"9711231305","fax":"9711231305","address1":"Address1","address2":"Address2","geographicZone":"Ngorongoro",   
"catchmentPopulation":100,"latitude":-555.5555,"longitude":444.4444,"altitude":4545.4545,"operatedBy":"MoH",  
"coldStorageGrossCapacity":3434.3434,"coldStorageNetCapacity":3535.3535,"suppliesOthers":true,"sdp":true,"hasElectricity":true,  
"online":true,"hasElectronicSCC":true,"hasElectronicDAR":true,"active":true,"goLiveDate":1377369000000,  
"goDownDate":1377455400000,"virtualFacility":false,"comments":"Comments","dataReportable":true,"gln":"Testing Gln"}]]></content>  </entry></feed>
