# Prevent Purchase Low Stock Products

## Install on your BigCommerce Store

Go to **Storefront** > **Script Manager**, click **Create a Script**, choose:

- **Location on page** = `Footer`
- **Select pages where script will be added** = `Checkout Page`
- **Script type** = `Script`

Enter the script below to **Scripts contents**: 


```html
<script>
    window.jQueryTheme = window.jQueryTheme || window.jQuerySupermarket || window.chiarajQuery || window.jQuery;
    window.PapaThemesPreventPurchaseLowStockSettings = {
        debug: false,
        graphQLToken: '{{{settings.storefront_api.token}}}',
        deletedMsg: '{items} are no longer available and was removed from your cart!'
    };
</script>
<script src="https://d3r059eq9mm6jz.cloudfront.net/microapps/prevent-purchase-low-stock/main.YOURDOMAIN.js" async defer></script>
```

Replace `YOURDOMAIN` by your store's domain name, for example `lockertown.com`. The complete URL should look like `https://d3r059eq9mm6jz.cloudfront.net/microapps/variant-image-gallery/main.lockertown.com.js`


<!--
Source code: https://github.com/tvlgiao/bc-bigcommerce-api-app/microapps/prevent-purchase-low-stock/
-->

