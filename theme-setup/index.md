---
layout: page
title: Website Build
description: "Walkthrough for how I built my site, using the HPSTR template from mmistakes. Instructions on how to install and customize a modern Jekyll theme."
image:
  feature: oeschinese.jpg
share: true
modified: 2018-02-02T15:14:43-04:00
---

I decided to build my own website partly for the learning experience and partly because I'm cheap and didn't want to pay $5/month for a service (ask me how that decision is going now that I've spent tens of hours fussing with styles, scaling, and portability issues). Since I'm a graduate student, I probably shouldn't have spent so much time on this side project; but maybe now that I did, someone else can benefit from that time investment and the knowledge I've gained in the process.

The template for this site, `hpstr-jekyll-theme` came from [Michael Rose](https://mademistakes.com), available on [his Github](https://github.com/mmistakes/hpstr-jekyll-theme)

Please feel free to clone or download these website materials and adapt as you see fit. Make sure to give credit where credit is due, particularly the original template. My only significant modification was to the homepage, where I defined a secondary header style and added it after the primary header. I did so because I wanted a bit more of a personal hook on the homepage so that visitors could learn at least one sentence about me without having to navigate any further. The rest of the modifications were for content - I added more page links to the menu bar to make the site a bit less focused on the blog content. In the future, I'd like to entirely rework the homepage and make the blog far less of a centerpiece.

Here are some instructions for adapting this site as your own (possibly with Github Pages). Following that are some additional instructions and code snippets related to the modifications and additions that are possible.

## Basic Setup for a new Jekyll site

1. Depending on your hosting process and plans to modify the site, you might want to install Ruby and Jekyll on your local machine. I did not elect to do so, since most of my content modifications could be done in a text editor and pushed to Github. To set up locally, [install Bundler](http://bundler.io) using `gem install bundler` and then install [Jekyll](http://jekyllrb.com) and all dependencies using `bundle install`.
2. Clone or download either the original [HPSTR Jekyll Theme repo](https://github.com/mmistakes/hpstr-jekyll-theme/) or [my modification](https://github.com/barbourww/barbourww.github.io/) of it and rename the site.
3. If you are planning to host the site via Github Pages, make sure to name your repository `*your_github_name*.github.io` and set up the hosting process in the repository settings. Check out [Github Pages](https://pages.github.com) for more information and setup guides.
4. See the next section for the first edits you should make, primarily by editing `_config.yml` to personalize your site. 
5. Check out the sample/existing blog posts in `_posts` to see examples for pulling in large feature images, assigning categories and tags, and other YAML data, which can easily be repurposed for your own use.
6. Read the documentation below for further customization pointers and documentation.

<div markdown="0"><a href="https://github.com/mmistakes/hpstr-jekyll-theme/archive/master.zip" class="btn">Download HPSTR Theme</a></div>
<div markdown="0"><a href="https://github.com/barbourww.github.io/archive/master.zip" class="btn">Download My Site</a></div>

---

## Important First Customizations

1. Change the `title:`, `description:`, `url:`, `name:`, `avatar:`, `bio:`, `email:`, `github:`, `google_analytics:`, and `timezone:` fields in the `_config.yml` file in the top directory.
2. Customize the site menu by editing `_includex/navigation.html` and `_data/navigation.yml`. The latter includes the external links to other pages; the two could likely be consolidated, but the separation can be helpful for organization.
3. Work on replacing information in all of the top lavel pages: `index.html` (homepage), `about/index.md`, and `research/index.md` (only on my site).

---

## Running Jekyll Locally

The preferred method for running Jekyll is with `bundle exec`, but if you're willing to deal gem conflicts feel free to go cowboy with a `jekyll build` or `jekyll serve`.

> In some cases, running executables without bundle exec may work, if the executable happens to be installed in your system and does not pull in any gems that conflict with your bundle.
>
>However, this is unreliable and is the source of considerable pain. Even if it looks like it works, it may not work in the future or on another machine.

```bash
bundle exec jekyll build

bundle exec jekyll serve
```

---

## Folder Structure

```bash
hpstr-jekyll-theme/
├── _includes
|    ├── browser-upgrade.html       # prompt to upgrade browser on < IE8
|    ├── footer.html                # site footer
|    ├── head.html                  # site head
|    ├── navigation.html            # site navigation
|    └── scripts.html               # jQuery, plugins, GA, etc
├── _layouts
|    ├── page.html                  # page layout
|    ├── page.html                  # post-index layout used on home page
|    └── post.html                  # post layout
├── _posts
├── _sass                           # Sass partials
├── assets
|    ├── css                        # compiled stylesheets
|    ├── js
|    |   ├── _main.js               # plugin options
|    |   ├── scripts.min.js         # concatenated and minifed site scripts
|    |   ├── plugins                # plugin scripts
|    └── └── vendor                 # jQuery and Modernizr scripts
├── images                          # images for posts and pages
├── _config.yml                     # Jekyll options
├── about/                          # about page
├── posts/                          # all posts
├── sample_posts               # sample posts included with original website template
├── tags/                           # all posts grouped by tag
└── index.html                      # home page with pagination
```

---

### Disqus Comments

Create a [Disqus](http://disqus.com) account and change `disqus_shortname` in `_config.yml` to the Disqus *shortname* you just setup. By default comments appear on all post and pages if you assigned a shortname. To disable commenting on a post or page, add the following to its YAML Front Matter:

```yaml
comments: false
```

### Social Share Links

To disable Facebook, Twitter, and Google+ share links on a post or page, add the following to its front matter:

```yaml
share: false
```

### Owner/Author Information

Change your name, and avatar photo (200x200 pixels or larger), email, and social networking URLs. If you want to link to an external image on Gravatar or something similar you'll need to edit the path in `navigation.html` since it assumes it is located in `/images`.

### Google Analytics and Webmaster Tools

Your [Google Analytics](https://www.google.com/analytics/#?modal_active=none) ID should be placed in its field in the `_config.yml` file. You can also add [Google Site Verification](https://support.google.com/webmasters/answer/35179?hl=en) in the same.

---

## Adding New Content

Posts are stored in the `_posts` directory and named according to the `YEAR-MONTH-DAY-title.MARKUP` format as per [Jekyll standards](https://jekyllrb.com/docs/posts/).

To streamline the creation of posts and pages, [Jekyll::Compose](https://github.com/jekyll/jekyll-compose) and [Octopress](https://github.com/octopress/octopress) are great plugins you can install to automate this process.

---

### Jekyll _includes

For the most part you can leave these as is since the author/owner details are pulled from `_config.yml`. That said you'll probably want to customize the copyright stuff in `footer.html` to your liking.

### Reading Time

On by default. To turn off remove `reading_time` from `_config.yml`. Default words per minute is set at 200 and can changed by updating `words_per_minute` in `_config.yml`.

### Feature Images

A good rule of thumb is to keep feature images nice and wide so you don't push the body text too far down. An image cropped around around 1024 x 256 pixels will keep file size down with an acceptable resolution for most devices. If you want to serve these images responsively I'd suggest looking at the [Jekyll Picture Tag](https://github.com/scottjehl/picturefill)[^1] plugin.

The two layouts make the assumption that the feature images live in the *images* folder. To add a feature image to a post or page just include the filename in the front matter like so.

```yaml
image:
  feature: feature-image-filename.jpg
  thumb: thumbnail-image.jpg #keep it square 200x200 px is good
```

If you want to apply attribution to a feature image use the following YAML front matter on posts or pages. Image credits appear directly below the feature image with a link back to the original source.

```yaml
image:
  feature: feature-image-filename.jpg
  credit: Michael Rose #name of the person or site you want to credit
  creditlink: http://mademistakes.com #url to their site or licensing
```

By default the `<div>` containing feature images is set to have a minimum height of 400px with CSS. Anything taller is hidden with an `overflow: hidden` declaration. You can customize the height of the homepage feature image and those appearing on posts/pages by modifying the following variables in `/_sass/_variables.scss`.

```scss
$feature-image-height: 400px; // min 150px recommended
$front-page-feature-image-height: 400px; // min 150px recommended
```

### Videos

Video embeds are responsive and scale with the width of the main content block with the help of [FitVids](http://fitvidsjs.com/).

### Link Post Type

Link blog like a champ by adding `link: http://url-you-want-linked` to a post's YAML front matter. Arrow glyph links to the post's permalink and the the `post-title` links to the source URL. Here's an [example of a link post]({{ site.url }}/sample-link-post/) if you need a visual.

---

### Further Customization

Jekyll 2.x added support for Sass files making it much easier to modify a theme's fonts and colors. By editing values found in `_sass/variables.scss` you can fine tune the site's colors and typography.

For example if you wanted a red background instead of white you'd change `$bodycolor: #fff;` to `$bodycolor: $cc0033;`.

---

### License

This theme is free and open source software, distributed under the [MIT License]({{ site.url }}/LICENSE) version 2 or later. So feel free to to modify this theme to suit your needs.

---

[^1]: If you're using GitHub Pages to host your site be aware that plugins are disabled. So you'll need to build your site locally and then manually deploy if you want to use this sweet plugin.
