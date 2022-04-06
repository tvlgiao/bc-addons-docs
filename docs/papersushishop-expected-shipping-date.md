# Papersushishop Expected Shipping Date

This extension enables administrators to specify the expected shipping date for any order.

## Installation

Go to **Advanced Settings** > **Account Signup Form**, in **Address Fields** tab, click **Create a New Field**, then choose **Date Field** in the dropdown. Enter **Field Name** = `Expected Shipping Date`.

Go to **Storefront** > **Script Manager**, click **Create a Script**, choose:

- **Location on page** = `Footer`
- **Select pages where script will be added** = `Checkout`
- **Script type** = `Script`

Enter the script below to **Scripts contents**: 

```html
<script>
    window.PapathemesPapersushishopExpectedShippingDate = {
        fieldName: 'Expected Shipping Date'
    };
</script>
<script src="https://d3r059eq9mm6jz.cloudfront.net/microapps/papersushishop-expected-shipping-date/main.YOURDOMAIN.js" async defer></script>
```

Replace `YOURDOMAIN` by your store's domain name, for example `papersushishop.com`. The complete URL should look like `https://d3r059eq9mm6jz.cloudfront.net/microapps/microapps/papersushishop-expected-shipping-date/main.papersushishop.com.js`

