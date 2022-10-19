# Checkout File Upload

This extension will add File Upload field on the checkout page.

## Installation

Go to **Storefront** > **Script Manager**, click **Create a Script**, choose:

- **Location on page** = `Footer`
- **Select pages where script will be added** = `All Pages`
- **Script type** = `Script`

Enter the script below to **Scripts contents**: 

```html
<script>
    window.PapathemesCheckoutFileUploadSettings = {
        debug: true,
        graphQLToken: '{{{settings.storefront_api.token}}}',
        checkoutId: '{{{checkout.id}}}',
        pageType: '{{page_type}}',
        customFieldNames: ['Prescription'],
        customFieldValueRegex: /yes|1|true/i,
        fileModifierNames: ['File Upload']
    };
</script>
<script src="https://d3r059eq9mm6jz.cloudfront.net/microapps/checkout-file-upload/main.YOURDOMAIN.js" async defer></script>
```

Replace `YOURDOMAIN` by your store's domain name, for example `nextdoormed.com`. The complete URL should look like `https://d3r059eq9mm6jz.cloudfront.net/microapps/checkout-file-upload/main.nextdoormed.com.js`

### Edit Upload File Product

Edit the product that holds the uploaded file:

- Create a custom field, for example: `Prescription` with value = `Yes`.
- Add a File Upload modifier name = `File Upload`.

## DEMO

1. Add [this product](https://theme-demo-01.mybigcommerce.com/file-upload-product/) to cart
2. Proceed to the checkout page. At the payment step, the file upload form will appear.



