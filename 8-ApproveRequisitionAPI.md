
# Approve Requisition API Specifications

### Communication Type

- HTTP PUT, to OpenLMIS

### Parameters

- username – Mandatory (Post Request Header)
- password  – Mandatory (Post Request Header)
- requisitionID – Mandatory
- approverName – Mandatory
Products:
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

- Invalid credentials
- Any mandatory field missing
- Invalid requisitionID
- Invalid "approvedQuantity"
- Already approved requisition.


### JSON Example 1 ( Below JSONs need to be updated)

(BeginningBalance, TotalReceivedQuantity, TotalConsumedQauntity assumed mandatory for more robust CommTrack integration)

    {
      "requisitionId":"123",
      "userId":"CHW2",
      "products":[
        {
          "productCode":"P",
          "quantityApproved":"10",
          "remarks":"Test"
        },
        {
          "productCode":"P2",
          "quantityApproved":"20",
          "remarks":"Test1"
        }
      ]
    }
