# Sell Products By Pack

Transform your BigCommerce store to sell products in bulk quantities with this powerful addon. Perfect for wholesale businesses, B2B stores, or any retailer offering products in predetermined pack sizes.

![bc-sell-by-pack-demo](img/bc-sell-by-pack-demo.gif)

## What This Addon Does

- **Pack-Based Selling**: Force customers to purchase products in specific quantities (e.g., 10-packs, 50-packs)
- **Variant Support**: Set different pack sizes for product variants
- **Automatic Validation**: Prevents customers from adding incorrect quantities to cart
- **Wholesale Ready**: Ideal for businesses selling to retailers or bulk buyers

## Installation Guide

### Step 1: Access Script Manager

1. Log into your BigCommerce admin panel
2. Navigate to **Storefront** → **Script Manager**
3. Click the **Create a Script** button

### Step 2: Configure Script Settings

Fill in the following settings:

| Field | Value |
|-------|-------|
| **Location on page** | Footer |
| **Select pages where script will be added** | All pages |
| **Script type** | Script |

### Step 3: Add the Script Code

Copy and paste the following code into the **Scripts contents** field:

```html
<script>
    window.jQueryTheme = window.jQueryTheme || window.jQuerySupermarket || window.chiarajQuery || window.jQuery || window.$;
    window.PapathemesSellByPackSettings = {
        stepCustomFieldName: 'Step',
        graphQLToken: '{{settings.storefront_api.token}}'
    };
</script>
<script src="//papathemes.com/content/sellbypackaddon/sellbypack.YOURDOMAIN.js" async></script>
```

**Important**: Replace `YOURDOMAIN` with your actual store domain name (e.g., if your store is `mystore.com`, use `sellbypack.mystore.js`)

## Product Configuration

### Setting Up Basic Pack Quantities

1. **Edit Your Product**:
   - Go to **Products** → **View Products**
   - Click **Edit** on the product you want to sell by pack

2. **Add Custom Field**:
   - Scroll down to the **Custom Fields** section
   - Click **Add Custom Field**
   - Set **Custom Field Name** to: `Step`
   - Set **Custom Field Value** to your pack size (e.g., `10` for 10-packs)

![edit-custom-field-sell-by-pack](img/edit-custom-field-sell-by-pack.png)

3. **Update Minimum Quantity**:
   - In the **Inventory** section, set **Minimum Purchase Quantity** to match your pack size
   - This ensures customers can't purchase less than one complete pack

### Advanced: Different Pack Sizes for Product Variants

If your product has variants (size, color, etc.) with different pack quantities, use this format in the **Custom Field Value**:

```
200,SKU-E23036E2:100,SKU-62C208F5:125,SKU-65D30EBC:150
```

**Explanation**:
- `200` = Default pack size for all variants
- `SKU-E23036E2:100` = This specific variant SKU sells in packs of 100
- `SKU-62C208F5:125` = This variant SKU sells in packs of 125
- `SKU-65D30EBC:150` = This variant SKU sells in packs of 150

**Format Rules**:
- Separate each variant with a comma (`,`)
- Use colon (`:`) between SKU and pack size
- First number is always the default pack size


## Configuration Options

### Basic Settings

These settings control the core functionality and can be customized if needed:

| Setting | Default Value | Description |
|---------|---------------|-------------|
| `stepCustomFieldName` | `'Step'` | The name of the custom field that contains pack quantities |
| `minQtyIsStep` | `true` | Automatically sets minimum purchase quantity to match pack size |
| `graphQLToken` | `'{{settings.storefront_api.token}}'` | Required for API communication (do not change) |

### Advanced Theme Customization

**⚠️ For Developers Only**: These settings are for custom themes that may use different CSS selectors:

| Setting | Default Value | Purpose |
|---------|---------------|---------|
| `qtyChangeSelector` | `'[data-quantity-change]'` | Quantity input field selector |
| `notQtyChangeSelector` | `'[data-also-bought] [data-quantity-change]'` | Elements to exclude from quantity changes |
| `productViewSelector` | `'.productView'` | Main product display container |
| `customFieldRowSelector` | `'[class*=productView-info-row]'` | Custom field row container |
| `customFieldNameSelector` | `'.productView-info-name'` | Custom field name element |
| `customFieldValueSelector` | `'.productView-info-value'` | Custom field value element |
| `incBtnSelector` | `'[data-action="inc"]'` | Quantity increase button |
| `decBtnSelector` | `'[data-action="dec"]'` | Quantity decrease button |
| `formSelector` | `'form[data-cart-item-add]'` | Add to cart form |
| `productIdInputSelector` | `'input[name="product_id"]'` | Hidden product ID input |
| `cartQtyInputSelector` | `'[data-cart-content] input[name^="qty-"]'` | Cart quantity inputs |
| `cartQtyIdRegExp` | `/^qty-(.*)/` | Pattern to match cart item IDs |
| `cartQtyBtnSelector` | `'[data-action]'` | Cart quantity buttons |
| `cartOverlaySelector` | `'[data-cart] .loadingOverlay'` | Cart loading overlay |
| `productViewTemplate` | `'products/product-view'` | Product page template file |

## Troubleshooting

### Common Issues

**Problem**: Quantity buttons don't work
- **Solution**: Check that your theme uses standard BigCommerce selectors. Contact support if using a custom theme.

**Problem**: Pack quantities not displaying
- **Solution**: Ensure the custom field name is exactly `Step` (case-sensitive)

**Problem**: Script not loading
- **Solution**: Verify you replaced `YOURDOMAIN` with your actual domain name in the script URL

### Getting Help

- For technical support, contact your theme developer
- For addon-specific issues, refer to the documentation or contact the addon provider

## Additional Resources

- Mod for Camden theme: https://github.com/tvlgiao/bc-sellbypack-ilighting-camden-theme
