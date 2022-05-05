# Product Card Badges

Display **Sale badge**, **Out of Stock badge** and **custom badges** taken from product custom fields (`__badge`) on every product cards created by **BigCommerce widgets** and **Klevu Search** app.

## Install on your BigCommerce Store

Go to **Storefront** > **Script Manager**, click **Create a Script**, choose:

- **Location on page** = `Footer`
- **Select pages where script will be added** = `Store pages`
- **Script type** = `Script`

Enter the script below to **Scripts contents**: 


```html
<script>
    window.PapathemesProductCardBadgesSettings = {
        graphQLToken: '{{{settings.storefront_api.token}}}'
    };
</script>
<script src="https://d3r059eq9mm6jz.cloudfront.net/microapps/product-card-badges/main.YOURDOMAIN.js" async defer></script>
```

Replace `YOURDOMAIN` by your store's domain name, for example `example.com`. The complete URL should look like `https://d3r059eq9mm6jz.cloudfront.net/microapps/product-card-badges/main.example.com.js`


<!--
Source code: https://github.com/tvlgiao/bc-bigcommerce-api-app/microapps/product-card-badges/
-->

