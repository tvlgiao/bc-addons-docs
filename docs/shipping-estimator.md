# Shipping Estimator Add-on for BigCommerce Product Pages

The Shipping Estimator add-on allows customers to calculate shipping costs directly on product pages before adding items to their cart. This enhances the shopping experience by providing transparent shipping information upfront, reducing cart abandonment and improving customer satisfaction.

## Overview

This add-on integrates seamlessly with your BigCommerce store's product pages, enabling customers to:

- Calculate real-time shipping costs based on their location
- View multiple shipping options and rates
- Make informed purchasing decisions with transparent shipping costs
- Experience a streamlined checkout process

## Live Demonstrations

**Demo 1:** Complete address form with Country, State, City, and Zipcode fields:

![Shipping estimator demo 1](img/estimate-shipping-demo1.gif)

**Demo 2:** Simplified form showing State and Zipcode fields only:

![Shipping estimator demo 2](img/estimate-shipping-demo2.gif)

## Installation Instructions

### Prerequisites

- Active BigCommerce store
- Administrative access to your store's control panel
- Your store domain name

### Step 1: Access Script Manager

1. Log into your BigCommerce admin panel
2. Navigate to **Storefront** → **Script Manager**
3. Click **Create a Script**

### Step 2: Configure Script Settings

Set the following options in the script configuration:

| Setting | Value | Description |
|---------|-------|-------------|
| **Location on page** | `Footer` | Ensures proper loading order |
| **Select pages where script will be added** | `All pages` | Enables the estimator across all product pages |
| **Script type** | `Script` | JavaScript execution type |

### Step 3: Add Script Code

Copy and paste the following code into the **Scripts contents** field:

```html
<script>
    window.jQueryTheme = window.jQueryTheme || window.jQuerySupermarket || window.jQuery;
    window.PapathemesShippingEstimatorSettings = {
        defaultCountry: 'Australia'
    };
</script>
<script src="//papathemes.com/content/shippingestimatoraddon/shipping-estimator.YOURDOMAIN.js" async></script>
```

**Important**: Replace `YOURDOMAIN` with your actual store domain name.

### Example Implementation

For a store with domain `sinkwarehouse.com.au`:

```html
<script>
    window.jQueryTheme = window.jQueryTheme || window.jQuerySupermarket || window.jQuery;
    window.PapathemesShippingEstimatorSettings = {
        defaultCountry: 'Australia'
    };
</script>
<script src="//papathemes.com/content/shippingestimatoraddon/shipping-estimator.sinkwarehouse.com.au.js" async></script>
```

## Configuration Options

### Core Settings

| Parameter | Type | Description | Default Value |
|-----------|------|-------------|---------------|
| `defaultCountry` | String | Pre-selected country in dropdown | `'United States'` |
| `hideCountry` | Boolean | Hide country selection field | `false` |
| `hideState` | Boolean | Hide state/province field | `false` |
| `hideCity` | Boolean | Hide city field | `false` |
| `productFormSelector` | String | CSS selector for product form | Auto-detected |
| `renderToSelector` | String | CSS selector for estimator placement | Auto-detected |
| `useCustomQuotesTemplate` | Boolean | Use custom styling for shipping quotes | `false` |

### Simplified Address Configuration

To display only essential fields (state and zipcode), configure the settings as follows:

```html
<script>
    window.jQueryTheme = window.jQueryTheme || window.jQuerySupermarket || window.jQuery;
    window.PapathemesShippingEstimatorSettings = {
        defaultCountry: 'Australia',
        hideCountry: true,
        hideCity: true
    };
</script>
<script src="//papathemes.com/content/shippingestimatoraddon/shipping-estimator.YOURDOMAIN.js" async></script>
```

## Theme-Specific Configurations

### Supermarket and Chiara Themes

The **Supermarket** and **Chiara** themes include built-in **Products Frequently Bought Together** functionality. To ensure proper integration with the main product form, you must specify a custom product form selector.

Add `productFormSelector: '[data-also-bought-parent-scope] form[data-cart-item-add]'` to your configuration.

#### Example 1: Complete Address Form

Display all address fields (country, state, city, zipcode):

```html
<script>
    window.jQueryTheme = window.jQueryTheme || window.jQuerySupermarket || window.jQuery;
    window.PapathemesShippingEstimatorSettings = {
        defaultCountry: 'Australia',
        productFormSelector: '[data-also-bought-parent-scope] form[data-cart-item-add]'
    };
</script>
<script src="//papathemes.com/content/shippingestimatoraddon/shipping-estimator.YOURDOMAIN.js" async></script>
```

#### Example 2: Simplified Address Form

Display only state and zipcode fields:

```html
<script>
    window.jQueryTheme = window.jQueryTheme || window.jQuerySupermarket || window.jQuery;
    window.PapathemesShippingEstimatorSettings = {
        defaultCountry: 'Australia',
        hideCountry: true,
        hideCity: true,
        productFormSelector: '[data-also-bought-parent-scope] form[data-cart-item-add]'
    };
</script>
<script src="//papathemes.com/content/shippingestimatoraddon/shipping-estimator.YOURDOMAIN.js" async></script>
```

## Advanced Implementation Examples

### Example 1: Custom Positioning with Responsive Design

Position the estimator below the Frequently Bought Together module with custom responsive styling:

