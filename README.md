# PDF.js

Forked from [/mozilla/pdf.js](https://github.com/mozilla/pdf.js) - See [diff](https://github.com/mozilla/pdf.js/compare/v2.8.335...officient:2-8).

## Why

### CSP issues in legacy builds

Mozilla/PDF.js is causing an **unsafe-eval** issue for legacy ES5 builds because of **regenerator-runtime** (babel polyfill for async/await) requiring a side effect because they are polluting global scope with `regeneratorRuntime`. They have a way of "escaping" strict mode but it's causing CSP issues for us. An alternative is to find the global object anyway and set the `regeneratorRuntime` variable correctly on that.

We found a patch that works for us but has not been merged yet: https://github.com/facebook/regenerator/pull/396 Our PDF.js fork uses this patch in our own [regenerator fork](https://github.com/officient/regenerator).

### Updated viewer

We added our own styling and removed the sidebar and toolbar to have a minimalistic look for our mobile app. Where you only see zoom in/out buttons.

### Loading inside an iframe

We are also embedding the viewer.html inside an iframe inside a PWA, this causes us to load the required file diffently.

## Building

```
npm install -g gulp-cli
npm install

gulp minified-legacy
cp -rf build/minified-legacy/* ../officient-employee-self-service/html/pdfjs
```

Then follow additional steps in the ESS repo [how-to-upgrade.md](https://github.com/officient/officient-employee-self-service/blob/master/html/pdfjs/build/how-to-upgrade.md)
