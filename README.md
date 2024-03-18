# twenty-twenty-style

> This is a personal modification for [Twenty Twenty](https://wordpress.org/themes/twentytwenty/), the [WordPress](https://wordpress.org/) official default theme for the year 2020.

Despite the theme could be updated since I modified the style, the style is only guarunteed to work on [v1.1](https://downloads.wordpress.org/theme/twentytwenty.1.1.zip). However, feel free to try it on the latest version of the theme.

## Changes

> The purpose of the modification is mainly for adaptation to Chinese-written blogs. It enabled the possibility of the theme to be used in a Chinese WordPress blog.

- Modified oversized fonts to a suitable size (also took care of the mobile end).
- Wider desktop display area, from `58rem` to `78rem`.
- Despite the original display area width was designed for WordPress's block editor, the new change disabled the usability of all the featured components within the block editor.
- Amended all the font-families. Removed the newly locally introduced [Inter](https://rsms.me/inter/) font-family, but prioritised the weight of the [Noto Serif SC](https://fonts.google.com/specimen/Noto+Serif+SC) font (need to be embeded from [Google Fonts](https://fonts.google.com/) later in the instructions). More font fallback options for [monospaced fonts](https://en.wikipedia.org/wiki/Monospaced_font).

*Related blog post: [https://huangxin.dev/partly-technical/my-twentytwenty-theme-modification.html](https://huangxin.dev/partly-technical/my-twentytwenty-theme-modification.html) (written in Chinese)*

## Screenshot

![](https://i.loli.net/2020/04/17/zMEDmOYjQTI6Gr4.jpg)

## Install

1. Install WordPress.
1. Install Twenty Twenty from the admin dashboard.
1. Replace all content in Appearance - Theme Editor - `style.css` with the style.css in this repository.
1. Save the changes and refresh from your blog's homepage.

These steps can also be done via command line:

```sh
cd /path/to/twenty-twenty/
rm -f style.css
wget https://cdn.jsdelivr.net/gh/hifocus/twenty-twenty-style/style.css

# If you would like to use a minified version instead
wget https://cdn.jsdelivr.net/gh/hifocus/twenty-twenty-style/style.min.css -O style.css
```

> If anything goes wrong, install the v1.1 theme.
> Download it from here: [https://downloads.wordpress.org/theme/twentytwenty.1.1.zip](https://downloads.wordpress.org/theme/twentytwenty.1.1.zip).

### Additional Steps

To make sure to release the full power of the modified style, you need to do some additional changes to the theme.

1. In `header.php`, introduce Noto Serif SC from Google Fonts: 

   ```html
   <link href="https://fonts.googleapis.com/css?family=Noto+Serif+SC&display=swap"  rel="stylesheet">
   ```

   Despite the use of the CSS property `display: swap`, this will not slow the loading speed of your blog.
1. In `footer.php`, centralise the summary texts at the homepage by adding Javascript code as below; plus introduce the instant.page library for better loading experience:

   ```html
   <script>
   let homepages = [ '/', 'index.html', 'index.htm', 'index.php'];
   if (homepages.indexOf(window.location.pathname) == "0") {
   let all = document.getElementsByClassName('entry-content');
   for (var i = 0; i < all.length; i++) {
   all[i].style['text-align'] = 'center';
   } }
   </script>

   <script src="https://cdn.jsdelivr.net/npm/instant.page@3/instantpage.min.js" type="module" defer></script>
   ```

## License

This repository is released under the same license as the original theme, the [GNU General Public License 2.0](https://github.com/hifocus/twenty-twenty-style/blob/master/LICENSE).