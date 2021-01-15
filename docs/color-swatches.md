# Display color swatches / image swatches on product card items

![card-color-swatches](img/card-color-swatches.gif)

This **product color swatches add-on** allows to display color swatches or product image swatches on product card items on Homepage, category pages, brands pages or any pages where product cards appear. It loads the swatches from your product attributes automatically, no extra input required.

The add-on also supports changing product image and price when a color swatch is selected.

## Install the script on your BigCommerce store

Go to **Storefront** > **Script Manager**, click **Create a Script**, choose:

- **Location on page** = `Footer`
- **Select pages where script will be added** = `All pages`
- **Script type** = `Script`

Enter the script below to **Scripts contents**: 

```html
<script>if (!window.jQuery) window.jQuery = window.jQuerySupermarket || window.jQueryTheme;</script>
<script src="//papathemes.com/content/productswatchesaddon/productswatches.YOURDOMAIN.js" async></script>
```

Replace `YOURDOMAIN` by your own store domain. Example:

```html
<script>if (!window.jQuery) window.jQuery = window.jQuerySupermarket || window.jQueryTheme;</script>
<script src="https://papathemes.com/content/productswatchesaddon/productswatches.fivebrotherworkwear.com.js" async></script>
```

Example with custom CSS and using GraphQL for faster performance:

```html
<script>
    window.PAPATHEMES_PRODUCTSWATCHESADDON = {
        productIdSelector: '.quickview, .quickview-alt, [data-product-id]',
        graphQLToken: '{{settings.storefront_api.token}}'
    };
</script>
<script type="text/plain" id="papathemes_productswatchesaddon_css">
	.productSwatches-attributes { -webkit-overflow-scrolling: touch; overflow: auto }
	.productSwatches-attributes::-webkit-scrollbar { display: none; }
    .productSwatches-swatches { display: inline-flex; flex-wrap: nowrap; justify-content: flex-start; margin: 0 auto; }
	@media (max-width: 800px) {
    	.productSwatches-attributes { height: 26px; }
    }
	@media (min-width: 801px) {
    	.productSwatches-attributes { height: 16px; }
        .productSwatches-swatches-item .form-option-variant--color,
        .productSwatches-swatches-item .form-option-variant--pattern { width: 12px; height: 12px; }
    }
</script>
<script>
    (function() {
        var style = document.createElement('style');
        style.innerHTML = document.getElementById('papathemes_productswatchesaddon_css').innerHTML;
        document.head.appendChild(style);
    })();
</script>
<script>if (!window.jQuery) window.jQuery = window.jQuerySupermarket || window.jQueryTheme;</script>
<script src="https://papathemes.com/content/productswatchesaddon/productswatches.solartown.com.js" async></script>
```


### Install when your site has no jQuery

If your site has no jQuery declared globally, add the line below to the top:

```html 
<script
src="https://code.jquery.com/jquery-3.4.1.min.js"
integrity="sha256-CSXorXvZcTkaix6Yvo6HppcZGetbYMGWSFlBw8HfCJo="
crossorigin="anonymous">
```

Completed code example:

```html
<script
src="https://code.jquery.com/jquery-3.4.1.min.js"
integrity="sha256-CSXorXvZcTkaix6Yvo6HppcZGetbYMGWSFlBw8HfCJo="
crossorigin="anonymous">
<script>if (!window.jQuery) window.jQuery = window.jQuerySupermarket || window.jQueryTheme;</script>
<script src="https://papathemes.com/content/productswatchesaddon/productswatches.fivebrotherworkwear.com.js" async></script>
```
