# Get Requisition Details API Specifications

### Communication Type

- GET, to OpenLMIS

### Authentication

- Authentication token (Base64 encrypted string containing username:password)

### Parameters

- requisitionId - Mandatory

### Return

- agentCode - Mandatory
- programCode - Mandatory
- periodID - Optional
- requisitionStatus  { Submitted | Authorized | In Approval | Approved | Released }
- orderID  (null until the requisition has been released as an order)
- orderStatus   { Released | Packed | Received }
- Products:  - Mandatory - multiple  records  
    {  
        * productCode - Mandatory   
        * beginningBalance - Optional - Non negative  
        * quantityReceived - Optional - Non negative          
        * quantityDispensed - Optional - Non negative    
        * lossesAndAdjustments - Optional  
        * stockOnHand - Optional - Non negative  
        * newPatientCount - Optional - Non negative  
        * stockOutDays - Optional - Non negative  
        * quantityRequested - Optional - Non negative  
        * reasonForRequestedQuantity - Optional  
        * calculatedQuantity - Mandatory  
        * approvedQuantity - Optional  
        * shippedQuantity - Optional  
        * receivedQuantity - Optional  
        * remarks - Optional   
    }  

### Error scenarios

#### 1) *Invalid authentication*  
**Response**:    
{  
   "error": "Authentication Failed"  
}   
**Description**: This error can be caused by an incorrect API username, an incorrect API password, or an invalid API signature. Make sure that all three of these values are correct.

#### 2) *Any mandatory field missing*
**Response**:  
{    
   "error": "Mandatory field Missing"    
}    
**Description**: This error will occur if any of the manadatory field is either null or tag is missing.

#### 3) *Invalid requisitionID*
**Response**:  
{        
   "error": "Invalid requisitionID"      
}  
  
**Description**: CommTrack stores the requisitionID which is returned in response of "submitreport" request on successful processing.This error will occur if requisitionID sent in the "RequisitionDetails" request is not a valid ID. 

#### 4) *Malformed JSON*
**Response**:   
{          
   "error": "Bad request"        
}   
**Description**: This error will occur if there is some formatting error in JSON.

#### 5) *Unrecognized field*
**Response**:  
{        
   "error": "Bad request"      
}  
**Description**: This error will occur if any unrecognized field (apart from fields mentioned in parameters) is sent as part of API.

#### 6) *Internal server error*
**Response**:  
{        
   "error": "Something went wrong"      
}  
**Description**: This error will occur if request can not be processed due to some internal server error.


### JSON Example -- Below JSON example needs to be updated

    {
      "rnr":{
        "id":1,
        "modifiedBy":3,
        "modifiedDate":1369984377779,
        "facilityId":1,
        "programId":2,
        "period":2,
        "status":"IN_APPROVAL",
        "fullSupplyLineItems":[
          {
            "id":1,
            "modifiedBy":3,
            "modifiedDate":1369984377782,
            "rnrId":1,
            "product":"ACETYL SALICYLIC ACID, TAB 300MG Capsule 300/200/600 mg",
            "productDisplayOrder":4,
            "productCode":"EM1",
            "productCategory":"Anaesthetics",
            "productCategoryDisplayOrder":4,
            "roundToZero":false,
            "packRoundingThreshold":1,
            "packSize":10,
            "dosesPerMonth":30,
            "dosesPerDispensingUnit":10,
            "dispensingUnit":"Strip",
            "maxMonthsOfStock":3,
            "fullSupply":true,
            "quantityReceived":1,
            "quantityDispensed":1,
            "beginningBalance":1,
            "totalLossesAndAdjustments":0,
            "stockInHand":1,
            "stockOutDays":0,
            "newPatientCount":0,
            "amc":0,
            "normalizedConsumption":1,
            "calculatedOrderQuantity":0,
            "maxStockQuantity":0,
            "quantityApproved":0,
            "packsToShip":0,
            "previousStockInHandAvailable":false,
            "price":"50.00"
          },
          {
            "id":2,
            "modifiedBy":3,
            "modifiedDate":1369984377786,
            "rnrId":1,
            "product":"AMOXYCILLIN (TRIHYDRATE), CAP 250MG Capsule 300/200/600 mg",
            "productDisplayOrder":5,
            "productCode":"EM2",
            "productCategory":"Anaesthetics",
            "productCategoryDisplayOrder":4,
            "roundToZero":true,
            "packRoundingThreshold":1,
            "packSize":10,
            "dosesPerMonth":30,
            "dosesPerDispensingUnit":10,
            "dispensingUnit":"Strip",
            "maxMonthsOfStock":3,
            "fullSupply":true,
            "quantityReceived":7,
            "quantityDispensed":7,
            "beginningBalance":7,
            "totalLossesAndAdjustments":0,
            "stockInHand":7,
            "stockOutDays":0,
            "newPatientCount":0,
            "amc":2,
            "normalizedConsumption":7,
            "calculatedOrderQuantity":0,
            "maxStockQuantity":6,
            "quantityApproved":0,
            "packsToShip":0,
            "previousStockInHandAvailable":false,
            "price":"50.00"
          },
          {
            "id":3,
            "modifiedBy":3,
            "modifiedDate":1369984377789,
            "rnrId":1,
            "product":"BENZATHINE BENZYL PENICILLIN , 2.4MU, PWD FOR INJ Capsule 300/200/600 mg",
            "productDisplayOrder":5,
            "productCode":"EM3",
            "productCategory":"Anaesthetics",
            "productCategoryDisplayOrder":4,
            "roundToZero":false,
            "packRoundingThreshold":1,
            "packSize":10,
            "dosesPerMonth":30,
            "dosesPerDispensingUnit":10,
            "dispensingUnit":"Strip",
            "maxMonthsOfStock":3,
            "fullSupply":true,
            "quantityReceived":4,
            "quantityDispensed":4,
            "beginningBalance":4,
            "totalLossesAndAdjustments":0,
            "stockInHand":4,
            "stockOutDays":0,
            "newPatientCount":0,
            "amc":1,
            "normalizedConsumption":4,
            "calculatedOrderQuantity":0,
            "maxStockQuantity":3,
            "quantityApproved":0,
            "packsToShip":0,
            "previousStockInHandAvailable":false,
            "price":"50.00"
          }
        ],
        "nonFullSupplyLineItems":[
   
        ],
        "submittedDate":1369984328023,
        "comments":[
   
        ]
      }
    }
   
