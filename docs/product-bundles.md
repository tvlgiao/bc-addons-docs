# Product Bundles

![Product Bundles Demo](img/product-bundles-demo.gif)

## Install on your BigCommerce Store

Go to **Storefront** > **Script Manager**, click **Create a Script**, choose:

- **Location on page** = `Footer`
- **Select pages where script will be added** = `Store pages`
- **Script type** = `Script`

Enter the script below to **Scripts contents**: 


```html
<script>
    window.jQueryTheme = window.jQueryTheme || window.jQuerySupermarket || window.chiarajQuery || window.jQuery;
    window.PapaThemesProductBundlesSettings = {
        graphQLToken: '{{{settings.storefront_api.token}}}',
        currencyCode: '{{currency_selector.active_currency_code}}',
        showRating: {{settings.show_product_rating}}
    };
</script>
<script src="https://d3r059eq9mm6jz.cloudfront.net/microapps/product-bundles/main.YOURDOMAIN.js" async defer></script>
```

Replace `YOURDOMAIN` by your store's domain name, for example `example.com`. The complete URL should look like `https://d3r059eq9mm6jz.cloudfront.net/microapps/product-bundles/main.example.com.js`


<!--
Source code: https://github.com/tvlgiao/bc-bigcommerce-api-app/microapps/product-bundles/
-->

