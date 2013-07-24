# Submit Requisition API Specifications

### Communication Type

- HTTP Post, to OpenLMIS

### Parameters

- Authentication token (Base64 encrypted string containing username:password)
- agentCode - Mandatory
- programCode - Mandatory
- periodId - Optional
- reportType - Mandatory { Regular | Emergency }
- products: - Mandatory - multiple records  
  {  
      * productCode - Mandatory  
      * beginningBalance - Optional - Non negative  
      * quantityReceived - Optional - Non negative  
      * quantityDispensed - Optional - Non negative  
      * lossesAndAdjustments - Optional  
      * newPatientCount - Optional
      * stockOnHand - Optional - Non negative (stockOnHand is mandatory if other quantity fields are not provided)
      * stockOutDays - Optional - Non negative  
      * quantityRequested - Optional - Non negative  
      * reasonForRequestedQuantity - Optional  
      * remarks - Optional  
}  

### Return

- requisitionId on successful submission

### Error scenarios

- Invalid authentication
- Any mandatory field missing
- Invalid agentCode
- Invalid programCode
- Invalid productCode - Requisition is rejected
- Product is not active - Replenishment quantity set to 0
- Product is not supported for that program - Ignore
- Product is not supported by CHW's base facility - Ignore
- Invalid data type - Requisition is rejected
- Internal Server Error - Indicates that the server encountered an error while attempting to execute the desired action.
- Malformed JSON
- Unrecognized field

### Responses

ACCEPTED  
requisitionID  
{ productCode:   [not_active | not_supported_for_program | not_available_at_facility]  
   productCode:   [not_active | not_supported_for_program | not_available_at_facility]  
   . . . }  
 
REJECTED   {invalid_credentials | invalid agentCode | mandatory_field_missing | internal_server_error | Malformed_JSON | Unrecognized_field}  
{ productCode:   [invalid_product_code |invalid_quantities]  
  productCode:   [invalid_product_code |invalid_quantities]  
  . . . }  


### Notes

- agentCode is for CHW or Clinician submitting the Report.
- CommTrack will retain the RequisitionID generated for each Report submitted to OpenLMIS.
- Parameter names are case-insensitive.
- OpenLMIS has macro-level requirements regarding the inclusion of some subset of beginningBalance, quantityDispensed, quantityReceived, and stockInHand values to support the reorder calculations. Individual Programs can be configured with combinations to suit their operating scenarios, provided they properly support the reorder calculations. FOR OUR COMMTRACK-OPENLMIS INTEGRATION, STOCKINHAND IS SUFFICIENT TO SUPPORT THE REORDER CALCULATIONS.

### JSON Example 1

(BeginningBalance, TotalReceivedQuantity, TotalConsumedQauntity assumed mandatory for more robust CommTrack integration)

    {
      "agentCode":"CHW1",
      "programId":"2",
      "periodId":"2",
      "reportType":"Regular",
      "products":[
        {
          "productCode":"EM1",
          "beginningBalance":3,
          "stockOnHand":1,
          "quantityDispensed":1,
          "quantityReceived":0,
          "lossesAndAdjustments":[
            {
              "type":{
                "name":"TRANSFER\_OUT"
              },
              "quantity":2
            }
          ],
          "stockInHand":0,
          "approvedQuantity":65,
          "newPatientCount":2,
          "stockOutDays":2,
          "quantityRequested":3,
          "reasonForRequestedQuantity":"reason",
          "remarks":"1"
        },
        {
          "productCode":"EM2",
          "beginningBalance":3,
          "quantityDispensed":1,
          "quantityReceived":0,
          "lossesAndAdjustments":[
            {
              "type":{
                "name":"TRANSFER\_OUT",
                "additive":"false"
              },
              "quantity":2
            }
          ],
          "stockOnHand":0,
          "approvedQuantity":65,
          "newPatientCount":2,
          "stockOutDays":2,
          "quantityRequested":3,
          "reasonForRequestedQuantity":"reason",
          "remarks":"1"
        },
        {
          "productCode":"EM3",
          "beginningBalance":3,
          "quantityDispensed":1,
          "quantityReceived":0,
          "lossesAndAdjustments":[
            {
              "type":{
                "name":"TRANSFER\_OUT",
                "additive":"false"
              },
              "quantity":2
            }
          ],
          "stockOnHand":0,
          "approvedQuantity":65,
          "newPatientCount":2,
          "stockOutDays":2,
          "quantityRequested":3,
          "reasonForRequestedQuantity":"reason",
          "remarks":"1"
        }
      ]
    }

### JSON Example 2

(stockInHand assumed mandatory for the basic CommTrack integration)

    {
      "facilityId":"",
      "programId":"",
      "periodId":"",
      "userId":"",
      "products":[
        {
          "productCode":"",
          "stockOnHand":"0",
          "lossesAndAdjustments":[
            {
              "type":{
                "name":"TRANSFER\_OUT"
              },
              "quantity":2
            }
          ],
          "newPatientCount":"0",
          "stockOutDays":"2"
        }
      ]
    }

