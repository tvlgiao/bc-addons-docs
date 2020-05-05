# Product Pick List Price

This addon shows price, SKU, stock number and stock message on every product pick list item on product details page.

## Install on your BigCommerce store

Go to **Storefront** > **Script Manager**, click **Create a Script**, choose:

- **Location on page** = `Footer`
- **Select pages where script will be added** = `All pages`
- **Script type** = `Script`

Enter the script below to **Scripts contents**: 

```html
<script>
    window.jQueryTheme = window.jQueryTheme || window.jQuerySupermarket || window.jQuery;
    window.window.PapathemesProductPickListPriceSettings = {};
</script>
<script src="//papathemes.com/content/productpicklistprice/product-pick-list-price.YOURDOMAIN.js" async></script>
```

Replace `YOURDOMAIN` by your domain name, for example: `mystore.com`.


## Configuration

```js
window.window.PapathemesProductPickListPriceSettings = {
    addToCartFormSelector: 'form[data-cart-item-add]',
    productOptionsSelector: '[data-product-option-change]',
    productPickListOptionsSelector: '[data-product-attribute="product-list"]',
    labelSelector: 'label',
    productIdSelector: 'input[name="product_id"]',
    parallelRequests: 3,
    list: [
        {
            name: '',
            productIds: []
        }
    ],
    template = `
        <div class="pplp__item" data-pplp-item>
            <span class="price price--withTax" data-pplp-price-with-tax style="display:none"></span> <span class="_price-label" data-pplp-price-with-tax-label style="display:none">(Incl. <span data-pplp-tax-label></span>)</span>
            <span class="price price--withoutTax" data-pplp-price-without-tax style="display:none"></span> <span class="_price-label" data-pplp-price-without-tax-label style="display:none">(Excl. <span data-pplp-tax-label></span>)</span>
            <span class="_sku-label" data-pplp-sku-label style="display:none">SKU:</span> <span class="_sku-value" data-pplp-sku style="display:none"></span>
            <span class="_stock-label" data-pplp-stock-label style="display:none">Stock:</span> <span class="_stock-value" data-pplp-stock style="display:none"></span>
            <span class="_stock-msg" data-pplp-stock-message style="display:none"></span>
        </div>
    `,
    renderFunc: ($input, _template) => {
        const $el = $input.parent();
        if ($el.find('[data-pplp-item]').length === 0) {
            $el.append(_template);
        }
        return $el.find('[data-pplp-item]');
    }
};
```

