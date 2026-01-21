# Apparel Product Options

Demo: https://totalapparel.com/mens-zone-performance-polo/

Git: https://github.com/tvlgiao/bc-bigcommerce-api-app/microapps/apparel-product-options

## Custom CSS for Parts Warehouse Theme

### Method 1: Using Script Manager (Recommended)

To apply custom CSS styling to the Apparel Product Options, follow these steps:

1. Go to **Storefront** > **Script Manager**
2. Click **Create a Script**
3. Configure the script settings:
    - **Location on page** = Footer
    - **Select pages where script will be added** = All Pages
    - **Script type** = Script

4. Enter the following code into **Scripts contents**:

```html
<script>
(function() {
    var style = document.createElement('style');
    style.innerHTML = `
        /* ===== HIDE UNNECESSARY ELEMENTS ===== */
        .PAPATHEMES_APPARELPRODUCTOPTIONS__form-field ._prices,
        .PAPATHEMES_APPARELPRODUCTOPTIONS__form-field .price-section,
        .PAPATHEMES_APPARELPRODUCTOPTIONS__form-field .price-section-group,
        .PAPATHEMES_APPARELPRODUCTOPTIONS__form-field ._stockLabel,
        .PAPATHEMES_APPARELPRODUCTOPTIONS__form-field ._stock,
        .PAPATHEMES_APPARELPRODUCTOPTIONS__form-field ._qtyLabel {
            display: none !important;
        }

        /* ===== GRID LAYOUT ===== */
        .PAPATHEMES_APPARELPRODUCTOPTIONS__form-field ._optionValues {
            display: grid !important;
            grid-template-columns: repeat(auto-fit, minmax(65px, 1fr)) !important;
            gap: 10px !important;
            max-width: 400px !important;
        }

        /* ===== OPTION VALUE BOX ===== */
        .PAPATHEMES_APPARELPRODUCTOPTIONS__form-field ._optionValue {
            display: inline-flex !important;
            flex-direction: column !important;
            align-items: start !important;
            width: auto !important;
            max-width: none !important;
            min-width: auto !important;
        }

        /* ===== LABEL ===== */
        .PAPATHEMES_APPARELPRODUCTOPTIONS__form-field ._label {
            font-size: 11px !important;
            font-weight: 600 !important;
            white-space: nowrap !important;
        }

        .PAPATHEMES_APPARELPRODUCTOPTIONS__form-field label.form-label {
            float: none;
        }

        /* ===== INPUT STYLING ===== */
        .PAPATHEMES_APPARELPRODUCTOPTIONS__form-field ._qty input {
            width: 50px !important;
            height: 30px !important;
            text-align: center !important;
            font-size: 12px !important;
            border: 1px solid #ccc !important;
            border-radius: 3px !important;
            box-sizing: border-box !important;
        }

        /* ===== HIDE SPINNER ===== */
        .PAPATHEMES_APPARELPRODUCTOPTIONS__form-field input[type='number'] {
            -moz-appearance: textfield;
        }

        .PAPATHEMES_APPARELPRODUCTOPTIONS__form-field input::-webkit-outer-spin-button,
        .PAPATHEMES_APPARELPRODUCTOPTIONS__form-field input::-webkit-inner-spin-button {
            -webkit-appearance: none;
            display: none !important;
        }
    `;
    document.head.appendChild(style);
})();
</script>
```

5. Click **Save**

### Method 2: Using Theme Customizer (Alternative)

If your theme supports custom CSS in the Theme Customizer:

1. Go to **Storefront** > **Themes** > Click **Customize** on your active theme
2. Find the **Custom CSS** section
3. Add the CSS code from the script above (without the `<script>` tags and `style.innerHTML`)


### What This CSS Does

- **Hides** unnecessary elements (prices, stock labels, quantity labels)
- **Creates a grid layout** for option values with responsive columns
- **Styles option value boxes** for better alignment and spacing
- **Formats labels** with consistent sizing and weight
- **Styles quantity input fields** with fixed dimensions and centered text
- **Removes spinner controls** from number inputs for cleaner appearance