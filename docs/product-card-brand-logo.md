# Display Brand Logo on Product Cards

## Install on your BigCommerce Store

Go to **Storefront** > **Script Manager**, click **Create a Script**, choose:

- **Location on page** = `Head`
- **Select pages where script will be added** = `Store pages`
- **Script type** = `Script`

Enter the script below to **Scripts contents**: 


```html
<script>
    window.PapathemesProductCardBrandLogoSettings = {
        debug: false,
        graphQLToken: '{{{settings.storefront_api.token}}}',
        imgWidth: 100,
        imgHeight: 30
    };
</script>
<script src="https://d3r059eq9mm6jz.cloudfront.net/microapps/product-card-brand-logo/main.YOURDOMAIN.js" async></script>
```

Replace `YOURDOMAIN` by your store's domain name, for example `example.com`. The complete URL should look like `https://d3r059eq9mm6jz.cloudfront.net/microapps/product-card-brand-logo/main.example.com.js`

### Fix CLS issue

Go to **Storefront** > **Script Manager**, click **Create a Script**, choose:

- **Location on page** = `Head`
- **Select pages where script will be added** = `Store pages`
- **Script type** = `Script`

Enter the script below to **Scripts contents**:

```html
<script>
    // Fix CLS issues
    (function() {
        var style = document.createElement('style');
        style.innerHTML = '.card-text--brand { min-height: 30px }';
        document.head.appendChild(style);
    })();
</script>
```


<!--
Source code: https://github.com/tvlgiao/bc-bigcommerce-api-app/microapps/product-card-brand-logo/
-->

