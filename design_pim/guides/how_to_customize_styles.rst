How to customize styles
=======================

As a part of the frontend/backend decoupling in the PIM we now use the official Less.js library to compile our stylesheets instead of the Oro Assetic bundle and lessphp. There are no major changes in the the way you can add or edit style.

### Configuration
In your package.json file you can configure:
1. The main .less file path - (main.less in pim-community-dev) by default
2. The output path (web/css) by default

### To edit an existing stylesheet
Previously, you would edit a LESS file and then recompile with `bin/console oro:assetic:dump`. The new command is `yarn run styles`. This will compile the LESS into a single CSS file and output it into the configured folder. It should take 1-2 seconds to complete.
You can also have the styles be automatically recompiled and refreshed when you make a change by running `yarn run styles watch`. This command will watch for changes and output a new CSS file each time.
To get the automatic browser refresh running you have to set up your Chrome or Firefox workspaces (links here).

### To add a new stylesheet
Previously, we had an assets.yml file that listed all the stylesheets that would be compiled (in order). This has been replaced with a `main.less` file that does exactly the same thing. Less.js uses this file to compile the final stylesheet.

### Customizing the PIM variables
Let's say you want to change the color of the PIM in your installation. There are two ways you could do this:

### Override every place where the colour is used, e.g:
```
.selector, .menu {
    color: blue
}
```
This isn't the best way, and you'd have to update it each time the PIM styles or structure changed.

### Use custom variables - in your bundle you create two new files:
1. variables.less
In this stylesheet include any variables that you want to override. E.g:
```
@AknThemeColor: blue;
```
2. customized.less (or whatever name you prefer)

In this stylesheet you will import all the PIM stylesheets (link to main.less) and add your variables stylesheet after the PIM one.
After adding these customizations you must change the path of the main stylesheet to yours (customized.less) and recompile with `yarn run styles`.

Note: If you have the assetic bundle compiling and referencing your CSS separately you don't have to change anything.