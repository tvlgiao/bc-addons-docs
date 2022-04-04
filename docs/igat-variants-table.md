# IGAT Variants Table

![igat-variants-table](img/igat-variants-table.png)

## Install on your BigCommerce Store

Go to **Storefront** > **Script Manager**, click **Create a Script**, choose:

- **Location on page** = `Footer`
- **Select pages where script will be added** = `Store Pages`
- **Script type** = `Script`

Enter the script below to **Scripts contents**: 


```html
<script>
    window.jQueryTheme = window.jQueryTheme || window.jQuerySupermarket || window.chiarajQuery || window.jQuery;
    window.PapaThemesIgatVariantsTableSettings = {
        graphQLToken: '{{{settings.storefront_api.token}}}'
    };
    </script>
</script>
<script src="https://d3r059eq9mm6jz.cloudfront.net/microapps/igat-variants-table/main.YOURDOMAIN.js" async defer></script>
```

Replace `YOURDOMAIN` by your store's domain name, for example `igat-snc-di-gatto-pietro-c-store-2.mybigcommerce.com`. The complete URL should look like `https://d3r059eq9mm6jz.cloudfront.net/microapps/igat-variants-table/main.igat-snc-di-gatto-pietro-c-store-2.mybigcommerce.com.js`


## Configuration

### Quantity increment

To limit the quantity of products purchased by pack, for example 10, 20, 30, 40, or 50, edit your product and set the **Minimum Purchase Quantity** to `10`, then create a custom field named `__pack` with a value of `10`.




<!--
Source code: https://github.com/tvlgiao/bc-bigcommerce-api-app/microapps/igat-variants-table/
-->

  