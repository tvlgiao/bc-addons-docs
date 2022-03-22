# Minimum Order Amount & Minimum Category Quantity

## Install on your BigCommerce Store

Go to **Storefront** > **Script Manager**, click **Create a Script**, choose:

- **Location on page** = `Footer`
- **Select pages where script will be added** = `Store pages`
- **Script type** = `Script`

Enter the script below to **Scripts contents**: 


```html
<script>
    window.jQueryTheme = window.jQueryTheme || window.jQuerySupermarket || window.chiarajQuery || window.jQuery;
    window.PapaThemesCategoryMinimumQuantitySettings = {
        debug: false,
        graphQLToken: '{{{settings.storefront_api.token}}}',
        apiUrl: '',
        useApi: false,
        storeHash: '{{{store_hash}}}',
        minimumAmount: 0,
        minimumAmountErrorMsg: 'Minimum order amount is $%min%',
        minimumQuantityByCategory: {},
        minimumErrorMsg: 'Minimum product quantity of %category% category is %min%',
        cartCheckoutActionSelector: '.previewCartAction-checkout, .previewCartAction-checkoutMultiple, .previewCart-additionalCheckoutButtons, .previewCartCheckout-checkoutButton, .previewCartCheckout-additionalCheckoutButtons, .cart-actions .button--primary, .card-actions .checkoutMultiple, .cart-additionalCheckoutButtons',
        watchingElementSelector: '#checkout-app, [data-cart-content] [data-cart-quantity], [data-cart-preview] [data-cart-quantity], .previewCart',
        cartStatusSelector: '[data-cart-status]'
    };
</script>
<script src="https://d3r059eq9mm6jz.cloudfront.net/microapps/category-minimum-quantity/main.YOURDOMAIN.js" async defer></script>
```

Replace `YOURDOMAIN` by your store's domain name, for example `example.com`. The complete URL should look like `https://d3r059eq9mm6jz.cloudfront.net/microapps/category-minimum-quantity/main.example.com.js`




<!--
Source code: https://github.com/tvlgiao/bc-bigcommerce-api-app/microapps/minimum-category-quantity/
-->

