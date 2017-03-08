Reduced test case to break Gulp SASS Sourcemaps
===============================================

Whilst using SASS to process scss in combination with gulp-autoprefixer it is
possible to break the external sourcemaps for scss files in nested directories.

Installation
------------

Navigate to project in a terminal and type:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
npm install
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Usage
-----

It is possible to generate CSS from the Gulp task by typing:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
gulp
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Individual Gulp tasks can be triggered via:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
gulp prefix
gulp noPrefix
gulp workAround
gulp postCSS
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Possible solutions
------------------

### WorkAround

Originally this was suggested by
[ByScripts](https://github.com/ByScripts/gulp-sample). It involves calling the
sourcemaps plugin twice. Once during the conversion of scss to css and once
during the auto-prefix part of the task. Whilst this solution does work, it
leaves the css file with two sourcemap references. Which on a larger project
could add to the css filesize in a negative way.

### Use PostCSS

Whilst looking into PostCSS, the processing ability of CSSNext has revealed
itself. This task does not use gulp-autoprefixer anymore. Again the task is
split into two parts. Initially the scss is converted in a default way into css.
That css is then processed by PostCSS using CSSNext, which auto-prefixes the
code. This method retains the sourcemaps connection and makes visual debugging
easier.

Support
-------

This repo was initially put together to illustrate the problem for Stack
Overflow. If the above solutions help you out, then great!
