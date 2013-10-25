# Confirm delivery API Specifications

### Communication Type

- HTTP POST, to OpenLMIS

### Authentication

- Authentication token (Base64 encrypted string containing username:password)

### Parameters

- orderID – Mandatory
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

#### 2) "Permission denied"  
**Response**:    
{  
   "error": "User does not have permission"  
}   
**Description**: This error will occur if user does not have manage proof of delivery rights on a supplying facility to which the order in the request belongs.   

#### 3) *Any mandatory field missing*
**Response**:  
{    
   "error": "Missing mandatory fields"    
}    
**Description**: This error will occur if any of the manadatory field tag is missing, blank tag will be considered as invalid value (not missing value).

#### 4) *Invalid orderID*
**Response**:  
{        
   "error": "Invalid order ID"      
}  
  
**Description**: CommTrack stores the orderID which is conveyed as part of "Requisition status feed" and "Get requisition details" API. 

#### 5) *Negative receivedQuantity*
**Response**:  
{        
   "error": "Invalid received quantity"      
}   
  
**Description**: Received quantity should be a positive integer. This error will occur if the received quantity for a product is negative.

#### 6) *Invalid receivedQuantity*  
**Response**:  "Bad Request"  

  **Description**: Received quantity should be a positive integer. This error will occur if the received quantity is non numeric or not an integer.

#### 7) *Already Received*
**Response**:  
{        
   "error": "Delivery already confirmed"       
}    
**Description**: This error will occur if "updateDelivery" request is received with an order which has been already received. 

#### 8) *Invalid productCode*
**Response**:  
{  
    "error": "[dasa, sdad, ssd] Invalid product code"  
}     
**Description**: This error will occur if the productCode is not valid or does not exist in OpenLMIS.

#### 9) *Malformed JSON*
**Response**:   
{          
   "error": "Bad request"        
}   
**Description**: This error will occur if there is some formatting error in JSON.

#### 10) *Unrecognized field*
**Response**:  
{        
   "error": "Bad request"      
}  
**Description**: This error will occur if any unrecognized field (apart from fields mentioned in parameters) is sent as part of API.

#### 11) *Internal server error*
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

In above cases, openLMIS will simply persist the delivery details for products against the order ID.  

### JSON Example 

Note : Order ID need to be given in the API URL, example : http://10.15.6.33:9091/rest-api/pod/"orderID".json  
```xml
{ 
  "podLineItems" : [{
    "productCode" : "dasa",
    "quantityReceived" : "10"
  },{
    "productCode" : "sdad",
    "quantityReceived" : "222"
  },{
    "productCode" : "ssd",
    "quantityReceived" : "222"
  }]
}
```
