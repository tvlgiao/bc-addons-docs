# Image Gallery for Product Options

## Install on your BigCommerce Store

Go to **Storefront** > **Script Manager**, click **Create a Script**, choose:

- **Location on page** = `Footer`
- **Select pages where script will be added** = `Store Pages`
- **Script type** = `Script`

Enter the script below to **Scripts contents**: 


```html
<script>
    window.jQueryTheme = window.jQueryTheme || window.chiarajQuery || window.jQuery;
    window.PapaThemesVariantImageGallerySettings = {
        debug: true,
        graphQLToken: '{{settings.storefront_api.token}}'
    }
</script>
<script src="https://d3r059eq9mm6jz.cloudfront.net/microapps/variant-image-gallery/main.YOURDOMAIN.js" async defer></script>
```

Replace `YOURDOMAIN` by your store's domain name, for example `lockertown.com`. The complete URL should look like `https://d3r059eq9mm6jz.cloudfront.net/microapps/variant-image-gallery/main.lockertown.com.js`


## Edit product images

Upload all images for the product options in Product Images. Edit the product images, append `|` and the option value to the description field of each product images, For example: `| Red`

![edit-product-image-variant](img/edit-product-image-variant.jpg)


<!--
Source code: https://github.com/tvlgiao/bc-bigcommerce-api-app/microapps/variant-image-gallery/
-->

  