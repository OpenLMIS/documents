# Submit Requisition API Specifications

#### Communication Type

- HTTP POST on [/rest-api/requisitions](#)  

#### Authentication
- [HTTP Basic Authentication](http://www.httpwatch.com/httpgallery/authentication/) (Base64 encoded string containing username:password)

#### Parameters
- agentCode - Mandatory
- programCode - Mandatory
- products: - Mandatory - multiple records  
[
      * productCode - Mandatory  
      * beginningBalance  
      * quantityReceived  
      * quantityDispensed  
      * newPatientCount
      * stockOnHand - (stockOnHand is mandatory if other quantity fields are not provided)
      * stockOutDays
      * quantityRequested  
      * reasonForRequestedQuantity  
      * remarks  
}  

### Return

###### Success
```json
{  
   "requisitionId": 3  
}
```

###### Error scenarios

#### 1) *Invalid authentication*  
**Response**:    
```json
{  
   "error": "Authentication Failed"  
}
```   
**Description**: This error can be caused by an incorrect API username or an incorrect API password. 

#### 2) *Any mandatory field missing*
**Response**:  
```json
{  
   "error": "Missing mandatory fields"  
}
```    
**Description**: This error will occur if any of the manadatory field tag is missing, blank tag will be considered as invalid value (not missing value).

#### 3) *User does not have permission*
**Response**:  
```json
{  
   "error": "User does not have permission"  
}
```    
**Description**: This error will occur if the user does not have create and authorize rights.

#### 4) *Invalid agentCode*
**Response**:  
```json
{  
   "error": "Invalid agent code"  
}
```      

**Description**: This error will occur if agentCode is not registered in OpenLMIS.  

#### 5) *Facility is inoperative*
**Response**:  
```json
{  
   "error": "Facility is inoperative"  
}
```      
**Description**: This error will occur if:-
a) Agent is inactive
b) Agent is disabled
c) Agent's parent is inactive
d) Agent's parent is disabled

#### 6) *Invalid program code*
**Response**:  
```json
{  
   "error": "Invalid program code"  
}  
```

**Description**: This error will occur if programCode is invalid or does not exist in OpenLMIS.

#### 7) *Program is not supported*
**Response**:  
```json
{  
   "error": "User does not have permission"  
}  
```

**Description**: This error will occur if:-
a) Program is not supported by agent
b) Program is not active at agent
c) Program is globally inactive

#### 8) *Program configuration missing*
**Response**:  
```json
{  
   "error": "Program configuration missing"  
}  
```

**Description**: This error will occur if:-
a) Current period/schedule is not defined
b) Current date is before the program start date

#### 9) *Requisition template not configured*
**Response**:  
```json
{  
   "error": "Please contact admin to define R&R template for this program."  
}  
```

**Description**: This error will occur if requisiton template is not configured

#### 10) *Invalid productCode*
**Response**:  
{        
   "error": "Invalid productCode {P1,P2}"    
}   
**Description**: This error will occur if the productCode is not valid or does not exist in OpenLMIS or is inactive or not supported by the CHW.

#### 11) *Invalid dataType*
**Response**:  
{        
   "error": "R&R has errors, please correct them to proceed"
}  
  
**Description**: Data type for each quantity is mentioned in parameter list. This error will occur if the value of a quantity for a product is invalid.

####12) *Violation of template configuration"*
**Response**:  
{        
   "error": "R&R has errors, please correct them to proceed"
}  
  
**Description**: This error will occur if :-   
a) The stock in hand data provided is violating the arithmetic calculations.  
b) Mandatory fields (set in master template) are not provided in the API.  

#### 13) *Malformed JSON*
**Response**:   
{          
   "error": "Bad request"        
}   
**Description**: This error will occur if there is some formatting error in JSON.

#### 14) *Unrecognized field*
**Response**:  
{        
   "error": "Bad request"      
}  
**Description**: This error will occur if any unrecognized field (apart from fields mentioned in parameters) is sent as part of API.

#### 15) *Internal server error*
**Response**:  
{        
   "error": "Something went wrong"      
}  
**Description**: This error will occur if request can not be processed due to some internal server error.

### Notes
- If a field is configured as "Calculated" in the master template of a program, OpenLMIS will always overwrite the reported value with the calculated value.   
- If a field is configured as "Hidded" in the master template of a program, OpenLMIS will ignore the reported value.
- agentCode is for CHW or Clinician submitting the Report.   
- CommTrack will retain the RequisitionID generated for each Report submitted to OpenLMIS.
- OpenLMIS has macro-level requirements regarding the inclusion of some subset of beginningBalance, quantityDispensed, quantityReceived, and stockInHand values to support the reorder calculations. Individual Programs can be configured with combinations to suit their operating scenarios, provided they properly support the reorder calculations. FOR OUR COMMTRACK-OPENLMIS INTEGRATION, STOCKINHAND IS SUFFICIENT TO SUPPORT THE REORDER CALCULATIONS.

### JSON 

    {
      "agentCode":"CHW1",
      "programId":"2",
      "products":[
        {
          "productCode":"EM1",
          "beginningBalance":3,
          "stockOnHand":1,
          "quantityDispensed":1,
          "quantityReceived":0,
          "newPatientCount":2,
          "stockOutDays":2,
          "quantityRequested":3,
          "reasonForRequestedQuantity":"reason",
          "remarks":"1"
        },
        {
          "productCode":"EM2",
          "stockOnHand":10,
        }
    }


