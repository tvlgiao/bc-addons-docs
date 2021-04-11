# Sell Products By Pack

This addon allows to sell products per pack, suitable wholesale purchases.

![bc-sell-by-pack-demo](img/bc-sell-by-pack-demo.gif)

## Install on your BigCommerce Store

Go to **Storefront** > **Script Manager**, click **Create a Script**, choose:

- **Location on page** = `Footer`
- **Select pages where script will be added** = `All pages`
- **Script type** = `Script`

Enter the script below to **Scripts contents**: 

```html
<script>
    window.jQueryTheme = window.jQueryTheme || window.jQuerySupermarket || window.chiarajQuery || window.jQuery || window.$;
    window.PapathemesSellByPackSettings = {
        stepCustomFieldName: 'Step',
        graphQLToken: '{{settings.storefront_api.token}}'
    };
</script>
<script src="//papathemes.com/content/sellbypackaddon/sellbypack.YOURDOMAIN.js" async></script>
```

Replace `YOURDOMAIN` by your store's domain name.

## Edit product

Edit your product, add a custom field with name = **Step** and value is the number of items sell per pack:

![edit-custom-field-sell-by-pack](img/edit-custom-field-sell-by-pack.png)

Update **Minimum Purchase Quantity** to be equal the number of items sell per pack.

### Configure quantity per variant SKUs


Enter the custom field value, for example: `200,SKU-E23036E2:100,SKU-62C208F5:125,SKU-65D30EBC:150`

- First value is the default number of items per pack (`200`)
- Variant SKU (`SKU-E23036E2`) and the coresponding number of items per pack (`100`) separated by colon (`:`).
- Each variant/pack is separated by a commas (`,`).


## Settings

Available settings and default values are listed below:

**Basic Settings:**

- `stepCustomFieldName = 'Step'`: Input the custom field name which has custom field value is quantity step. For example, custom field is `Step` and value = `10` to sell the product every 10 pcs.
- `minQtyIsStep = true`: Specify minimum quantity  equal the step value.
- `graphQLToken = '{{settings.storefront_api.token}}'`

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


## Misc

- Mod for Camden theme: https://github.com/tvlgiao/bc-sellbypack-ilighting-camden-theme

