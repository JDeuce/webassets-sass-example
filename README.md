# Purpose
Sample file showing how to use variable overrides in SASS with webassets.

# Files

## 1.scss

    $foo: bar;

## 2.scss

    $foo: foo !default;


## webassets.yaml


    directory: .

    bundles:

        bundle1:
            output: out.css
            filters: scss,cssutils

            # Set SASS to output mode, the real key
            # for shared variables
            config:
                SASS_AS_OUTPUT: true

            contents:
                - 1.scss
                - 2.scss

## out.css

    .test{background-color:bar}


# Running it

    webassets -c webassets.yaml build


## Note

If you mess with the config options you need to clear the webassets cache (or just disable caching altogether)

    webassets -c webassets.yaml clean
