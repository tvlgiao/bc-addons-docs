# Multi-Storefronts Universal Login Automatically

This addon allows customers log in to one store, will also log in to all other multi-stores using the same account. The Multi-Storefronts feature is available only to Enterprise accounts.

## Installation

Create an API key for BC API access by following this instruction: https://support.bigcommerce.com/s/article/Store-API-Accounts#creating

- Choose **Create V2/V3 API Token**.
- In **Oauth Scopes** choose:
    - **Customers**: `read-only`
    - **Customers Login**: `login`

Send us the Access Token, Client ID and Client Secret code to install on your database.

Go to **Channel Manager** > **Storefronts** > click **Scripts** on all stores, then click **Create a Script**, choose:

- **Location on page** = `Footer`
- **Select pages where script will be added** = `All Pages`
- **Script type** = `Script`

Enter the script below to **Scripts contents**: 

```html
<script>
    window.PapathemesMsfUniversalLoginSettings = {
        debug: true,
        urls: [
            'papathemes-app-sandbox.mybigcommerce.com',
            'papathemeappsandbox2-945366.mybigcommerce.com'
        ],
		storeHash: '{{{settings.store_hash}}}',
        customerId: '{{{customer.id}}}',
        channelId: '{{{settings.channel_id}}}'
    };
</script>
<script src="https://d3r059eq9mm6jz.cloudfront.net/microapps/back-to-category/main.YOURDOMAIN.js" async defer></script>
```

Replace `YOURDOMAIN` by your **primary store**'s domain name, for example `papathemes-app-sandbox.mybigcommerce.com`. The complete URL should look like `https://d3r059eq9mm6jz.cloudfront.net/microapps/back-to-category/main.papathemes-app-sandbox.mybigcommerce.com.js`.

Replace the domain list (`urls`) by your store's domains:

```js
'papathemes-app-sandbox.mybigcommerce.com',
'papathemeappsandbox2-945366.mybigcommerce.com'
```

Create the script again for each of your stores, but don't modify the primary store's domain.




