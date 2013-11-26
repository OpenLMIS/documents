# Approve Requisition API Specifications

### Communication Type

- HTTP PUT on [/rest-api/requisitions/{id}/approve](#)

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
```
{  
   "Requisition approved successfully"  
}  
```
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
**Description**: This error will occur if :-   
a) Requisition is not authorized or already approved or in a stage from which it can not be approved.   
b) Requisition does not belong to a virtual facility (CHW).   

#### 4) *Any mandatory field missing*
**Response**:  
```
{  
   "error": "Missing mandatory fields"  
}
```  
**Description**: This error will occur if any of the manadatory field is missing.

#### 5) *Invalid requisitionID*
**Response**:  
```
{        
   "error": "Requisition Not Found"      
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

#### 8) *Malformed JSON*
**Response**:  
```
{          
   "error": "Bad request"        
}  
```
**Description**: This error will occur if there is some formatting error in JSON.

#### 9) *Unrecognized field*
**Response**:  
```   
{        
   "error": "Bad request"      
}  
```
**Description**: This error will occur if any unrecognized field (apart from fields mentioned in parameters) is sent as part of API.

#### 10) *Internal server error*
**Response**:  
```
{        
   "error": "Something went wrong"      
}  
```
**Description**: This error will occur if request can not be processed due to some internal server error.   

#### Note  
The approve API should contain data for all the products that were ordered by the requisitioner. OpenLMIS will accept the approval requesr in following cases :-   
a) Product is inactive   
b) Program is inactive   

System will check only for products which were ordered in the requisition, current status of products will not matter.
 
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
