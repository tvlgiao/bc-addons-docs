# Hide Price for Non-Logged In Customers

## Install on your BigCommerce Store

Go to **Storefront** > **Script Manager**, click **Create a Script**, choose:

- **Location on page** = `Head`
- **Select pages where script will be added** = `Store Pages`
- **Script type** = `Script`

Enter the script below to **Scripts contents**: 


```html
<script>
    {{#unless customer}}
    var script = document.createElement('script');
    script.src = 'https://d3r059eq9mm6jz.cloudfront.net/microapps/hide-price/main.YOURDOMAIN.js';
    document.head.appendChild(script);
    {{/unless}}
</script>
```

Replace `YOURDOMAIN` by your store's domain name, for example `devtestent.beautysolutions.com`. The complete URL should look like `https://d3r059eq9mm6jz.cloudfront.net/microapps/hide-price/main.devtestent.beautysolutions.com.js`


<!--
Source code: https://github.com/tvlgiao/bc-bigcommerce-api-app/microapps/hide-price/
-->

  