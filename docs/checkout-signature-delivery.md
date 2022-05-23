# Add Signature on Delivery on Checkout Page

Automatically add **Signature on Delivery** custom product to cart if **Require signature on delivery** checkbox is selected or the total order amount exceeds a specified threshold.

## Install on your BigCommerce Store

Go to **Storefront** > **Script Manager**, click **Create a Script**, choose:

- **Location on page** = `Footer`
- **Select pages where script will be added** = `Checkout Page`
- **Script type** = `Script`

Enter the script below to **Scripts contents**: 


```html
<script>
    window.PapathemesCheckoutSignatureDeliverySettings = {
        storeHash: '{{settings.store_hash}}',
        checkoutId: '{{checkout.id}}',
        fieldId: 32,
        checkboxLabel: 'Request signature on delivery',
        freeSubTotal: 2500,
        productName: 'Signature on Delivery',
        productPrice: 5,
        productSku: '',
        confirmMsg: 'Are you sure you do not want signature on delivery?',
        confirmButtonText: 'No signature required',
        denyButtonText: 'Keep signature requirement'
    };
</script>
<script src="https://d3r059eq9mm6jz.cloudfront.net/microapps/checkout-signature-delivery/main.YOURDOMAIN.js" async defer></script>
```

Create an address custom field for **Request signature on delivery** checkbox.

Create and send us a v2/v3 API token wth OAuth Scopes:

- **Carts** = `Modify`
- **Information & settings** = `Read Only`
- **Sites & Routes** = `Ready Only`
- **Channel settings** = `Read Only`
- **Channel listings** = `Read Only`

<!--
Source code: https://github.com/tvlgiao/bc-bigcommerce-api-app/microapps/checkout-signature-delivery/
-->

