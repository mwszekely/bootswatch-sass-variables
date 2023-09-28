# Bootswatch Sass Variables

Combination of [Bootstrap Sass Variables](https://github.com/mwszekely/bootstrap-sass-variables) (a Sass Modules """polyfill""" for Bootstrap, I guess?) and [Bootswatch](https://bootswatch.com).

The intent is to make it easier to customize individual variables within a Bootswatch theme in the same way that [Bootstrap Sass Variables](https://github.com/mwszekely/bootstrap-sass-variables) does for Bootstrap itself, since Bootstrap doesn't support Sass modules yet.

This library and [Bootstrap Sass Variables](https://github.com/mwszekely/bootstrap-sass-variables) are in the public domain -- Bootswatch and Bootstrap are MIT-licensed.

Note: When building with Sass, this library assumes load paths have been added with (e.g.) the following command line arguments: `--load-path="./node_modules/bootstrap-sass-variables/sass" --load-path="./node_modules/bootstrap" --load-path="./node_modules/bootswatch-sass-variables/sass"`

## To use

Sass can override `!default` variables. Dependencies get complicated, but Sass's error messages are very helpful in diagnosing what order things should be in: 

````scss
// Override the Zephyr theme's $secondary color,
// and Bootstrap's $primary color.
// (Sass "guides" you through this process via error messages)

// Dependency of $primary, must come first if $primary is overridden
// (because Zephyr defines its own $blue)
@forward "bootswatch-sass-variables/zephyr/variables/blue";
// Override $secondary in Zephyr's theme
@forward "bootswatch-sass-variables/zephyr/variables/secondary" with ($secondary: aquamarine);
// Override $primary in Bootstrap's theme
@use "bootstrap-sass-variables/primary" with ($primary: fuchsia);

// Use the rest of the Zephyr theme (including Bootstrap itself).
@forward "bootswatch-sass-variables/zephyr";
````
