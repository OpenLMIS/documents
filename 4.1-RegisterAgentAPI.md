Coming Soon
=======
# Create Satellite Facility API

### Communication Type

- HTTP Post, to OpenLMIS

### Parameters

systemID - Mandatory
authtoken - Mandatory
userID - Mandatory
parentFacilityID - Mandatory
facilityTypeID - Mandatory (Need to Discuss)
firstName - Mandatory
PrimaryPhoneNumber - Optional

### Return

satelliteFacilityId

### Dependencies

systemID

### Notes

CommTrack will store satelliteFacilityId & UserId mapping & provide satelliteFacilityId while submitting report to OpenLMIS.

