# Restrict Shipping Countries on Specific Products

![products-restrict-shipping-countries](img/products-restrict-shipping-countries.png)

This extension allows to restrict shipping countries on specific products. It also displays the shipping countries info on the product details page. It stops customer complete the checkout payment step if products cannot be shipped to the specific countries. You can configure the shipping countries per product level in product custom fields.

Does not require editing of your theme files. Works with all Stencil / Cornerstone based themes. The code is optimized, asynchronously loaded (parallel loaded), works fast and doesn't affect the speed of your website.

Demo: https://theme-demo-01.mybigcommerce.com/

## Install the script on your BigCommerce store

### Step 1: Install the script

Go to **Storefront** > **Script Manager**, click **Create a Script**, choose:

- **Location on page** = `Footer`
- **Select pages where script will be added** = `All Pages`
- **Script type** = `Script`

Enter the script below to **Scripts contents**: 

```html
<script>
    if (!window.jQueryTheme) window.jQueryTheme = window.chiarajQuery || window.jQuerySupermarket;
    window.PAPATHEMES_RESTRICT_PRODUCT_PURCHASE_BY_COUNTRY = {
        cartId: '{{cart_id}}',
        graphQLToken: '{{settings.storefront_api.token}}'
    };
</script>
<script src="https://papathemes.com/content/supermarket/addon.restrict-product-purchase-by-country.js" async defer></script>
```

## Settings

### cartId

- The cart ID.
- Value must be: `{{cart_id}}`

### productCustomField

- The custom field to read shipping countries. Field value contains country ISO 2-letters code, seperated by commas.
- Default: `__purchasable_countries`
- Example: Field name = `__purchasable_countries`, Field value = `US,VN`
  
- ### stateProductCustomField

- The custom field to read shipping states. Field value contains country ISO 2-letters code or state name, seperated by commas.
- Default: `__purchasable_states`
- Example: Field name = `__purchasable_states`, Field value = `GA,Geogia,AL,Alabama`

### graphQLToken

- GraphQL token string.
- Value must be: `{{settings.storefront_api.token}}`

### limitProductsPerQuery

- Limit number of products per graphQL request.
- Default: `50`

### flagImg

- Function to return country flag image URL.
- Default: `code => ``https://cdn11.bigcommerce.com/s-2tqgeqo45u/lib/flags/${code.toLowerCase()}.gif`` `

### dropdownTemplate

- The countries dropdown template to display on the PDP.
- Default:

```html
<div class="rppbc__shippingDropdown">
    <button type="button" class="_handler" data-rppbc-dropdown-toggle>This product ship to</button>
    <div class="_dropdown" data-rppbc-dropdown>
        <ul>
            <%#countries%>
                <li><img src="<%flag%>" alt="<%name%>"><%name%></li>
            <%/countries%>
            <%#states%>
                <li><%.%></li>
            <%/states%>
        </ul>
    </div>
</div>
```

### renderDropdownFunc

- The countries dropdown render function.
- Default: `($form, $dropdown) => $form.append($dropdown)`

### txtUnavailableShippingCountry

- Error message on checkout page.
- Default: `<strong>{name}</strong> cannot ship to <strong>{country}</strong>`

### txtUnavailableShippingState

- Error message on checkout page.
- Default: `<strong>{name}</strong> cannot ship to <strong>{state}</strong>`


## Edit Product

Edit your product, add a custom field with name = `__purchasable_countries`, value contains the shipping countries ISO 2-letters code, separated by commas. For example: `US,VN`.
Add a custom field with name = `__purchasable_states`, value contains the shipping states ISO 2-letters code or state name, separated by commas. For example: `GA,Alabama`. 

![products-restrict-shipping-countries-custom-fields](img/products-restrict-shipping-countries-custom-fields.png)

