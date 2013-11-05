# Facility programs ATOM Feed

#### Communication Type

- HTTP GET on
	- [/feeds/programs-supported/recent](#)
	- [/feeds/programs-supported/**\<pageNumber\>**](#)


#### Feed Content

- facilityCode
- programCode
- programName
- Active {TRUE | FALSE} 
- startDate

#### Notes

CommTrack will use this facility-program data to determine what programs are active at individual facilities, to support the replenishment process for  Clinicians / CHWs. 

#### Sample feed

```xml
<?xml version="1.0" encoding="UTF-8"?>
<feed xmlns="http://www.w3.org/2005/Atom">
  <title>Event feed</title>
  <link rel="self" type="application/atom+xml" href="http://localhost:9091/feeds/programs-supported/recent" />
  <link rel="via" type="application/atom+xml" href="http://localhost:9091/feeds/programs-supported/1" />
  <author>
    <name>Atomfeed</name>
  </author>
  <id>+1</id>
  <generator uri="https://github.com/ICT4H/atomfeed">Atomfeed</generator>
  <updated>2013-11-05T07:44:08Z</updated>
  <entry>
    <title>Programs Supported</title>
    <category term="programs-supported" />
    <id>tag:atomfeed.ict4h.org:cb1a0e5d-ca58-4c44-ad15-f5c3578dea5b</id>
    <updated>2013-11-05T07:41:06Z</updated>
    <content type="application/vnd.atomfeed+xml"><![CDATA[{"facilityCode":"F10","programsSupported":[{"code":"ESS_MEDS","name":"ESSENTIAL MEDICINES","active":false,"startDate":1383589800000},{"code":"HIV","name":"HIV","active":false,"startDate":1383676200000}]}]]></content>
  </entry>
  <entry>
    <title>Programs Supported</title>
    <category term="programs-supported" />
    <id>tag:atomfeed.ict4h.org:29b2bec4-b3fd-4212-b627-470ea8995a44</id>
    <updated>2013-11-05T07:44:08Z</updated>
    <content type="application/vnd.atomfeed+xml"><![CDATA[{"facilityCode":"F11","programsSupported":[{"code":"VACCINES","name":"VACCINES","active":false,"startDate":1383244200000},{"code":"MALARIA","name":"MALARIA","active":false,"startDate":1384281000000}]}]]></content>
  </entry>
</feed>
```
