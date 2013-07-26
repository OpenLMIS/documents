# Approve Requisition API Specifications

### Communication Type

- HTTP PUT, to OpenLMIS

### Authentication

- Authentication token (Base64 encrypted string containing username:password)

### Parameters

- requisitionID – Mandatory
- approverName – Mandatory
- Products:  - Mandatory - multiple records  
{  
    * ProductCode - Mandatory  
    * approvedQuantity - Mandatory  
}  

## Return

### Success
{  
   "Success": "Success message"  
}  

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

#### 3) *Invalid requisitionID*
**Response**:  
{        
   "error": "Invalid requisitionID"      
}  
  
**Description**: CommTrack stores the requisitionID which is returned in response of "submitreport" request on successful processing.This error will occur if requisitionID sent in the "approveRequisition" request is not a valid ID. 

#### 4) *Invalid approvedQuantity*
**Response**:  
{        
   "error": [ {"productCode1: Invalid approvedQuantity"},  
              {"productCode2: Invalid approvedQuantity"}  
            ......]  
}  
  
**Description**: Approved quantity should be a non-negative integer. This error will occur if the approved quantity for a product is not a non-negative integer.

#### 5) *Already Approved*
**Response**:  
{        
   "error": "Requisition already Approved"       
}    
**Description**: A requisition can be approved only once. This error will occur if "approveRequisition" request is received with a requisitionID which has been already approved. 

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
No error will be returned for following cases :-  
- Product is not active - Replenishment quantity set to 0 (No error returned)
- Product is not supported for that program - Ignore
- Product is not supported by CHW's base facility - Ignore
 
### JSON Example 1 ( Below JSONs need to be updated)

(BeginningBalance, TotalReceivedQuantity, TotalConsumedQauntity assumed mandatory for more robust CommTrack integration)

    {
      "requisitionId":"123",
      "approverName":"Ahmed",
      "products":[
        {
          "productCode":"P333",
          "approvedQuantity":"10",
        },
        {
          "productCode":"P456",
          "approvedQuantity":"20",
        }
      ]
    }
