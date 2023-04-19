# Minimum Order Amount & Minimum Category / Brand Quantity & Total Amount

## Install on your BigCommerce Store

Navigate to **Storefront** > **Script Manager**, click **Create a Script**, and choose:

- **Location on page** = `Footer`
- **Select pages where script will be added** = `All Pages`
- **Script type** = `Script`

Enter the script below in the **Script contents** section:

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
        minimumErrorMsg: 'Minimum product quantity of "%category%" category is %min%',
        minimumAmountByCategory: {},
        minimumAmountByCategoryErrorMsg: 'Minimum order amount of "%category%" category is $%min%',
        minimumAmountByBrand: {},
        minimumAmountByBrandErrorMsg: 'Minimum order amount of "%brand%" brand is $%min%',
        cartCheckoutActionSelector: '.previewCartAction-checkout, .previewCartAction-checkoutMultiple, .previewCart-additionalCheckoutButtons, .previewCartCheckout-checkoutButton, .previewCartCheckout-additionalCheckoutButtons, .cart-actions .button--primary, .card-actions .checkoutMultiple, .cart-additionalCheckoutButtons',
        watchingElementSelector: '#checkout-app, [data-cart-content] [data-cart-quantity], [data-cart-preview] [data-cart-quantity], .previewCart',
        cartStatusSelector: '[data-cart-status]',
        disableProcessOrderButtonOnly: false,
        watchingPaymentFormSelector: '[data-test="payment-form"]'
    };
</script>
<script src="https://d3r059eq9mm6jz.cloudfront.net/microapps/category-minimum-quantity/main.YOURDOMAIN.js" async defer></script>
```

Replace `YOURDOMAIN` with your store's domain name, for example `example.com`. The complete URL should look like `https://d3r059eq9mm6jz.cloudfront.net/microapps/category-minimum-quantity/main.example.com.js`

## Usage

### Limit minimum order amount for the whole cart

To limit minimum order amount for the whole cart, set `minimumAmount` to the minimum amount you want to limit. For example, if you want to limit minimum order amount to `$100`, set `minimumAmount` to `100`.

```js
minimumAmount: 0,
```

### Limit minimum quantity of products per categories

To limit minimum quantity of products per categories, set `minimumQuantityByCategory` to the minimum quantity you want to limit. For example, if you want to limit minimum quantity of products in category ID `110` to `2` and category ID `112` to `4`, set `minimumQuantityByCategory` to:

```js
minimumQuantityByCategory: {
    110: 2,
    112: 4
},
```

### Limit minimum order amount per categories

To limit minimum order amount per categories, set `minimumAmountByCategory` to the minimum amount you want to limit. For example, if you want to limit minimum order amount of products in category ID `110` to `$100` and category ID `112` to `$200`, set `minimumAmountByCategory` to:


```js
minimumAmountByCategory: {
    110: 100,
    112: 200
},
```

### Limit minimum order amount per brands

To limit minimum order amount per brands, set `minimumAmountByBrand` to the minimum amount you want to limit. For example, if you want to limit minimum order amount of products in brand `ashanks` to `$100` and brand `bluedio` to `$200`, set `minimumAmountByBrand` to:

```js
minimumAmountByBrand: {
    'ashanks': 100,
    'bluedio': 200
},
```



<!--
Source code: https://github.com/tvlgiao/bc-bigcommerce-api-app/microapps/minimum-category-quantity/
-->

