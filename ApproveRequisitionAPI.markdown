
# Approve Requisition API Specifications

### Communication Type

- HTTP PUT, to OpenLMIS

### Parameters

- username - Mandatory (Post Request Header)
- password - Mandatory (Post Request Header)
- requisitionId - Mandatory
- userId - Mandatory
- productCode - Mandatory - Multiple
- quantityApproved - Mandatory - Multiple
- remarks - Optional

### Return

- requisitionId

### Dependencies

- username
- password
- requisitionId

### Notes

- CommTrack will retain the RequisitionID generated for each Report submitted to OpenLMIS.
- userId is CommTrack UserId who is registered in OpenLMIS as approver.

### JSON Example 1

(BeginningBalance, TotalReceivedQuantity, TotalConsumedQauntity assumed mandatory for more robust CommTrack integration)

{ "requisitionId" : "123", "userId" : "CHW2", "products" :[ { "productCode" : "P", "quantityApproved" : "10", "remarks" : "Test" } { "productCode" : "P2", "quantityApproved" : "20", "remarks" : "Test1" } }] }

### HTTP Responses

- **200 OK** - All Indicates that the specified action was successfully completed.
- **401 Unauthorized** - Raised when the username-password combination incorrect.
- **400 Invalid data** - Indicates invalid data.
- **500 Internal Server Error** - Indicates that the server encountered an error while attempting to execute the desired action.
