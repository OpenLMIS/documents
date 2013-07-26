# Submit Requisition API Specifications

### Communication Type

- HTTP Post, to OpenLMIS

### Authentication

- Authentication token (Base64 encrypted string containing username:password)

### Parameters

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

#### 1) *Invalid authentication*  
**Response**:    
{  
   "error": "Could not authenticate Vendor"  
}   
**Description**: This error can be caused by an incorrect API username or an incorrect API password. 

#### 2) *Any mandatory field missing*
**Response**:  
{    
   "error": "Mandatory field Missing"    
}    
**Description**: This error will occur if any of the manadatory field tag is missing, blank tag will be considered as invalid value (not missing value).

#### 3) *Invalid agentCode*
**Response**:  
{  
   "error": "Invalid agentCode"  
}  
**Description**: This error will occur if:-   
a) agentCode is not registered in OpenLMIS.  
b) agentCode is not a virtual facility in OpenLMIS (Update cannot be made on regular OpenLMIS facilities).

#### 4) *Invalid programCode*
**Response**:  
{  
   "error": "Invalid programCode"  
}  
**Description**: This error will occur if programCode is invalid or does not exist in OpenLMIS.

#### 5) *Invalid productCode*
**Response**:  
{        
   "error":  [ {"productCode1: Invalid productCode"},  
              {"productCode2: Invalid productCode"}  
            ......]        
}   
**Description**: This error will occur if the productCode is not valid or does not exist in OpenLMIS.

#### 6) *Invalid dataType*
**Response**:  
{        
   "error": [ {"productCode1: Invalid quantities"},  
              {"productCode2: Invalid quantities"}  
            ......]  
}  
  
**Description**: Data type for each quantity is mentioned in parameter list. This error will occur if the value of a quantity for a product is invalid.

#### 7) *Malformed JSON*
**Response**:   
{          
   "error": "Bad request"        
}   
**Description**: This error will occur if there is some formatting error in JSON.

#### 8) *Unrecognized field*
**Response**:  
{        
   "error": "Bad request"      
}  
**Description**: This error will occur if any unrecognized field (apart from fields mentioned in parameters) is sent as part of API.

#### 9) *Internal server error*
**Response**:  
{        
   "error": "Something went wrong"      
}  
**Description**: This error will occur if request can not be processed due to some internal server error.

#### Note
No error for following cases :-  
- Product is not active - Replenishment quantity set to 0 (No error returned)
- Product is not supported for that program - Ignore
- Product is not supported by CHW's base facility - Ignore

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

