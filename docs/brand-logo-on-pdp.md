# Display Brand Logo on Product Details Page

## Install the script to your store

Go to **Storefront** > **Script Manager**, click **Create a Script**, choose:

- **Location on page** = `Footer`
- **Select pages where script will be added** = `Store Pages`
- **Script type** = `Script`

Enter the script below to **Scripts contents**: 

```html
<script>
    window.PAPATHEMES_BRANDLOGOV2_SETTINGS = {
        debug: true,
        graphQLToken: '{{settings.storefront_api.token}}'
    };
</script>
<script src="https://d3r059eq9mm6jz.cloudfront.net/brand-logo-v2.public.js" async defer></script>
```

## Settings

**Default settings:**

```js
{
    debug = false,
    graphQLToken = '',
    productViewSelector = '.productView',
    getProductIdFunc = $productView => Number($productView.find('input[name=product_id]').filter((i, el) => $(el).closest('[data-also-bought]').length === 0).val()),
    brandImageWidth = 100,
    brandImageHeight = 50,
    brandImageTemplate = `
        <img class="_brandImg" src="<%img%>" alt="<%alt%>">
    `,
    renderBrandImageFunc = ($productView, html) => {
        $productView.find('.productView-brand a').prepend(html);
    },
}
```
