As of AMP 1.9.9.6, you can now easily customise AMPs appearance with custom themes. These are simply CSS files with extra styles applied over the top of AMPs defaults. These files are preserved between updates and can be switched on-demand, requiring just a page refresh.

# Creating Theme Files

Theme files are simply CSS files with custom styling rules. You can write these same as any other styles. You can use your browsers developer tools to experiment and then save your changes as a new file.

See the [w3c](https://www.w3schools.com/Css/) for an excellent beginners guide to CSS.

If you wish to share your themes you're welcome to do so, the only rule is they must not remove or obscure any CubeCoders/AMP branding. If you wish to do so the best way to do this is to submit a pull request with your theme in from the Theme directory of the CubeCoders/AMP repo (https://github.com/CubeCoders/AMP/tree/master/Themes)

# Installing Theme Files

Themes are located in the WebRoot/Themes directory of your ADS01 instance. On a Linux system for example this will be in `~/.ampdata/instances/ADS01/WebRoot/Themes/` where you'll find an (empty) default.css file.

Place your new CSS files here and then restart your ADS instance. Once that's running you'll be able to access your new theme by its name under Configuration -> Branding -> Theme (or search for 'Theme' in the top-right search box).

Changing your theme requires a refresh of the page to take effect. This theme will be applied to all users of your AMP installation. It will also apply to any instances that are managed by ADS as they share the same front-end.