# Create selected product options link

Demo: <https://theme-demo-01.mybigcommerce.com/dining-table-set-folding-dining-room-table-set/>

## Installation

Go to **Storefront** > **Script Manager**, click **Create a Script**, choose:

- **Location on page** = `Footer`
- **Select pages where script will be added** = `Store Pages`
- **Script type** = `Script`

Enter the script below to **Scripts contents**: 

```html
<script>
    window.PapaThemesPreselectProductOptionLinkSettings = {
        productViewSelector: '.productView',
        debug: false,
        storeHash: '{{{settings.store_hash}}}',
        shareButtonTmpl: '<button class="button button--secondary" type="button" data-waiting-msg="Creating...">Share</button>',
        insertShareButtionFunc: (self) => $(self.shareButtonTmpl).insertAfter(self.$scope.find('form[data-cart-item-add]')),
        addToCartFormSelector: 'form[data-cart-item-add]',
        pathPrefix: 'product-quote/'
    };
</script>
<script src="https://d3r059eq9mm6jz.cloudfront.net/microapps/preselect-product-option-link/main.YOURDOMAIN.js" async defer></script>
```

Replace `YOURDOMAIN` by your store's domain name, for example `theme-demo-01.mybigcommerce.com`. The complete URL should look like `https://d3r059eq9mm6jz.cloudfront.net/microapps/back-to-category/main.theme-demo-01.mybigcommerce.com.js`.

### Create the API Access Key

Login to your BC admin panel with **store owner account**, go to Advanced Settings > API Accounts > Click **Create V2/V3 API Token** from **Create API Account** dropdown button.

In **OAuth Scopes**, choose:
- **Information & settings** = `Read-Only`.
- **Channel settings** = `Read-Only`.
- **Channel listings** = `Read-Only`.
- **Sites & Routes** = `Modify`.
- 
- Then click **Save** button.

Send us the API credential file to install it on our server.

