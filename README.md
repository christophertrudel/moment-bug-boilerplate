# Purpose
Showcasing a possible bug with react-boilerplate and imports such as the ones used in moment.

# Reproducing

Just alternate between the two ways of importing the moment locale in app/App/index.js. Then,
display the page. In one case, the console should show an i18n'ed locale (but Jest will complain),
and in the other the console will show the default 'en' locale, but tests will pass without
a problem.

# Context

We're experiencing problems importing moment locales in our react-boilerplate project.

The problem is: if we "import 'moment/locale/fr';" then it's as if the locale is not loaded, and moment stays in English.

If we "import 'moment/src/locale/fr';" then the locale is loaded, we can use a localized moment, but then the tests fail: Jest tells us "Unexpected token import" when trying to parse 'moment/src/locae/fr' (which is indeed written using ES6 module syntax).

I have worked around that by using a custom "transformIgnorePatterns" including the moment module, but I'm wondering why the locale is not loaded when using the "normal" import.

For reference, the same code works fine with a fresh Create-React-App project.

