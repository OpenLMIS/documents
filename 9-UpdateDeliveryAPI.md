# Confirm delivery API Specifications

### Communication Type

- HTTP PUT, to OpenLMIS

### Parameters

- Authentication token (Base64 encrypted string containing username:password)
- requisitionID – Mandatory
- Products:  - Mandatory - multiple records  
{  
    * ProductCode - Mandatory  
    * receivedQuantity - Mandatory  
}  
  
### Return
ACCEPTED

REJECTED   {invalid_credentials | mandatory_field_missing | invalid_requisitionID | already_received | internal_server_error | Malformed_JSON | Unrecognized_field }  
{   
   productCode:   [invalid_quantity | invalid_product_code]  
   productCode:   [invalid_quantity | invalid_product_code]  
   . . .    
}    
 
### Error scenarios 

- Invalid authentication
- Any mandatory field missing
- Invalid requisitionID
- Invalid "receivedQuantity"
- Already received.
- Malformed JSON
- Unrecognized field

### JSON Example 1 ( Below JSONs need to be updated)

(BeginningBalance, TotalReceivedQuantity, TotalConsumedQauntity assumed mandatory for more robust CommTrack integration)

    {
      "requisitionId":"123",
      "userId":"CHW2",
      "products":[
        {
          "productCode":"P",
          "receivedQuantity":"10",
        },
        {
          "productCode":"P2",
          "receivedQuantity":"20",
        }
      ]
    }
