# Category Minimum Quantity Setup - hornlegend.com

## Overview

This script enforces minimum order quantities per product category on your store:

- **Group 1 Automotive - Polos** (`/group-1-automotive-polos/`): minimum **24** items
- **Group 1 Automotive - Pullovers** (`/group-1-automotive-pullovers/`): minimum **12** items

Customers will not be able to checkout until the minimum quantity is met for each category. An error message will be displayed on the cart and checkout pages.

## Installation Steps

1. In your BigCommerce admin, navigate to **Storefront** > **Script Manager**
2. Click **Create a Script**
3. Configure the script settings:
   - **Name of script** = `Category Minimum Quantity`
   - **Location on page** = `Footer`
   - **Select pages where script will be added** = `All Pages`
   - **Script type** = `Script`

4. Paste the following code into the **Script contents** box:

```html
<script>
    window.jQueryTheme = window.jQueryTheme || window.jQuerySupermarket || window.chiarajQuery || window.jQuery;
    window.PapaThemesCategoryMinimumQuantitySettings = {
        graphQLToken: '{{{settings.storefront_api.token}}}',
        minimumQuantityByCategory: {
            2201: 24,
            2202: 12
        },
        minimumErrorMsg: 'Minimum product quantity of "%category%" category is %min%',
        mergeVariantQuantity: true
    };
</script>
<script src="https://d3r059eq9mm6jz.cloudfront.net/microapps/category-minimum-quantity/main.hornlegend.com.js" async defer></script>
```

5. Click **Save**

## How It Works

- When a customer adds products from **Group 1 Automotive - Polos** (category ID 2201) to their cart, they must have at least **24** items from that category to proceed to checkout.
- When a customer adds products from **Group 1 Automotive - Pullovers** (category ID 2202) to their cart, they must have at least **12** items from that category to proceed to checkout.
- The `mergeVariantQuantity: true` setting ensures that when the same product is added in multiple sizes (e.g., Polo XL qty 5 + Polo 2XL qty 5), all quantities are summed together toward the category minimum.
- If the minimum is not met, the checkout button will be hidden and an error message will be displayed.

## Troubleshooting

- Make sure **Script type** is set to `Script` (not `URL`).
- Make sure **Location on page** is set to `Footer`.
- Make sure **Select pages where script will be added** is set to `All Pages`.
- If the script does not work, try clearing your browser cache or opening the page in an incognito window.
- To enable debug logging in the browser console, add `debug: true` to the settings object.

## Reference

Full documentation: [https://bc-addons-docs.papathemes.com/category-minimum-quantity.html](https://bc-addons-docs.papathemes.com/category-minimum-quantity.html)
