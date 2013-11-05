# Facility ATOM Feed

#### Communication Type

- HTTP GET on
	- [/feeds/facilities/recent](#)
	- [/feeds/facilities/**\<pageNumber\>**](#)


#### Feed Content

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

#### Notes

If the value of field is null is OpenLMIS, that field tag will not be included in the response. It is the standard that will be maintained in all the API responses.

This feed updates CommTrack about creation of new facilities and updates on existing facilities supported by MoH.
TBD: How will we bootstrap the list of facilities in CommTrack as part of the initial co-deployment?  

#### Example Feed
```xml
<?xml version="1.0" encoding="UTF-8"?>
<feed xmlns="http://www.w3.org/2005/Atom">
  <title>Event feed</title>
  <link rel="self" type="application/atom+xml" href="http://localhost:9091/feeds/facilities/recent" />
  <link rel="via" type="application/atom+xml" href="http://localhost:9091/feeds/facilities/1" />
  <author>
    <name>Atomfeed</name>
  </author>
  <id>+1</id>
  <generator uri="https://github.com/ICT4H/atomfeed">Atomfeed</generator>
  <updated>2013-11-05T07:44:08Z</updated>
  <entry>
    <title>Facility</title>
    <category term="facilities" />
    <id>tag:atomfeed.ict4h.org:1f61a202-3539-494d-90f6-f8045401fb04</id>
    <updated>2013-11-05T07:41:06Z</updated>
    <content type="application/vnd.atomfeed+xml"><![CDATA[{"geographicZone":"Ngorongoro","facilityType":"Health Center","operatedBy":"MoH","programsSupported":["ESS_MEDS","HIV"],"code":"F10","enabled":true,"name":"Village Dispensary","id":256,"description":"A village dispensary","active":true,"createdBy":1,"modifiedBy":1,"virtualFacility":false,"sdp":false,"goLiveDate":1375295400000,"gln":"123","catchmentPopulation":333333,"latitude":123.123,"longitude":233.444,"altitude":444.0,"coldStorageGrossCapacity":4444.0,"coldStorageNetCapacity":3434.0,"suppliesOthers":true,"hasElectricity":true,"online":true,"hasElectronicSCC":false,"hasElectronicDAR":false,"goDownDate":1383589800000}]]></content>
  </entry>
  <entry>
    <title>Facility</title>
    <category term="facilities" />
    <id>tag:atomfeed.ict4h.org:093fff3f-5618-44ad-ba36-4011819f10af</id>
    <updated>2013-11-05T07:44:08Z</updated>
    <content type="application/vnd.atomfeed+xml"><![CDATA[{"geographicZone":"Ngorongoro","facilityType":"Lvl1 Hospital","operatedBy":"NGO","programsSupported":["VACCINES","MALARIA"],"code":"F11","enabled":true,"name":"Central Hospital","id":257,"active":true,"createdBy":1,"modifiedBy":1,"virtualFacility":false,"sdp":true,"goLiveDate":1283970600000,"suppliesOthers":true,"hasElectricity":true,"online":true,"hasElectronicSCC":true,"hasElectronicDAR":true,"goDownDate":1383589800000}]]></content>
  </entry>
</feed>

```
