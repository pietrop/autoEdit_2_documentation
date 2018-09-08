# Build project page

The project page is visible at [autoedit.io](http://www.autoedit.io).To edit the project page go to `./project_page` folder and edit the [jekyll](https://jekyllrb.com/) site that is hosted on github pages for this repository.

To update the project page run

```text
npm run make_page
```

This copyies from the `./project_page` folder \(that also contains the demo front end\) to [the `/docs` folder](https://help.github.com/articles/configuring-a-publishing-source-for-github-pages/) in this repo used to publish with [github page](https://pages.github.com/).

This comand also updates the demo front end \([autoedit.io/demo](http://www.autoedit.io/demo)\). To update project page without updating demo front end code `npm run preview_page_no_demo_reload`.

The project page is a jeckyll site, and can be previewed locally using

```text
npm run preview_page
```

Then visit [http://127.0.0.1:4000/](http://127.0.0.1:4000/)

The project site uses this template for the Landing page [pratt-app-landing-page](http://blacktie.co/2013/10/pratt-app-landing-page/) [demo](http://blacktie.co/demo/pratt)

