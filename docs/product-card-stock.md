# Display Stock on Product Cards

## Install the script to your store

Go to **Storefront** > **Script Manager**, click **Create a Script**, choose:

- **Location on page** = `Footer`
- **Select pages where script will be added** = `Home Pages`
- **Script type** = `Script`

Enter the script below to **Scripts contents**: 

```html
<script>
    window.PapathemesProductCardStockSettings = {
        debug: true,
        graphQLToken: '{{settings.storefront_api.token}}'
    };
</script>
<script src="https://d3r059eq9mm6jz.cloudfront.net/microapps/product-card-stock/main.YOURDOMAIN.js" async></script>
```

Replace `YOURDOMAIN` by your store's domain name, for example `example.com`. The complete URL should look like `https://d3r059eq9mm6jz.cloudfront.net/microapps/product-card-stock/main.example.com.js`

## Settings

**Default settings:**

```js
{
    debug = false,
    graphQLToken = '',
    graphQLItemLimit = 50,
    productCardSelector = '.card',
    inStockMessage = 'stk pả lager',
    outOfStockMessage = 'Udsolgt',
    comingSoonMessage = 'Kommer Snart',
    iconBeforeMessage = `<span>&#9679;</span>`,
    findProductIdFunc = $card =>
        Number($card.data('entityId')) ||
        Number($card.find('[data-product-id]').data('productId')) ||
        Number(String($card.find('[href*="product_id="]').attr('href')).replace(/^.*product_id=([0-9]*).*$/i, '$1')) ||
        Number($card.find('input[name="product_id"]').first().val()),

    insertStock = ($card, html) => {
        if ($card.is('.card')) {
            const $stockLocation = $card.find('.card-body');
            $stockLocation.append(html);
        }
    },
}
```
