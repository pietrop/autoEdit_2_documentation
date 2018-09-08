# Build/update demo front end page

[autoedit.io/demo](http://www.autoedit.io/demo) contains a dummy demo of the front end, to update this after substantial changes to the app, run

```text
npm run make_demo
```

This runs browserify to bundle the client side code and copies the `./electron` folder into the `./project_page/demo` folder.

