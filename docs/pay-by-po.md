# Pay by PO

**Note:** moved https://github.com/tvlgiao/bc-paybypo-dev to **bigcommerce-api-app/microapps/paybypo**

```
<script type="application/json" id="PAPATHEMESPAYBYPO_cartId">{{{JSONstringify cart_id}}}</script>
<script type="application/json" id="PAPATHEMESPAYBYPO_config">
{
    "customerFieldPayByPOLabel": "Pay by PO Allowed",
    "customerFieldPayByPOValue": "Yes",
    "allowCustomerGroup": "",
    "payByPOPaymentMethodName": "Pay by PO",
    "poNumberField": "PO Number"
}
</script>
<script data-dev-src="http://localhost:5173/src/main.js" data-dev-type="module" src="https://d3r059eq9mm6jz.cloudfront.net/microapps/paybypo/index.papathemes-app-sandbox.mybigcommerce.com.js" defer async></script>
```

More docs here: https://bc-supermarket-docs.papathemes.com/faqs#display-pay-by-po-payment-method-for-certain-customers-on-the-checkout-page
