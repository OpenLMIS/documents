# Update delivery API Specifications

### Communication Type

- HTTP PUT, to OpenLMIS

### Parameters

- username – Mandatory (Post Request Header)
- password  – Mandatory (Post Request Header)
- requisitionID – Mandatory

- Products:

  { ProductCode – Mandatory
    - receivedQuantity – Mandatory }
 
 
### Return
ACCEPTED

REJECTED   {invalid_credentials | mandatory_field_missing | invalid_requisitionID | already_received | internal_server_error}
{ productCode:   [invalid_quantity | invalid_product_code]
  productCode:   [invalid_quantity | invalid_product_code]
  . . . }
 
### Error scenarios 

- Invalid credentials
- Any mandatory field missing
- Invalid requisitionID
- Invalid "receivedQuantity"
- Already received.


### JSON Example 1 ( Below JSONs need to be updated)

(BeginningBalance, TotalReceivedQuantity, TotalConsumedQauntity assumed mandatory for more robust CommTrack integration)

    {
      "requisitionId":"123",
      "userId":"CHW2",
      "products":[
        {
          "productCode":"P",
          "quantityReceived":"10",
        },
        {
          "productCode":"P2",
          "quantityReceived":"20",
        }
      ]
    }
