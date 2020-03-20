# Display custom popups on any page.

This extension allows to display your custom popups on any page. Popup content and configuration can be edited in **Marketing** > **Banners**.

## Install the script on your BigCommerce store

Go to **Storefront** > **Script Manager**, click **Create a Script**, choose:

- **Location on page** = `Footer`
- **Select pages where script will be added** = `All pages`
- **Script type** = `Script`

Enter the script below to **Scripts contents**: 

```html
<script>
    window.PapathemesPopupsSettings = {
        pageType: '{{page_type}}'
    };
</script>
<script src="//papathemes.com/content/popups/popups.public.js" async></script>
```

## Create the popup content

Login to your store admin, go to **Marketing** > **Banners** > click **Create a Banner** button.

In **Banner Content**, click the small **HTML** button to open HTML Source Editor:

![popups-banner-content-click-html-button](img/popups-banner-content-click-html-button.png)

Copy and paste the sample content below:

```html
<div data-papathemes-popups="{
    'delay': 5,
    'pageType': '',
    'urlMatch': '',
    'id': 'popup1',
    'expire', 3600,
    'disableText': 'Do not show again',
    'swal': {
        'timer': 3000,
        'timerProgressBar': true,
        'width': '800px'
    }
}">
  <p>The First Popup displays after page loaded 5s.</p>
</div>


<div data-papathemes-popups="{
    'delay': 5,
    'pageType': '',
    'urlMatch': ''
}">
  <p>The Second Popup displays after the first popup closed 5s.</p>
</div>
```

![popups-banner-content-edit-html](img/popups-banner-content-edit-html.png)


Choose:

- **Show on Page** = `Search Results Page`
- **Visible** = `Yes`
- **Location** = `Botom of Page`

![popups-banner-options](img/popups-banner-options.png)

Save the banner.

Refresh your storefront page you should see 2 popups display after 5s and 10s.


## Popup Configuration

Take a look of the above code:

```js
    'delay': 5,
    'pageType': '',
    'urlMatch': '',
    'id': 'popup1',
    'expire': 3600,
    'disableText': 'Do not show again',
    'swal': {
        'timer': 3000,
        'timerProgressBar': true,
        'width': '800px'
    }
```

- `delay`: Is delay time (in second) before the popup displays when the page is loaded.
- `pageType`: Leave it empty to display the popup on all pages.
    - = `default`: To display the popup on Homepage only.
    - = `category`: To display the popup on category pages.
    - = `product`: To display the popup on product pages.
    - = `page`: To display the popup on static web pages.
- `urlMatch`: Leave it empty to display the popup on all pages.
    - Set an url for example `/all-products/` to display the popup on any page which has URL matches `/all-products/`.
- `id`: The unique popup name. Required only if `expire` is set.
- `expire`: A time (in seconds) to not show the popup again.
- `disableText`: a checkbox label to allow user not showing the popup again. If not set, the default label is "Don't show again".
- `swal`: Are **SweatAlert2** configuration variables. Check more details here: <https://sweetalert2.github.io/#configuration>

