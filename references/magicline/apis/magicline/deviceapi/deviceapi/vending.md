# Vending

Here are all the endpoints that are necessary for `GenericVending` to be successfully used. This endpoints should be used for device with model `GENERIC_VENDING_READER`. The model can be found in response from `getDevices` which was already described in authentication process.

## Checks if customer is authorized to use vending device

 - [POST /open-api/device/vending/identification](https://redocly.sportalliance.com/apis/magicline/deviceapi/deviceapi/vending/vendingidentification.md): You can find more information about identification here.

## Product sale (dry-run possible)

 - [POST /open-api/device/vending/sale](https://redocly.sportalliance.com/apis/magicline/deviceapi/deviceapi/vending/vendingsale.md): This should be conducted post-identification with  in order to execute a dry-run, ensuring that customers can obtain the product, for example has enough credit, etc. If this first request was successful, the product can be dispensed. After the product was sucessfully dispensed, this endpoint needs to be called again with , which will subsequently lead to the customer being charged. You can find more information about sale here

## Top up customer's consumption credit

 - [POST /open-api/device/vending/revalue](https://redocly.sportalliance.com/apis/magicline/deviceapi/deviceapi/vending/vendingrevalue.md): This should be used to top up customer's consumption credit.

