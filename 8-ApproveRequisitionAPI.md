# Approve Requisition API Specifications

### Communication Type

- HTTP PUT on [/rest-api/requisitions/{id}/approve(#)

### Authentication

- Authentication token (Base64 encrypted string containing username:password)

#### Parameters

- Products
{  
    * ProductCode - Mandatory  
    * quantityApproved - Mandatory  
}  

## Return

### Success
{  
   "Success": "Success message"  
}  

### Error scenarios 

#### 1) *Invalid authentication*  
**Response**:  
```   
{   
   "error": "Authentication Failed"  
}    
```   
**Description**: This error can be caused by an incorrect API username or an incorrect API password. 

#### 2) *User does not have permission*  
**Response**:    
```
{        
   "error": "User does not have permission"  
}   
```  
**Description**: This error will occur if the user does not have approve requisition rights on the corresponding node on which requisition is pending for approval.

#### 3) *requisition is not ready for approval*  
**Response**:   
``` 
{  
   "error": "Approval not allowed"  
}  
```    
**Description**: This error will occur if requisition is not authorized or already approved or in a stage from which it can not be approved.

#### 4) *Any mandatory field missing*
**Response**:  
```json
{  
   "error": "Missing mandatory fields"  
}
```  
**Description**: This error will occur if any of the manadatory field is missing.

#### 5) *Invalid requisitionID*
**Response**:  
```
{        
   "error": "Invalid requisitionID"      
}  
```  
**Description**: CommTrack stores the requisitionID which is returned in response of "submitreport" request on successful processing.This error will occur if requisitionID sent in the "approveRequisition" request is not a valid ID. 

#### 6) *Product count mismatch*
**Response**:  
```
{        
   "error": "Products do not match with requisition"      
}  
```  
**Description**: This error will occur if number of products in aprroval request does not match with the requested products.


#### 7) *Invalid product code*
**Response**: 
``` 
{
   "error":"Invalid product codes [P1000]"   
}
```     
**Description**: This error will occur if product is not present in the system or was not ordered in the requisition.   

#### 8) *Already Approved*
**Response**:  
```
{        
   "error": "Requisition already Approved"       
}  
```   
**Description**: A requisition can be approved only once. This error will occur if "approveRequisition" request is received with a requisitionID which has been already approved. 

#### 9) *Malformed JSON*
**Response**:  
```
{          
   "error": "Bad request"        
}  
```
**Description**: This error will occur if there is some formatting error in JSON.

#### 10) *Unrecognized field*
**Response**:  
```   
{        
   "error": "Bad request"      
}  
```
**Description**: This error will occur if any unrecognized field (apart from fields mentioned in parameters) is sent as part of API.

#### 11) *Internal server error*
**Response**:  
{        
   "error": "Something went wrong"      
}  
**Description**: This error will occur if request can not be processed due to some internal server error.   

#### Note  
The approve API should contain data for all the products that were ordered by the requisitioner.
 
### JSON Example 
```
{   
   "products":[
   {
     "productCode":"P333",
     "quantityApproved":"10"
   },
   {
     "productCode":"P456",
     "quantityApproved":"20"
   }
 ]
}
```
