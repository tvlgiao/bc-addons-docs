# Sell Products By Pack

This addon allows to sell products per pack, suitable wholesale purchases.

![bc-sell-by-pack-demo](img/bc-sell-by-pack-demo.gif)

## Install on your BigCommerce Store

1. Go to **Storefront** > **Script Manager**, click **Create a Script**, choose:

- **Location on page** = `Footer`
- **Select pages where script will be added** = `All pages`
- **Script type** = `Script`

Enter the script below to **Scripts contents**: 

```html
<script>
    window.jQueryTheme = window.jQueryTheme || window.jQuerySupermarket || window.chiarajQuery || window.jQuery || window.$;
    window.PapathemesSellByPackSettings = {
        // Add the addon settings here:
        stepCustomFieldName: 'Step',

        // End.
        cartId: '{{card_id}}'
    };
</script>
<script src="//papathemes.com/content/sellbypackaddon/sellbypack.YOURDOMAIN.js" async></script>
```

Replace `YOURDOMAIN` by your store's domain name.

2. Edit your product, add a custom field with name = **Pack** and value is the number of pieces you sell per pack:

![edit-custom-field-sell-by-pack](img/edit-custom-field-sell-by-pack.png)


## Configuration

Below are available configuration variables and the default values:

**Basic Settings:**

- `stepCustomFieldName = 'Step'`: Input the custom field name which has custom field value is quantity step. For example, custom field is `Step` and value = `10` to sell the product every 10 pcs.

**Advanced Settings for custom themes:**

- `qtyChangeSelector = '[data-quantity-change]'`: The quantity input CSS selector.
- `notQtyChangeSelector = '[data-also-bought] [data-quantity-change]'`: filter elements are not quantity input.
- `productViewSelector = '.productView'`: Product view CSS selector.
- `customFieldRowSelector = '[class*=productView-info-row]'`: Custom field row CSS selector.
- `customFieldNameSelector = '.productView-info-name'`: Custom field name CSS selector.
- `customFieldValueSelector = '.productView-info-value'`: Custom field value CSS selector.
- `incBtnSelector = '[data-action="inc"]'`: Increase button CSS selector.
- `decBtnSelector = '[data-action="dec"]'`: Decrease button CSS selector.
- `formSelector = 'form[data-cart-item-add]'`: Add to Cart Form CSS selector.
- `productIdInputSelector = 'input[name="product_id"]'`: The hidden product_id input selector.
- `cartQtyInputSelector = '[data-cart-content] input[name^="qty-"]'`: Quantity input selector on the cart page.
- `cartQtyIdRegExp = /^qty-(.*)/`: RegExp to find product item ID in the cart.
- `cartQtyBtnSelector = '[data-action]'`: Quantity increase/decrease buttons selector.
- `cartOverlaySelector = '[data-cart] .loadingOverlay'`: Cart overlay selector.
- `productViewTemplate = 'products/product-view'`: Product view template file.