```html
<script>
    window.jQueryTheme = window.jQueryTheme || window.jQuerySupermarket || window.jQuery;
    window.PapathemesShippingEstimatorSettings = {
        productFormSelector: '[data-also-bought-parent-scope] form[data-cart-item-add]',
        renderToSelector: '.productView-detailsWrapper',
        defaultCountry: 'United States',
        hideCity: true
    };
    (function() {
        var css = document.createElement('style');
        css.innerHTML = '@media (min-width: 801px) {'
        	+ 'div.PASE-shipping-estimator { float: right; clear: right; width: 50% }'
        	+ '}';
        document.head.appendChild(css);
    })();
</script>
<script src="//papathemes.com/content/shippingestimatoraddon/shipping-estimator.phragos.com.js" async></script>
```

### Example 2: Custom Quotes Template

Implement a custom design for shipping quotes display:

![estimate-shipping-custom-quotes-template](img/estimate-shipping-custom-quotes-template.png)

```html
<script>
    window.jQueryTheme = window.jQueryTheme || window.jQuerySupermarket || window.jQuery;
    window.PapathemesShippingEstimatorSettings = {
        defaultCountry: 'United Kingdom',
        hideCountry: true,
        hideCity: true,
        hideState: true,
        renderToSelector: 'div.productView-options',
        useCustomQuotesTemplate: true
    };
    (function() {
    	var style = document.createElement('style');
        style.innerHTML = '.PASE-shipping-estimator .estimator-form-row--total { padding-top: .75rem; border-top: 1px solid #ddd }';
        document.head.appendChild(style);
    })();
</script>
<script src="//papathemes.com/content/shippingestimatoraddon/shipping-estimator.central-uk.mybigcommerce.com.js?1" async></script>
```

### Example 3: Custom Language Labels and Positioning

Customize heading text and position below the Add to Cart button:

```html
<script>
    window.jQueryTheme = window.jQueryTheme || window.jQuerySupermarket || window.jQuery;
    window.PapathemesShippingEstimatorSettings = {
        productFormSelector: '[data-also-bought-parent-scope] form[data-cart-item-add]',
        renderToSelector: '.productView-details:last-child',
        defaultCountry: 'United Kingdom',
        lang: {
            estimate_shipping: 'Calculate Shipping'
        }
    };
    (function() {
        var css = document.createElement('style');
        css.innerHTML = '@media (min-width: 801px) {'
            + '/*div.PASE-shipping-estimator { float: right; clear: right; width: 50% }*/'
            + '}'
        	+ 'div.PASE-shipping-estimator { margin-top: -0.75rem }'
        	+ '.form--addToCart { margin-bottom: 0 }';
        document.head.appendChild(css);
    })();
</script>
<script src="https://papathemes.com/content/shippingestimatoraddon/shipping-estimator.r129.co.js" async defer></script>
```

## Language Customization

Customize text labels using the `lang` configuration object:

```javascript
window.PapathemesShippingEstimatorSettings = {
    lang: {
        estimate_shipping: 'Calculate Shipping Costs',
        country: 'Select Country',
        state: 'State/Province',
        city: 'City',
        zipcode: 'Postal Code',
        calculate: 'Get Shipping Rates'
    }
};
```

## Advanced Configuration Options

### Additional Parameters

| Parameter | Type | Description | Default Value |
|-----------|------|-------------|---------------|
| `lang` | Object | Custom language labels | English labels |
| `collapsible` | Boolean | Make estimator collapsible | `false` |
| `collapsed` | Boolean | Start in collapsed state | `false` |
| `showEstimateButton` | Boolean | Display calculate button | `true` |
| `autoCalculate` | Boolean | Calculate on field change | `false` |

### CSS Customization

You can add custom CSS styling by injecting styles into the page:

```javascript
(function() {
    var style = document.createElement('style');
    style.innerHTML = `
        .PASE-shipping-estimator {
            border: 1px solid #ddd;
            padding: 1rem;
            margin: 1rem 0;
            border-radius: 4px;
        }
        .PASE-shipping-estimator .form-field {
            margin-bottom: 0.5rem;
        }
    `;
    document.head.appendChild(style);
})();
```

## Troubleshooting

### Common Issues

1. **Estimator not appearing**
   - Verify the domain in the script URL matches your store domain exactly
   - Check browser console for JavaScript errors
   - Ensure the script is loaded in the footer

2. **Incorrect product detection**
   - Verify `productFormSelector` is properly configured for your theme
   - Check if your theme has custom product form structures

3. **Styling conflicts**
   - Use custom CSS to override theme-specific styling
   - Adjust `renderToSelector` to place the estimator in a better location

4. **Shipping rates not calculating**
   - Ensure your BigCommerce shipping zones are properly configured
   - Verify that shipping methods are enabled for the selected regions

### Browser Compatibility

The shipping estimator supports:
- Chrome 60+
- Firefox 55+
- Safari 12+
- Edge 79+
- Internet Explorer 11+ (with polyfills)

## Best Practices

1. **Performance**: The script loads asynchronously to avoid blocking page rendering
2. **User Experience**: Consider hiding less relevant fields for a cleaner interface
3. **Mobile Optimization**: Test the estimator on mobile devices and adjust styling as needed
4. **Testing**: Verify shipping calculations match your store's actual shipping rates

## Support and Maintenance

For technical support or customization requests, provide:
- Your store domain
- Current theme name and version
- Specific configuration requirements
- Any custom styling needs
- Screenshots of issues (if applicable)