# Add Additional Product To Cart Automatically

This addon allows to add an additional product to cart when a product is added to cart with a specific product option is selected. The additional product cannot be removed when the main product still exists in the cart.

![auto-add-product-to-cart-demo](img/auto-add-product-to-cart-demo.gif)



## Install on your BigCommerce Store


Go to **Storefront** > **Script Manager**, click **Create a Script**, choose:

- **Location on page** = `Footer`
- **Select pages where script will be added** = `All pages`
- **Script type** = `Script`

Enter the script below to **Scripts contents**: 

```html
<script>
    window.jQueryTheme = window.jQueryTheme || window.jQuerySupermarket || window.jQuery;
    window.PapathemesAutoAddToCartSettings = {
        conditions: [
            {
                productId: '',
                optionMatch: '',
                optionValueMatch: 'Including $400 Refundable Core Charge Deposit.',
                productIdToAdd: 378,
            }
        ],
        cartId: '{{cart_id}}'
    };
</script>
<script src="//papathemes.com/content/autoaddtocartaddon/autoaddtocart.YOURDOMAIN.js" async></script>
```

Replace `YOURDOMAIN` by your store's domain name.


### Configuration

- `productId`: Input a product ID if you want to apply for a specific product only.
- `optionMatch`: Input the option name to process only when this option is selected.
- `optionValueMatch`: Input the option value to process only when this option value is selected.
- `productIdToAdd`: Input the additional product ID to add to cart.

