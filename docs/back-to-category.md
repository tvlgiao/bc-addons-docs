# Add Back to Category button on the cart page

## Installation

Go to **Storefront** > **Script Manager**, click **Create a Script**, choose:

- **Location on page** = `Footer`
- **Select pages where script will be added** = `Store Pages`
- **Script type** = `Script`

Enter the script below to **Scripts contents**: 

```html
<script>
    window.PapathemesBackToCategorySettings = {
        pageType: '{{page_type}}'
    };
</script>
<script src="https://d3r059eq9mm6jz.cloudfront.net/microapps/back-to-category/main.YOURDOMAIN.js" async defer></script>
```

Replace `YOURDOMAIN` by your store's domain name, for example `marquis-wines.com`. The complete URL should look like `https://d3r059eq9mm6jz.cloudfront.net/microapps/back-to-category/main.marquis-wines.com.js`.


