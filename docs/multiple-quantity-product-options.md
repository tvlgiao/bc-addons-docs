# Multiple Quantity Product Options

This extension will replace BigCommerce's default product options or products pick list to a child products list with ability to select quantity and add products to cart at the same time. Similar the grouped products feature in Magento or WooCommerce.

![mqpo-demo](img/mqpo-demo.gif)

## Install on your BigCommerce store


Go to **Storefront** > **Script Manager**, click **Create a Script**, choose:

- **Location on page** = `Footer`
- **Select pages where script will be added** = `All pages`
- **Script type** = `Script`

Enter the script below to **Scripts contents**: 

```html
<script>
    window.jQueryTheme = window.jQueryTheme || window.jQuerySupermarket || window.jQuery;
    window.PapathemesMultiQtyProductOptionsSettings = {
        fields: [
            {
                name: 'Add Remote',
                productIds: []
            }
        ],
        cartId: '{{cart_id}}'
    };
</script>
<script src="//papathemes.com/content/multiqtyproductoptions/multi-qty-product-options.YOURDOMAIN.js" async></script>
```

Replace `YOURDOMAIN` by your domain name, for example: `mystore.com`.


**Configuration:**

- `fields`:
  + `name`: is your product option name or label.
  + `productIds`: array of product IDs to enable MQPO for this product option. Please `[]` to apply for all products.
- `cartId`: Is your cart object ID, leave it unchanged as above configuration.


**Other optional configuration:**

```js
productOptionsSelector = '[data-product-option-change]',
optionLabelSelector = 'label:not([for])',
formFieldSelector = '.form-field[data-product-attribute]',
quantityFormFieldSelector = '.form-field--increments',
productIdSelector = 'input[name=product_id]',
productOptionsListSelector = '.productOptions-list',
productListTemplate = `
    <div class="mqpo-productsList">
        <%#list%>
        <div class="_item" data-mqpo-attribute-item>
            <%#imgTag%><div class="_img" data-img><%&.%></div><%/imgTag%>
            <div class="_title" data-name><%name%></div>
            <div class="_price"><span class="price price--withTax" data-mqpo-price-with-tax></span></div>
            <div class="_qty">
                <div class="form-increment" data-mqpo-quantity-change>
                    <button class="button button--icon" data-action="dec">
                        <span class="is-srOnly">Decrease Quantity:</span>
                        <i class="icon" aria-hidden="true"><svg><use xlink:href="#icon-keyboard-arrow-down"></use></svg></i>
                    </button>
                    <input class="form-input form-input--incrementTotal" id="qty_<%id%>" data-mqpo-attribute-id="<%attrId%>" data-mqpo-attribute-value="<%attrVal%>" type="tel" value="0" data-quantity-min="0" data-quantity-max="0" min="0" pattern="[0-9]*" aria-live="polite">
                    <button class="button button--icon" data-action="inc">
                        <span class="is-srOnly">Increase Quantity:</span>
                        <i class="icon" aria-hidden="true"><svg><use xlink:href="#icon-keyboard-arrow-up"></use></svg></i>
                    </button>
                </div>
            </div>
        </div>
        <%/list%>
    </div>`,
addedToCartMsgTemplate = `
    <div class="mqpo-addedToCartMsg-content">
        <div class="_msg"><%msg%></div>
        <ul class="_list">
            <%#list%>
                <li class="_item">
                    <%#imgTag%><div class="_img"><%&.%></div><%/imgTag%>
                    <div class="_title"><%name%></div>
                    <div class="_qty"><%qty%></div>
                </li>
            <%/list%>
        </ul>
        <div class="_actions">
            <a class="button button--primary" href="/checkout.php">Checkout Now</a>
            <a class="button" href="/cart.php">View your Cart</a>
        </div>
    </div>
`,
addedToCartMsgTitle = 'Added to your cart!',
```

**Example script for shoppartsland.com:**

```html
<script>
    window.jQueryTheme = window.jQueryTheme || window.jQuerySupermarket || window.jQuery;
    window.PapathemesMultiQtyProductOptionsSettings = {
        fields: [
            {
                name: 'Color',
                productIds: []
            }
        ],
        cartId: '{{cart_id}}'
    };
    (function() {
        var css = document.createElement('style');
        css.innerHTML = '.mqpo-productsList { font-size: 14px }';
        document.head.appendChild(css);
    })();
</script>
<script src="//papathemes.com/content/multiqtyproductoptions/multi-qty-product-options.shoppartsland.com.js" async></script>
```

## Configuration for product options table

![product-options-table](img/product-options-table.jpg)

```html
<script>
    window.jQueryTheme = window.jQueryTheme || window.jQuerySupermarket || window.jQuery;
    window.PapathemesMultiQtyProductOptionsSettings = {
        fields: [
            {
                name: ['Colour', 'Size'],
                productIds: []
            }
        ],
        cartId: '{{cart_id}}'
    };
</script>
<script src="//papathemes.com/content/multiqtyproductoptions/multi-qty-product-options.YOURDOMAIN.js" async></script>
```

- `name: ['Colour', 'Size']`: is an array of titles of 2 product options.
- `productIds: []`: is an array of the product IDs which enable this feature.


