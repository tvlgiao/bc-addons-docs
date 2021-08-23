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
    window.PapaThemesHidePriceSettings = {
        priceSelector = '.price-section, [data-test-id="product-widget-price"], [data-test-id="product-set-widget-price"]',
        loginHtml = `<span class='login_msg_prod'><a href='/login.php'>Login</a> or <a href='/login.php?action=create_account'>Sign Up</a> to see price</span>`,
    }
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

  
### Example configuration for beautysolutions

Edit your custom script as below:

```html
<script>
    {{#or (unless customer) (if customer.customer_group_name '===' 'Guests')}}
    window.PapaThemesHidePriceSettings = {
        priceSelector: '[data-test-id="product-widget-price"], [data-test-id="product-set-widget-price"]',
        loginHtml: '<span class="login_msg_prod"><a href="/login.php">Login</a> or <a href="/login.php?action=create_account">Sign Up</a> to see price</span>'
    };
    var script = document.createElement('script');
    script.src = 'https://d3r059eq9mm6jz.cloudfront.net/microapps/hide-price/main.YOURDOMAIN.js';
    document.head.appendChild(script);
    var style = document.createElement('style');
    style.innerHTML = '.login_msg_prod { color: #232323 }';
    document.head.appendChild(style);
    {{/or}}
</script>
```

Replace `YOURDOMAIN` by your store's domain name, for example `devtestent.beautysolutions.com`. The complete URL should look like `https://d3r059eq9mm6jz.cloudfront.net/microapps/hide-price/main.devtestent.beautysolutions.com.js`


