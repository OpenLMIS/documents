# User Registration API

### Communication Type

- HTTP Post, to OpenLMIS

### Parameters

systemID - Mandatory
authtoken - Mandatory
userID - Mandatory
facilityID - Mandatory
programID - Madatory
firstName - Mandatory
lastName - Madatory
email
status - Mandatory
role - Mandatory
CreatedAt

### Return

Confirmation user is registered

### Dependencies

systemID

### Notes

CommTiack will call this API when adding/updating a Clinician or CHW whose Reports will be submitted to OpenLMIS.

Status  ∈  { Active |  Inactive }
Role   ∈  { Creator |  Approver }

UserId is CommTrack UserId which is used by Commtrack while sending report.

