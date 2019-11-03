# Conditional Product Options

## Demo

![conditional product options demo](img/conditional-product-options.gif)

## Install the script on your BigCommerce store

Go to **Storefront** > **Script Manager**, click **Create a Script**, choose:

- **Location on page** = `Footer`
- **Select pages where script will be added** = `All pages`
- **Script type** = `Script`

Enter the script below to **Scripts contents**: 

```html
<script>
    window.jQueryTheme = window.jQueryTheme || window.chiarajQuery || window.jQuery;
    window.PapathemesConditionalProductOptionsSettings = {
        fields: [
            {
                title: 'One side design only:',
                options: [
                    {
                        label: 'Front-side design',
                        showAttributes: [
                            'SIZES',
                            'FRONT PHOTO UPLOAD',
                            'FRONT TEXT'
                        ]
                    },
                    {
                        label: 'Back-side design',
                        showAttributes: [
                            'BACKSIDE STYLE OPTIONS',
                            'BACK PHOTO UPLOAD'
                        ]
                    }
                ]
            }
        ]
    };
</script>
<script src="//papathemes.com/content/conditionalproductoptionsaddon/conditional-product-options.public.js" async></script>
```

## Customize the dependent options

You can customize the option title and the radio labels by editing:
- `'One side design only:'`
- `'Front-side design'`
- `'Back-side design'`

Check the screenshot below:

![option group title](img/edit-option-group-title.png)

### Configure the product options depending on the first choice

![first choice dependent options](img/first-dependent-options.png)

**Note:**
- The product option title entered in the configuration code snippet above must be in uppercase. 
- This string must be the same or appear at the beginning of your product option title.


### Configure the product options depending on the second choice

![second choice dependent options](img/first-dependent-options.png)

There is no limited number of choices and dependent product options. You can configure the configuration code to display more.

