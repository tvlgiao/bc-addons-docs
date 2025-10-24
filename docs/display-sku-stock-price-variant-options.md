# Display SKU, Stock & Price on Product Variant Options

## Overview

This feature displays **SKU**, **Stock**, and **Price** for each variant option value on the product page. Data is fetched from BigCommerce GraphQL API and displayed in real-time when users select options.

**GitHub Repository**: [bc-onlinemetalsupply-supermarket-variant-option-price-sku-stock-mod](https://github.com/allcommerce/bc-onlinemetalsupply-supermarket-variant-option-price-sku-stock-mod)

**Theme Compatibility**: Supermarket theme

## Created/Modified Files

### 1. **assets/js/theme/common/product-variant-info.js** (NEW)

Service class to:

- Fetch variant data from GraphQL API with authentication (graphQLToken)
- Map variants with option values
- Generate HTML to display variant info
- Format prices according to currency settings
- Cache variant data for performance optimization

### 2. **assets/js/theme/common/product-details.js** (UPDATED)

Added:

- Import `ProductVariantInfo` service
- Method `initVariantInfo()` - Initialize and fetch variant data
- Method `updateAllOptionVariantInfo()` - Update info for all options
- Method `updateOptionValueVariantInfo()` - Update info for each option value
- Method `getSelectedOptionValueIds()` - Get selected option values
- Method `getVariantTextForSelect()` - Format text for dropdown options

### 3. **assets/scss/components/stencil/productView/_productView-variantInfo.scss** (NEW)

CSS styling for:

- `.variant-info-container` - Container for variant info
- `.variant-sku` - SKU display with 📋 icon
- `.variant-stock` - Stock display (green if in stock, red if out)
- `.variant-price` - Price display with sale price support
- Responsive styles
- Loading animation
- Out of stock styling

### 4. **assets/scss/components/stencil/productView/_component.scss** (UPDATED)

Import new CSS file

## How It Works

### Workflow:

1. **Page Load**: When product page loads
   - `ProductDetails` constructor is called
   - Initialize `ProductVariantInfo` service with product ID
   - Call `initVariantInfo()` to fetch variants
2. **Fetch Variants**:
   - Check if `graphQLToken` exists (required)
   - GraphQL query fetches all product variants with authentication
   - Headers: `Authorization: Bearer ${graphQLToken}`
   - Includes: SKU, stock, prices, option values
   - Data is cached in service
3. **Build Variant Map**:
   - Each variant is mapped with combination of option value IDs
   - Example: Size M + Color Red = variant with SKU "M-RED-001"
4. **Display Info**:
   - For each option value, find corresponding variant
   - Generate HTML with SKU, stock, price
   - Insert into UI (different for each option type)
5. **Update on Change**:
   - When user selects different option
   - Re-calculate variant info
   - Update UI with new data

## GraphQL Query

```graphql
query ProductVariants($productId: Int!, $currencyCode: currencyCode!, $includeTax: Boolean!) {
  site {
    product(entityId: $productId) {
      entityId
      variants(first: 250) {
        edges {
          node {
            entityId
            sku
            inventory {
              isInStock
              aggregated {
                availableToSell
              }
            }
            isPurchasable
            prices(currencyCode: $currencyCode, includeTax: $includeTax) {
              price { currencyCode value }
              retailPrice { currencyCode value }
              salePrice { currencyCode value }
              basePrice { currencyCode value }
            }
            productOptions {
              edges {
                node {
                  entityId
                  displayName
                  isVariantOption
                  ... on MultipleChoiceOption {
                    __typename
                    values {
                      edges {
                        node {
                          entityId
                          label
                          isSelected
                        }
                      }
                    }
                  }
                }
              }
            }
          }
        }
      }
    }
    currency(currencyCode: $currencyCode) {
      display {
        symbol
        symbolPlacement
        decimalToken
        thousandsToken
        decimalPlaces
      }
    }
  }
}
```

## UI Display Examples

### 1. Swatch Options (Color/Size swatches)

```html
<label class="form-option form-option-swatch">
  <input type="radio" value="red" />
  <span>Red</span>
  <div class="variant-info-container">
    <span class="variant-info">
      <span class="variant-sku">📋 SKU: RED-001</span>
      <span class="variant-stock in-stock">📦 15 in stock</span>
      <span class="variant-price">$29.99</span>
    </span>
  </div>
</label>
```

### 2. Rectangle/Radio Options

```html
<label class="form-label">
  <input type="radio" value="medium" />
  <span>Medium</span>
  <div class="variant-info-container">
    <span class="variant-info">
      <span class="variant-sku">📋 SKU: M-001</span>
      <span class="variant-stock in-stock">📦 8 in stock</span>
      <span class="variant-price">
        <span class="price-now">$24.99</span>
        <span class="price-was">$29.99</span>
      </span>
    </span>
  </div>
</label>
```

### 3. Select Dropdown

```html
<select>
  <option value="1">Small (SKU: S-001 - $19.99 - 10 in stock)</option>
  <option value="2">Medium (SKU: M-001 - $24.99 - 8 in stock)</option>
  <option value="3">Large (SKU: L-001 - $29.99 - Out of stock)</option>
</select>
```

## Console Logs

Feature includes logging for debugging:

```
🎯 Initializing variant info...
🔍 Fetching variants for product 123...
✅ Successfully fetched 12 variants
📊 Mapped 12 variants
```

## CSS Classes

### Main Classes:

- `.variant-info-container` - Container wrapper
- `.variant-info` - Flex container for info items
- `.variant-sku` - SKU display
- `.variant-stock` - Stock display
  - `.in-stock` - In stock (green color)
  - `.out-of-stock` - Out of stock (red color, strikethrough)
- `.variant-price` - Price display
  - `.price-now` - Current/sale price
  - `.price-was` - Original price (strikethrough)

### State Classes:

- `.unavailable` - Option unavailable (reduced opacity, strikethrough)
- `.variant-info-loading` - Loading state with shimmer effect

## Customization

### Change icons:

In `product-variant-info.js`:

```javascript
generateVariantInfoHTML(variant) {
    // SKU icon: 📋 -> 🏷️
    parts.push(`<span class="variant-sku">🏷️ SKU: ${variant.sku}</span>`);

    // Stock icon: 📦 -> ✓
    parts.push(`<span class="variant-stock in-stock">✓ ${stockText}</span>`);
}
```

### Change colors:

In `_productView-variantInfo.scss`:

```scss
.variant-stock {
    &.in-stock {
        color: #28a745; // Green
    }

    &.out-of-stock {
        color: #dc3545; // Red
    }
}
```

### Change layout:

```scss
.variant-info {
    flex-direction: column; // Stack vertically
    // or
    flex-direction: row; // Inline horizontally
}
```

## Browser Support

- Chrome/Edge: ✅ Full support
- Firefox: ✅ Full support
- Safari: ✅ Full support
- IE11: ⚠️ Requires polyfills for async/await and Map

## Performance

- Variant data is cached after first fetch
- GraphQL query limits to 250 variants (can increase if needed)
- UI updates only when option changes
- No re-fetch when switching between options

## Testing

### 1. Test on product with variants:

1. Navigate to product page with variants (Size, Color, etc.)
2. Open Console to view logs
3. Select different options
4. Verify variant info displays correctly

### 2. Test edge cases:

- Product without variants
- Out of stock variants
- Variants with sale price
- Multiple variant combinations
- Slow network (check loading state)

## Troubleshooting

### Variant info not displaying:

1. Check console logs - if you see "⚠️ graphQLToken does not exist", check config
2. Verify product has variants in BigCommerce admin
3. Check GraphQL endpoint `/graphql` is working
4. Verify `context.graphQLToken` has value (required for authentication)
5. Verify `context.showPricesWithTax` settings

### Wrong price/stock:

1. Check currency code in context
2. Verify includeTax setting
3. Check variant mapping logic

### CSS not applied:

1. Verify SCSS file is imported
2. Run build process: `npm run build`
3. Clear cache and reload

## Future Enhancements

1. **Lazy loading**: Only fetch variants when needed
2. **Image preview**: Display variant image on hover
3. **Tooltip mode**: Alternative display mode
4. **Batch updates**: Optimize multiple option changes
5. **Animation**: Smooth transitions when updating info
6. **Localization**: Support multi-language

## Support

If you have issues:

1. Check console logs
2. Verify GraphQL query in Network tab
3. Check variant data in BigCommerce admin
4. Review applied CSS classes
