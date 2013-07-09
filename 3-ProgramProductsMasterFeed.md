# Program Product ATOM Feed

### Communication Type

- HTTP GET, Atom feed, published by OpenLMIS

### Parameters

- username - Mandatory (Post Request Header)
- password - Mandatory (Post Request Header)

### Feed Content

- productCode
- name
- description
- unit
- category
- programCode

### Notes

CommTrack will use this program-product data for supporting the replenishment process with Clinicians / CHWs, and submitting Reports to OpenLMIS. All products approved for a program will be avaliable to the CHW through OpenLMIS. CHWs inherit the facility type of their "home" or "base" facility, and the products made available to CHWs through their base facility can be further constrained within CommTrack. This approach can be revised once CommTrack introduces the notion of facility type.
