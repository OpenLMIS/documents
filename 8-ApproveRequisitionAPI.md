# Approve Requisition API Specifications

### Communication Type

- HTTP PUT, to OpenLMIS

### Parameters

- Authentication token (Base64 encrypted string containing username:password)
- requisitionID – Mandatory
- approverName – Mandatory
Products: Mandatory (Multiple records)  
    { ProductCode – Mandatory  
    approvedQuantity – Mandatory }  
 
 
### Return
ACCEPTED
{ productCode:   [not_active | not_supported_for_program | not_available_at_facility]
    productCode:   [not_active | not_supported_for_program | not_available_at_facility]
   . . . }
 
REJECTED   {invalid_credentials | mandatory_field_missing | invalid_requisitionID | already_approved | internal_server_error}
{ productCode:   [invalid_product_code |invalid_quantity]
  productCode:   [invalid_product_code |invalid_ quantity]
  . . . }
 
### Error scenarios 

- Invalid authentication
- Any mandatory field missing
- Invalid requisitionID
- Invalid "approvedQuantity"
- Already approved requisition.


### JSON Example 1 ( Below JSONs need to be updated)

(BeginningBalance, TotalReceivedQuantity, TotalConsumedQauntity assumed mandatory for more robust CommTrack integration)

    {
      "requisitionId":"123",
      "approverName":"Ahmed",
      "products":[
        {
          "productCode":"P",
          "approvedQuantity":"10",
        },
        {
          "productCode":"q",
          "approvedQuantity":"20",
        }
      ]
    }
