# Confirm delivery API Specifications

### Communication Type

- HTTP PUT, to OpenLMIS

### Authentication

- Authentication token (Base64 encrypted string containing username:password)

### Parameters

- requisitionID – Mandatory
- Products:  - Mandatory - multiple records  
{  
    * ProductCode - Mandatory  
    * receivedQuantity - Mandatory  
}  
  
### Return

{  
"Success": "Success message"  
}  

### Error scenarios 

#### 1) *Invalid authentication*  
**Response**:    
{  
   "error": "Authentication Failed"  
}   
**Description**: This error can be caused by an incorrect API username or an incorrect API password. 

#### 2) *Any mandatory field missing*
**Response**:  
{    
   "error": "Mandatory field Missing"    
}    
**Description**: This error will occur if any of the manadatory field tag is missing, blank tag will be considered as invalid value (not missing value).

#### 3) *Invalid requisitionID*
**Response**:  
{        
   "error": "Invalid requisitionID"      
}  
  
**Description**: CommTrack stores the requisitionID which is returned in response of "submitreport" request on successful processing.This error will occur if requisitionID sent in the "updateDelivery" request is not a valid ID. 

#### 4) *Invalid receivedQuantity*
**Response**:  
{        
   "error": [ {"productCode1: Invalid receivedQuantity"},  
              {"productCode2: Invalid receivedQuantity"}  
            ......]  
}  
  
**Description**: Received quantity should be an integer. This error will occur if the received quantity for a product is not an integer.

#### 5) *Already Received*
**Response**:  
{        
   "error": "Requisition already Received"       
}    
**Description**: This error will occur if "updateDelivery" request is received with a requisition which has been already received. 

#### 6) *Invalid productCode*
**Response**:  
{        
   "error":  [ {"productCode1: Invalid productCode"},  
              {"productCode2: Invalid productCode"}  
            ......]        
}   
**Description**: This error will occur if the productCode is not valid or does not exist in OpenLMIS.

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

### JSON Example 1 ( Below JSONs need to be updated)

(BeginningBalance, TotalReceivedQuantity, TotalConsumedQauntity assumed mandatory for more robust CommTrack integration)

    {
      "requisitionId":"333",
      "userId":"CHW2",
      "products":[
        {
          "productCode":"P123",
          "receivedQuantity":"10",
        },
        {
          "productCode":"P456",
          "receivedQuantity":"20",
        }
      ]
    }
