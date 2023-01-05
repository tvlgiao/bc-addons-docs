# Bulk Pricing Variants (Alternative)

![Bulk pricing variants](img/bulk-pricing-variants.png)

Git: https://github.com/tvlgiao/bc-bigcommerce-api-app/microapps/bulk-pricing-variants

This extension displays all product variants and bulk pricing tiers in a table on PDP.



## Installation

Go to **Storefront** > **Script Manager**, click **Create a Script**, choose:

- **Location on page** = `Footer`
- **Select pages where script will be added** = `All pages`
- **Category type** = `Essential`
- **Script type** = `Script`

Enter the script below to **Scripts contents**:

```html
<script>
    window.PapathemesBulkPricingVariantsSettings = {
        graphQLToken: '{{{settings.storefront_api.token}}}',
        currencyCode: '{{currency_selector.active_currency_code}}',
        money: {{{json settings.money}}},
        displayTableFunc: function($table, $scope) {
            $scope.after($table);
        }
    };
    (function() {
        function loadMainScript() {
            window.jQueryTheme = window.jQueryTheme || window.jQuery;
            var js = document.createElement('script');
            js.src = 'https://d3r059eq9mm6jz.cloudfront.net/microapps/bulk-pricing-variants/main.YOURDOMAIN.js';
            js.async = true;
            js.defer = true;
            document.head.appendChild(js);
        }
        if (!window.jQueryTheme && !window.jQuery) {
            var jquery = document.createElement('script');
            jquery.src = 'https://code.jquery.com/jquery-3.4.1.min.js';
            jquery.integrity = 'sha256-CSXorXvZcTkaix6Yvo6HppcZGetbYMGWSFlBw8HfCJo=';
            jquery.crossOrigin = 'anonymous';
            jquery.async = true;
            jquery.defer = true;
            jquery.onload = loadMainScript;
            document.head.appendChild(jquery);
        } else {
            loadMainScript();
        }
    })();
</script>
```

Replace `YOURDOMAIN` by your domain name, for example `khardware.com`




