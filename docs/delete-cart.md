# Delete Cart

![delete cart](img/delete-cart.png)

This extension allows to remove all items in your store with just one click. It displays a **Remove all items** button on your shopping cart page. It's also position to display the button on any pages or any position.

Does not require editing of your theme files. Works with all Stencil / Cornerstone based themes. The code is optimized, asynchronously loaded (parallel loaded), works fast and doesn't affect the speed of your website.

Demo: https://theme-demo-01.mybigcommerce.com/


## Install the script on your BigCommerce store

### Step 1: Install the script

Go to **Storefront** > **Script Manager**, click **Create a Script**, choose:

- **Location on page** = `Footer`
- **Select pages where script will be added** = `Store Pages`
- **Script type** = `Script`

Enter the script below to **Scripts contents**: 

```html
<script>
    if (!window.jQueryTheme) window.jQueryTheme = window.chiarajQuery || window.jQuerySupermarket;
    window.PapathemesDeleteCartSettings = {
        // Required settings
        cartId: '{{cart_id}}',

        // Optional settings
        renderToSelector: '[data-cart-content]',
        renderType: 'after', // append|prepend|before|after
        txtDeleteAll: 'Remove all items',
        txtDeleting: 'Removing...',
        txtConfirmMsg: 'Are you sure you want to remove all items in your cart?',
        txtConfirmBtn: 'Remove All',
        txtCancelBtn: 'Cancel',
        redirectUrl: '/'
    };
</script>
<script src="https://papathemes.com/content/deletecartaddon/deletecart.YOURDOMAIN.js" async defer></script>

```

Replace `YOURDOMAIN` by your own store domain. Example:

```html
<script>
    if (!window.jQueryTheme) window.jQueryTheme = window.chiarajQuery || window.jQuerySupermarket;
    window.PapathemesDeleteCartSettings = {
        cartId: '{{cart_id}}'
    }
</script>
<script src="https://papathemes.com/content/deletecartaddon/deletecart.mydomain.com.js" async defer></script>
```


## Settings

All these settings are optional.

### renderToSelector

DOM selector of the element to render the button to.

### renderType

Render method. Valid value is: `append`, `prepend`, `before` or `after`.

### txtDeleteAll

The **Remove all items** button text.

### txtDeleting

The **Remove all items** button text when deleting.

### txtConfirmMsg

Confirmation message when click on the **Remove all items** button.

### txtConfirmBtn

Confirmation button text.

### txtCancelBtn

Cancel button text.

### redirectUrl

Redirect URL after removing all items successful.


