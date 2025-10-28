# Hide Product Options/Values based on Customer Groups

This script allows you to hide product options or option values based on customer groups.

## Features

- ✅ **Hide entire options** - Hide both dropdown/input and label of an option
- ✅ **Hide specific values** - Only hide some values within a dropdown
- ✅ **Hide for specific customer groups** - Hide options only for certain customer groups
- ✅ **Hide for all except** - Hide options for all customer groups except specified ones

## Basic Concepts

### 1. Option vs Option Value

- **Option**: The entire dropdown or input field. Example: "Color", "Size"
- **Option Value**: The values within an option. Example: "Red", "Blue" within "Color" option

### 2. Hiding Methods

| Method | When to Use | Result |
|--------|-------------|--------|
| **Hide Option Value** | Want to hide specific values only | Dropdown still visible but missing some choices |
| **Hide Entire Option** | Want to hide the entire dropdown/field | Both dropdown and label disappear |

### 3. Customer Group Selection Methods

| Method | When to Use | Syntax |
|--------|-------------|--------|
| **customerGroups** | Hide only for specific groups | `customerGroups: ['Group A', 'Group B']` |
| **hideForAllExcept** | Hide for all groups except specified ones | `hideForAllExcept: ['Group A', 'Group B']` |

## Example 1: Hide Specific Values for Certain Customer Groups

**Requirement**: Hide sizes "Extra Small" and "Monster" only for "Dealer Australia" and "Dealer International" groups

```html
<script>
    window.PapathemesHideProductOptionSettings = {
        rules: [
            {
                options: [
                    {
                        name: 'Size',
                        value: 'Extra Small',
                    },
                    {
                        name: 'Size',
                        value: 'Monster',
                    }
                ],
                customerGroups: [
                    'Dealer Australia',
                    'Dealer International'
                ]
            }
        ],
        customerGroupName: '{{customer.customer_group_name}}',
        graphQLToken: '{{settings.storefront_api.token}}',
        debug: false
    };
</script>
```

## Example 2: Hide Entire Option for Certain Customer Groups

**Requirement**: Hide the entire "Gift Wrapping" option only for "Wholesale" group

```html
<script>
    window.PapathemesHideProductOptionSettings = {
        rules: [
            {
                hideOptions: [
                    'Gift Wrapping'
                ],
                customerGroups: [
                    'Wholesale'
                ]
            }
        ],
        customerGroupName: '{{customer.customer_group_name}}',
        graphQLToken: '{{settings.storefront_api.token}}',
        debug: false
    };
</script>
```

## Example 3: Hide for ALL Groups Except Specified Ones

**Requirement**: Hide "Five Point Star Embroidery? (+$15.00)" option and "Black" value in "Color" option for ALL customer groups, EXCEPT "Union County SO" and "Union County SO (FULL)"

```html
<script>
    window.PapathemesHideProductOptionSettings = {
        rules: [
            {
                hideOptions: [
                    'Five Point Star Embroidery? (+$15.00)'
                ],
                options: [
                    {
                        name: 'Color',
                        value: 'Black'
                    }
                ],
                hideForAllExcept: [
                    'Union County SO',
                    'Union County SO (FULL)'
                ]
            }
        ],
        customerGroupName: '{{customer.customer_group_name}}',
        graphQLToken: '{{settings.storefront_api.token}}',
        debug: false
    };
</script>
```

**Result**:

- Customers in "Union County SO" or "Union County SO (FULL)" → See all options
- Customers in other groups (including guests) → Cannot see "Five Point Star Embroidery" and "Black" color

## Example 4: Combine Multiple Rules

**Requirement**:

- Hide size "Extra Small" for "Dealer" group
- Hide entire "Gift Wrapping" option for ALL groups except "VIP Customer"

```html
<script>
    window.PapathemesHideProductOptionSettings = {
        rules: [
            {
                options: [
                    {
                        name: 'Size',
                        value: 'Extra Small'
                    }
                ],
                customerGroups: ['Dealer']
            },
            {
                hideOptions: ['Gift Wrapping'],
                hideForAllExcept: ['VIP Customer']
            }
        ],
        customerGroupName: '{{customer.customer_group_name}}',
        graphQLToken: '{{settings.storefront_api.token}}',
        debug: false
    };
</script>
```

## Complete Structure

```javascript
window.PapathemesHideProductOptionSettings = {
    rules: [
        {
            // Hide entire options (can be empty if not used)
            hideOptions: [
                'Option Name 1',
                'Option Name 2'
            ],

            // Hide specific values (can be empty if not used)
            options: [
                {
                    name: 'Option Name',
                    value: 'Option Value'
                }
            ],

            // Choose ONE of the two methods below:

            // Method 1: Hide only for these groups
            customerGroups: [
                'Group Name 1',
                'Group Name 2'
            ],

            // Method 2: Hide for all EXCEPT these groups
            hideForAllExcept: [
                'Group Name 1',
                'Group Name 2'
            ]
        }
    ],
    customerGroupName: '{{customer.customer_group_name}}',
    graphQLToken: '{{settings.storefront_api.token}}',
    debug: false  // Set to true to see debug logs in Console
};
```

