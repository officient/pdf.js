# PDF.js

Forked from [/mozilla/pdf.js](https://github.com/mozilla/pdf.js) - See [diff](https://github.com/mozilla/pdf.js/compare/3456ed271b0109f4be735691d9565e513c43267a...officient:master).

## Why

The ES5 build in mozilla/pdf.js causes an unsafe-eval issue because of regenerator-runtime.
We have made a [patch](https://github.com/mozilla/pdf.js/commit/226106d83384734d17c13c25100b8d3188b602f9) to remove strict mode during the minified build.

We are also embedding the viewer.html inside an iframe inside a PWA, this causes us to load the required file diffently.

We also added our own styling, without a sidebar and toolbar to improve UX on mobile.

## Building

```
npm install -g gulp-cli
npm install

gulp minified-legacy
cp -rf build/minified-legacy/* ../officient-employee-self-service/html/pdfjs
```

Then follow additional steps in the ESS repo [how-to-upgrade.md](https://github.com/officient/officient-employee-self-service/blob/master/html/how-to-upgrade.md)
