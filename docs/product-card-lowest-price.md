# Product Card Lowest Price

## Install on your BigCommerce Store

Go to **Storefront** > **Script Manager**, click **Create a Script**, choose:

- **Location on page** = `Footer`
- **Select pages where script will be added** = `Store pages`
- **Script type** = `Script`

Enter the script below to **Scripts contents**: 


```html
<script>
    window.jQueryTheme = window.jQueryTheme || window.jQuerySupermarket || window.chiarajQuery || window.jQuery;
    window.PapaThemesProductCardLowestPriceSettings = {
        debug: true,
        graphQLToken: '{{{settings.storefront_api.token}}}',
        graphQLItemLimit: 20,
        productCardSelector: '.card, [class*="sd-product-set-carousel"] > div > div > div',
        lowestPriceHtml: '<p class="card-text card-txt--lowestPrice">As low as <strong>{price}</strong> (calculated price @ {label} discount value)</p>',
        includeTax: true,
        excludeExtraLowestPriceCustomFields: [],
        extraPercentOff: 0
    };
</script>
<script src="https://d3r059eq9mm6jz.cloudfront.net/microapps/product-card-lowest-price/main.YOURDOMAIN.js" async defer></script>
```

Replace `YOURDOMAIN` by your store's domain name, for example `example.com`. The complete URL should look like `https://d3r059eq9mm6jz.cloudfront.net/microapps/variant-image-gallery/main.example.com.js`


### Example scripts for onlineworkwear.com.au

```html
<script>
    window.jQueryTheme = window.jQueryTheme || window.jQuerySupermarket || window.chiarajQuery || window.jQuery;
    window.PapaThemesProductCardLowestPriceSettings = {
        debug: true,
        graphQLToken: '{{{settings.storefront_api.token}}}',
        graphQLItemLimit: 20,
        productCardSelector: '.card, [class*="sd-product-set-carousel"] > div > div > div',
        lowestPriceHtml: '<p class="card-text card-txt--lowestPrice" style="font-size: 13px; margin-bottom: 36px; color: #000">As low as <strong>{price}</strong> (calculated price @ {label} discount value)</p>',
        includeTax: true,
        excludeExtraLowestPriceCustomFields: ['__bulk-price'],
        extraPercentOff: 20
    };
</script>
<script src="https://d3r059eq9mm6jz.cloudfront.net/microapps/product-card-lowest-price/main.onlineworkwear.com.au.js" async defer></script>
```


<!--
Source code: https://github.com/tvlgiao/bc-bigcommerce-api-app/microapps/product-card-lowest-price/
-->

