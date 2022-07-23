# Product Card Lowest Price

Demo: <https://easybuyingredients.com/shop-all/>


## Install on your BigCommerce Store

Go to **Storefront** > **Script Manager**, click **Create a Script**, choose:

- **Location on page** = `Footer`
- **Select pages where script will be added** = `Store pages`
- **Script type** = `Script`

Enter the script below to **Scripts contents**:


```html
<script>
    window.PapathemesProductCardUnitPriceSettings = {
        graphQLToken: '{{{settings.storefront_api.token}}}',
        money: {{{json settings.money}}}
    };
</script>
<script src="https://d3r059eq9mm6jz.cloudfront.net/microapps/product-card-unit-price/main.YOURDOMAIN.js" async defer></script>
```

Replace `YOURDOMAIN` by your store's domain name, for example `example.com`. The complete URL should look like `https://d3r059eq9mm6jz.cloudfront.net/microapps/product-card-unit-price/main.example.com.js`


## Parameters

```js
window.PapathemesProductCardUnitPriceSettings = {
    debug = false,
    graphQLToken = '',
    graphQLItemLimit = 20,
    productCardSelector = '.card, [class*="sd-product-set-carousel"] > div > div > div',
    unitOptionNames = ['Weight'],
    unitPriceWithTaxHtml = `
        <div class="price-section price-section--unit price-section--withTax">
            <span class="price-label">From</span>
            <span data-product-price-with-tax= class="price price--withTax price--main">{price}</span><span class="price-label">/{unit}</span>
        </div>
    `,
    unitPriceWithoutTaxHtml = `
        <div class="price-section price-section--unit price-section--withoutTax">
            <span class="price-label">From</span>
            <span data-product-price-with-tax class="price price--withoutTax price--main">{price}</span><span class="price-label">/{unit}</span>
        </div>
    `,
    findProductIdFunc = $card =>
        Number($card.data('entityId')) ||
        Number($card.find('[data-product-id]').data('productId')) ||
        Number($card.find('[href*="product_id="]').attr('href').replace(/^.*product_id=([0-9]*).*$/i, '$1')),
    extractValueFunc = valueLabel => {
        const a = valueLabel.split(' ', 2).map(s => String(s).trim());
        return {
            number: Number(a[0]),
            unit: a[1],
        };
    },
    insertUnitPriceFunc = ($card, html) => {
        if ($card.is('.card')) {
            $card.find('.card-body [data-test-info-type="price"]').first().html('').append(html);
        } else {
            $card.append(html);
        }
    },
}
```
