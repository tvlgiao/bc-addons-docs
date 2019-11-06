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
