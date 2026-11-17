# GitHub Pages Jekyll Template
This is an example [GitHub Pages](https://pages.github.com/) repository for a simple 'front door' site for an online community or other small-scale project, powered by [Jekyll](https://jekyllrb.com/) and the [Cayman](https://github.com/pages-themes/cayman) GitHub Pages theme. Unlike the default GitHub pages themes, it doesn't include a .zip download of your repo contents, as this use case isn't relevant for a standalone site.

## Adding new pages

See the [GitHub Pages documentation](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/adding-content-to-your-github-pages-site-using-jekyll) to understand how to add new pages to the site.

## Customising the theme/templates

See the [Cayman theme documentation](https://github.com/pages-themes/cayman#customizing) for instructions on editing the templates, styling and config. See also:
* [Adding a theme to your GitHub Pages site using Jekyll](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/adding-a-theme-to-your-github-pages-site-using-jekyll) - GitHub Pages documentation
* [Themes - Overriding Theme Defaults](https://jekyllrb.com/docs/themes/#overriding-theme-defaults) - Jekyll documentation.

To get your site up and running, you will likely want to change, at a minimum, the following things:
* In `_config.yml`:  
  * Set the `title` and `description` variables
  * If the site is for a Slack community, generate an invite link and set it as the value of `slack_invite_url`
  * If you use any other URLs or repeated values across multiple pages and/or includes, you can define them as global variables in this file, then refer to them in other files using the`{{ site.variable_name }}` syntax
* Change the contents of `index.md` to meet your needs. You'll probably want to start from scratch.
* Fill in `code-of-conduct.md` and `community-principles.md`, or delete them if you don't need them.
* Create additional `.md` files as needed, one for each page you want to add to your site.
  * Make sure to include a [front matter](https://jekyllrb.com/docs/front-matter/) section at the top of the file with `layout: default` and `title: [your page title here]` properties, or else the page won't be included in the site generation.
  * You may wish to nest your pages inside folders (e.g. `about/meet-the-team.md`)
* In `images/`:
  * Add your own logo and social media icon.
* In `_includes/head_custom.html`:
  * Update the `<link>` and `<meta>` elements to point to your logo and social media icon.
* Inside the `<header>` element in `_layouts/default.html`:
  * Update the `<img>` tag to point to your actual logo.
  * In the `<nav>` element, change the links as needed. Note the use of the `{{ site.baseurl }}{% link page-filename.md %}`template strings in the `href` prop.
    * Alternatively, [follow this tutorial](https://jekyllrb.com/tutorials/navigation/) to auto-generate your site navigation.
* In `style.scss`: 
  * modify the colour variables to choose your own colour theme for the site
    * See the [variables.scss](https://github.com/pages-themes/cayman/blob/master/_sass/variables.scss) file in the base theme for a full list of variables you can modify.
  * Adjust the button, navigation and skip link styles as needed.

And here are some other possible tweaks you might want to make:
* To overwrite any additional behaviour in the [base Cayman theme](https://github.com/pages-themes/cayman) that isn't covered by any of the above files, create an identically-named file in an identically-named directory. 
  * For example, if you wanted to modify the theme wholesale then you would copy over the [jekyll-theme-cayman.scss](https://github.com/pages-themes/cayman/blob/master/_sass/jekyll-theme-cayman.scss) file and place it in your repo in the `_sass/` directory, then edit it as needed.
* If you want to include blog posts/articles in your site, this isn't demonstrated in this repo, but it's a native Jekyll feature.
  * Create a `_posts` directory, then [follow these instructions](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/adding-content-to-your-github-pages-site-using-jekyll#adding-a-new-post-to-your-site) to add new posts.
  * To render a list of posts on other pages (or in your header/footer), see the [Jekyll documentation](https://jekyllrb.com/docs/posts/#displaying-an-index-of-posts).
* To associate your GitHub pages deployment with a custom domain, [follow these instructions](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site). 
## Building locally

First, ensure that you have a recent version of Ruby installed locally.

On a Mac, you can install [rbenv](https://github.com/rbenv/rbenv) using [Homebrew](https://brew.sh/) and install a sensible version of Ruby within this directory. *Version 4.x of Ruby has compatibility issues with Jekyll and GitHub pages that this repo's author was not able to resolve - PRs welcome!*
```
brew install rbenv

rbenv init # follow the instructions to add rbenv to your shell environment

rbenv install 3.4.12 # install the correct Ruby version for this repo on your machine

cd path/to/your/repo
rbenv local  # run this command to set/confirm the Ruby version for just this project
```

If any of these commands don't work as they should, you may need to quit and re-open your terminal app/tab before trying again.

Once you have a sensible Ruby environment up and running, run these two commands to install dependencies:
```
gem install bundler
bundle install
```

Finally, run this command to generate the static site and serve it locally at [localhost:4000](http://localhost:4000/):
```
bundle exec jekyll serve
```

As you edit files and save them, the static site will automatically rebuild. You will need to refresh the page to see your changes. Changes to `_config.yml` won't always be automatically reflected - you might need to stop the Jekyll serve process (Ctrl/Cmd + C) and restart it before you can see them.

## AI disclaimer
The example logo and social media icon were generated using Claude. The same Claude session was then used to auto-generate a WCAG AA-compliant colour scheme based on the colours used in the generated images.