## Important Notes

1. **Names must match exactly**: Option and value names must match exactly as they appear in BigCommerce (case-sensitive)
2. **Enable debug when testing**: Set `debug: true` to see logs in Console (F12) during testing
3. **Don't use both customerGroups and hideForAllExcept**: Only choose one method
4. **Guest customers**: To hide for non-logged-in customers, add empty string `''` to customerGroups

## Links

- GitHub (new): https://github.com/tvlgiao/bigcommerce-api-app/tree/master/microapps/hide-product-option
- GitHub: https://github.com/tvlgiao/bc-zacataklures-chiara-hide-product-options


## Installation Guide

### Step 1: Go to Script Manager

Go to **Storefront** > **Script Manager**, click **Create a Script**, choose:

- **Location on page** = `Footer`
- **Select pages where script will be added** = `Store Pages`
- **Script type** = `Script`

### Step 2: Add script to **Scripts contents**

```html
<script>
window.PapathemesHideProductOptionSettings = {
    rules: [
        {
            // Example: Hide some option values
            options: [
                {
                    name: 'Color',
                    value: 'Black',
                }
            ],
            // Hide for these groups
            customerGroups: [
                'Wholesale',
            ]
        },
    ],
    customerGroupName: '{{customer.customer_group_name}}',
    graphQLToken: '{{settings.storefront_api.token}}',
    debug: false
};
</script>
<script src="https://d3r059eq9mm6jz.cloudfront.net/microapps/hide-product-option/main.js" async defer></script>
```

**Note**: Modify the content in `rules` according to your requirements (see examples above)

---

## Installation for parrpse.com

### Requirement

Hide the following options for ALL customer groups EXCEPT "Union County SO" and "Union County SO (FULL)":

- The entire "Five Point Star Embroidery? (+$15.00)" option
- The "Black" color value (other colors remain visible)

### Explanation

This configuration uses the `hideForAllExcept` method, which means:

**For Union County SO and Union County SO (FULL) customers:**

- ✅ They can see the "Five Point Star Embroidery? (+$15.00)" option
- ✅ They can select "Black" color
- ✅ They can see all other colors
- Result: Full access to all product options

**For all other customers (including guests, retail customers, etc.):**

- ❌ The "Five Point Star Embroidery? (+$15.00)" option is completely hidden (both label and dropdown disappear)
- ❌ The "Black" color is removed from the Color dropdown
- ✅ Other colors are still visible in the dropdown
- Result: Restricted access - cannot order these specific options

### Script to Install

```html
<script>
window.PapathemesHideProductOptionSettings = {
    rules: [
        {
            hideOptions: [
                'Five Point Star Embroidery? (+$15.00)',
            ],
            options: [
                {
                    name: 'Color',
                    value: 'Black',
                }
            ],
            hideForAllExcept: [
                'Union County SO',
                'Union County SO (FULL)',
            ],
        },
    ],
    customerGroupName: '{{customer.customer_group_name}}',
    graphQLToken: '{{settings.storefront_api.token}}',
    debug: true,
};
</script>
<script src="https://d3r059eq9mm6jz.cloudfront.net/microapps/hide-product-option/main.parrpse.com.js" async defer></script>
```

### Configuration Breakdown

| Setting | Value | What it does |
|---------|-------|--------------|
| `hideOptions` | `['Five Point Star Embroidery? (+$15.00)']` | Completely hides this entire option (label + dropdown) |
| `options` | `name: 'Color', value: 'Black'` | Hides only the "Black" value within the Color dropdown |
| `hideForAllExcept` | `['Union County SO', 'Union County SO (FULL)']` | Apply hiding to ALL groups EXCEPT these two |
| `debug` | `true` | Shows debug information in browser Console (F12) for troubleshooting |

### Testing

1. **Test as Union County SO customer**: You should see the embroidery option and Black color
2. **Test as guest or other group**: The embroidery option should completely disappear, and Black color should not be in the dropdown
3. **Enable debug mode**: Press F12, go to Console tab to see detailed logs

---

## Installation for strideanimalhealth.com

```html
<script>
window.PapathemesHideProductOptionSettings = {
    rules: [
        {
            options: [
                {
                    name: 'Order Frequency',
                    value: 'One Time Purchase',
                },
                {
                    name: 'Order Frequency',
                    value: 'Subscribe & Save',
                },
                {
                    name: 'Ships Every',
                    value: 'Ships Every (2-8 weeks)'
                },
                {
                    name: 'Ships Every',
                    value: 'Ships Every (1-3 months)',
                },
            ],
            customerGroups: [
                'Veterinarian',
                'BB Dealer',
                'STRIDE DEALER',
                'APC - Lifeline only @ dealer cost',
            ]
        },
    ],
    customerGroupName: '{{customer.customer_group_name}}',
    graphQLToken: '{{settings.storefront_api.token}}',
    debug: false
};
</script>
<script src="https://d3r059eq9mm6jz.cloudfront.net/microapps/hide-product-option/main.strideanimalhealth.com.js" async defer></script>
```
