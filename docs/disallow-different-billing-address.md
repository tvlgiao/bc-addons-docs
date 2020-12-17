# Disallow billing address not match shipping address

## Install on your BigCommerce store

Go to **Storefront** > **Script Manager**, click **Create a Script**, choose:

- **Location on page** = `Footer`
- **Select pages where script will be added** = `Checkout`
- **Script type** = `Script`

Enter the script below to **Scripts contents**: 

```html
<script>
    window.PAPATHEMES_DDBA = {
        cartId: {{{JSONstringify cart_id}}}
    };
</script>
<script src="//papathemes.com/content/supermarket/addon.disallow-different-billing-address.js" async></script>
```

