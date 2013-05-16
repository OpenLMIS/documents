
# Submit Report API Specifications

### Communication Type

- HTTP Post, to OpenLMIS

### Parameters

- username - Mandatory (Post Request Header)
- password - Mandatory (Post Request Header)
- facilityId - Mandatory
- programId - Mandatory
- productCode - Mandatory - Multiple
- periodId - Mandatory
- userId - Mandatory
- beginningBalance - Optional
- quantityDispensed - Optional
- quantityReceived - Optional
- lossesAndAdjustments - Optional
- stockInHand - Optional
- newPatientCount - Optional
- stockOutDays - Optional
- quantityRequested - Optional
- reasonForRequestedQuantity - Optional
- approvedQuantity - Optional
- remarks - Optional

### Return

- requisitionId

### Dependencies

- username
- password
- facilityId
- programId
- productCode
- periodId
- userId

### Notes

- userID is for CHW or Clinician submitting the Report.
- "username" & "password" (authentication token) are one time created for CommTrack system in OpenLMIS and required for all API communications. They needs to be sent as request header for authentication.
- CommTrack will retain the RequisitionID generated for each Report submitted to OpenLMIS.
- Parameter names are case-insensitive.
- OpenLMIS has macro-level requirements regarding the inclusion of some subset of beginningBalance, quantityDispensed, quantityReceived, and stockInHand values to support the reorder calculations. Individual Programs can be configured with combinations to suit their operating scenarios, provided they properly support the reorder calculations. FOR OUR COMMTRACK-OPENLMIS INTEGRATION, STOCKINHAND IS SUFFICIENT TO SUPPORT THE REORDER CALCULATIONS.

### JSON Example 1

(BeginningBalance, TotalReceivedQuantity, TotalConsumedQauntity assumed mandatory for more robust CommTrack integration)

{ "facilityId" : "1", "programId" : "2", "periodId": "2", "userId" : "CHW1", "products" :[ { "productCode":"EM1", "beginningBalance": 3, "quantityDispensed": 1, "quantityReceived": 0, "lossesAndAdjustments" : [ {"type": {"name": "TRANSFER\_OUT" }, "quantity" : 2}], "stockInHand":0, "approvedQuantity" : 65, "newPatientCount":2, "stockOutDays" : 2, "quantityRequested" : 3, "reasonForRequestedQuantity" : "reason", "remarks" : "1" }, { "productCode":"EM2", "beginningBalance": 3, "quantityDispensed": 1, "quantityReceived": 0, "lossesAndAdjustments" : [ {"type": {"name": "TRANSFER\_OUT", "additive" : "false" }, "quantity" : 2}], "stockInHand":0, "approvedQuantity" : 65, "newPatientCount":2, "stockOutDays" : 2, "quantityRequested" : 3, "reasonForRequestedQuantity" : "reason", "remarks" : "1" }, { "productCode":"EM3", "beginningBalance": 3, "quantityDispensed": 1, "quantityReceived": 0, "lossesAndAdjustments" : [ {"type": {"name": "TRANSFER\_OUT", "additive" : "false" }, "quantity" : 2}], "stockInHand":0, "approvedQuantity" : 65, "newPatientCount":2, "stockOutDays" : 2, "quantityRequested" : 3, "reasonForRequestedQuantity" : "reason", "remarks" : "1" }] }

### JSON Example 2

(stockInHand assumed mandatory for the basic CommTrack integration)

{ "facilityId": "", "programId": "", "periodId": "", "userId": "", "products": [ { "productCode": "", "stockInHand": "0", "lossesAndAdjustments": [ { "type": { "name": "TRANSFER\_OUT" }, "quantity": 2 } ], "newPatientCount": "0", "stockOutDays": "2" } ] }

### HTTP Responses

- **200 OK** - All Indicates that the specified action was successfully completed.
- **401 Unauthorized** - Raised when the username-password combination incorrect.
- **400 Invalid data** - Indicates invalid data.
- **500 Internal Server Error** - Indicates that the server encountered an error while attempting to execute the desired action.
