# A modified version of Hugo Academic

This is an adapted version of [gcushen's Academic
theme](https://github.com/gcushen/hugo-academic) for [Hugo](https://gohugo.io).
I made some edits to suit it to my tastes. The license is the same (MIT). 

My changes are:

1. Choose selected publications for display with the new `.Params.selected =
   true`. There are also new parameters in the frontmatter of each publication.

2. Added a script to convert a BibTex file to a series of [Markdown] `publication` files.

3. Modified the sections: now Bio, Teaching, Students & Advising, Publications, Contact. Most importantly, Research Interests and education are no longer stored in `config.toml`.

4. Email addresses under pic and under Contact are now protected with some Javascript and unicode encoding 

5. Added support for keybase and OpenPGP under Contact

6. Kicked out blog `post` and `project` as I did not need them. Just take the code from the original Academic theme if you want to reintroduce them.

7. Adjusted font sizes in CSS.

# The original Hugo academic

The remainder of this page is an adjusted version of the Academic theme for
[Hugo](https://gohugo.io). Kudos to gcushen for getting this underway and
supporting it.

[![Screenshot](https://raw.githubusercontent.com/gcushen/hugo-academic/master/images/screenshot.png)](https://github.com/gcushen/hugo-academic/)

Key features:

- Designed for academic staff, students, or general personal use
- Includes Biography, Publications, Projects, News/Blog, Teaching, and Contact sections
- Write in [Markdown](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet) for easy formatting and code highlighting, with [LaTeX](https://en.wikibooks.org/wiki/LaTeX/Mathematics) for mathematical expressions
- Academic linking (Scholar etc.), Google Analytics, and Disqus comments
- Responsive and mobile friendly
- Simple and refreshing one page design
- Easy to customize

## Installation

1. Install [Hugo](https://gohugo.io/overview/installing/) and create a new website:

        hugo new site my_website
        cd my_website

2. Install Academic theme with `git`:

        git clone git@github.com:ralphholz/hugo-academic.git themes/academic

3. If you are creating a new website, copy the contents of the `exampleSite` folder to your website root folder, overwriting existing files if necessary. The `exampleSite` folder contains an example config file and content to help you get started.

        cp -av themes/academic/exampleSite/* .

4. Start the Hugo server from your website root folder:

        hugo server --watch

    Now you can go to [localhost:1313](http://localhost:1313) and your new Academic themed website should appear.

5. Customize your website (see next section), build it by running `hugo`, and deploy it by copying the `public/` directory (by FTP, Rsync, git push, etc.) to your production web server.

## Getting Started

Assuming you created a new website with the example content following the installation steps above, this section explores just a few more steps in order to customize it.

### Configuration

The core parameters for the website can be edited in the `config.toml` configuration file.

As can be seen in the example `config.toml`, the social/academic networking icons and education qualifications are defined as multiples of `[[params.social]]` and `[[params.education]]` respectively. They can be duplicated or deleted as necessary.

Homepage sections will automatically disappear if you remove content (`content/`) from them.

For deployment, the `baseURL` variable should be changed to match your website URL such as `baseURL = "http://your-site.org/"`.

### Introduce yourself with a biography

Place a cropped portrait photo named `portrait.jpg` into the `static/img/` folder, overwriting any defaults.

Edit your biography in the example file in `content/home`.

### Create a publication

The attached Python script can create publication files for you.


### Add a section to home page

To add a new section to the home page:

    hugo new home/my-section-name.md

Then edit the newly created file `content/home/my-section-name.md` with your section title and content. In the `+++` preamble, you should also increment the `section_id` to ensure it's unique amongst the other sections in `content/home` and you can adjust `weight` variable to change the order within the custom section of the home page.

You may also wish to add a navigation link to the new section. This can be achieved by adding something similar to the following lines to your `config.toml`, where the URL will consist of the first title word in lowercase:

    [[menu.main]]
        name = "Research"
        url = "#research"
        weight = 10

### Removing content

Generally, to remove content, simply delete the relevant file from your `content/post`, `content/publication`, `content/project`, or `content/home` folder.

Then you can re-build and view the updated website with the `hugo` and `hugo server --watch` commands, respectively.

## Advanced customization

It is possible to carry out many customizations without touching any files in `themes/academic`, making it easier to upgrade the theme in the future.

### Custom theme color (CSS) or JavaScript (JS)

You can link custom CSS and JS assets (relative to your root `static/css` and `static/js` respectively) from your `config.toml` using `custom_css = ["custom.css"]` or `custom_js  = ["custom.js"]`.

### Permalinks

*Permalinks*, or *permanent links*, are URLs to individual pages and posts on your website. They are permanent web addresses which can be used to link to your content. Using Hugo's *permalinks* option these can be easily customized. For example, the blog post URL can be changed to the form *yourURL/2016/05/01/my-post-slug* by adding the following near the top of your `config.toml` (before `[params]` settings):

    [permalinks]
        post = "/:year/:month/:day/:slug"

Where `:slug` defaults to the filename of the post, excluding the file extension. However, slug may be overridden on a per post basis if desired, simply by setting `slug = "my-short-post-title"` in your post preamble.

## Upgrading

I am goint to try and pull in changes from upstream.

## Contributing

Please use the [issue tracker](https://github.com/gcushen/hugo-academic/issues) to let me know about any bugs or feature requests, or alternatively make a pull request.

## License

Copyright 2016 [George Cushen](http://cushen.me).
Copyright 2016 [Ralph Holz] for the changes.

Released under the [MIT](https://github.com/gcushen/hugo-academic/blob/master/LICENSE.md) license.
