# Get Requisition Details API Specifications

#### Communication Type

- HTTP GET on [/rest-api/requisitions/**\<requisitionId\>**](#)


#### Authentication
- [HTTP Basic Authentication](http://www.httpwatch.com/httpgallery/authentication/) (Base64 encoded string containing username:password)


#### Return

- id   
- agentCode
- programCode
- emergency { false | true }
- periodStartDate ( in ms format)   
- periodEndDate ( in ms format)  
- requisitionStatus  { INITIATED | SUBMITTED | AUTHORIZED | IN_APPROVAL | APPROVED | RELEASED }
- orderId  (null until the requisition has been released as an order)
- orderStatus (null until the requisition has been released as an order) { RELEASED | READY_TO_PACK | RECIEVED | IN_ROUTE | TRANSFER_FAILED | PACKED }
- supplyingFacilityCode (null until the requisition has been released as an order)   
- Products:  - multiple  records  
    {  
        * productCode   
        * beginningBalance - Non negative  
        * quantityReceived -  Non negative          
        * quantityDispensed - Non negative    
        * totalLossesAndAdjustments  
        * stockInHand - Non negative  
        * newPatientCount - Non negative  
        * stockOutDays - Non negative  
        * quantityRequested - Non negative  
        * reasonForRequestedQuantity  
        * calculatedOrderQuantity - Non negative   
        * quantityApproved - Non negative    
        * remarks   
    }  

#### Error scenarios

##### 1) *Invalid authentication*  
**Response**:    
{  
   "error": "Authentication Failed"  
}   
**Description**: This error can be caused by an incorrect API username or an incorrect API password.

##### 2) *Missing requisitionID*
**Response**:  
{    
   "error": "Request method 'GET' not supported"    
}    
**Description**: This error will occur if requisitionID is missing in the request URl

##### 3) *requisitionID Does Not Exist*
**Response**:  
{        
   "error": "Requisition Not Found"      
}  
  
**Description**: CommTrack stores the requisitionID which is returned in response of "submitreport" request on successful processing.This error will occur if requisitionID sent in the "RequisitionDetails" request is not a valid ID. 

##### 4) *Invalid requisitionID*
**Response**:  
{        
   "error": "Oops, something has gone wrong. Please try again later"      
}  
  
**Description**: CommTrack stores the requisitionID which is returned in response of "submitreport" request on successful processing.This error will occur if requisitionID sent in the "RequisitionDetails" request is not a valid type. 

##### 5) *Unrecognized Field*
**Response**:  
{        
   "error": "NOT_FOUND"      
}  
  
**Description**: This error will occur if URL contains unrequired/extra/wrong parameters.    


##### 6) *Internal server error*
**Response**:  
{        
   "error": "Something went wrong"      
}  
**Description**: This error will occur if request can not be processed due to some internal server error.


#### JSON Example -- Below JSON example needs to be updated
``` json
{
    "requisition":
    {
        "id":1,
        "programCode":"HIV",
        "agentCode":"F10",
        "emergency":false,
        "periodStartDate":1358274600000,
        "periodEndDate":1359570599000,
        "products":
            [
                {
                    "productCode":"P10",
                    "beginningBalance":3,
                    "quantityReceived":0,
                    "quantityDispensed":1,
                    "totalLossesAndAdjustments":-2,
                    "stockInHand":0,
                    "newPatientCount":2,
                    "stockOutDays":2,
                    "quantityRequested":3,
                    "reasonForRequestedQuantity":"reason",
                    "calculatedOrderQuantity":57,
                    "quantityApproved":65,
                    "remarks":"1"
                }
            ],
            "requisitionStatus":"RELEASED",
            "orderId":1,"orderStatus":"RELEASED",
            "supplyingFacilityCode":"F10"
    }
}
```   
