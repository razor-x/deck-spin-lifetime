# Effect of contacts on spin lifetime measurements in graphene

[![All rights reserved](https://img.shields.io/badge/license-All_rights_reserved-blue.svg)](./LICENSE.txt)
[![Dependency Status](https://img.shields.io/gemnasium/evansosenko/deck-spin-lifetime.svg)](https://gemnasium.com/razor-x/jekyll-and-deck.js)
[![Build Status](https://img.shields.io/travis/evansosenko/deck-spin-lifetime.svg)](https://travis-ci.org/razor-x/jekyll-and-deck.js)

**by [Evan Sosenko](https://evansosenko.com/)**

[Contributed Talk, APS March Meeting March 2014, Denver, CO, US.](http://meetings.aps.org/Meeting/MAR14/Event/209736)

See this and other talks at
[evansosenko.com](https://evansosenko.com/).

Source for [my deck](https://evansosenko.com/deck-spin-lifetime/) running on Jekyll and deck.js.

Source for your deck running on Jekyll and deck.js.
Just clone and deck.

Demo at [io.evansosenko.com/jekyll-and-deck.js/](https://io.evansosenko.com/jekyll-and-deck.js/).

Lots of baked in features.

If you like this, check out the sister project
[Jekyll & ZURB](https://github.com/razor-x/jekyll-and-zurb).

**Version 2 is the last stable release** and will remain on Jekyll 2.
Only bug fixes and security patches will be accepted.

For new decks, checkout my new
[Bespoke.js deck skeleton powered by Brunch and awesome.](https://github.com/makenew/deck-bespoke.js)

### Create your [deck.js](http://imakewebthings.com/deck.js/) deck with [Jekyll](http://jekyllrb.com/).

  * Basic [Rake](https://github.com/jimweirich/rake) tasks with support
    for dev and testing modes, run `rake -D` for info.
  * Automatically publish to [GitHub pages](http://pages.github.com/)
    with [Travis CI](https://travis-ci.org/).
  * [LiveReload](http://livereload.com/) support. Just run `guard`.
  * Use [Firebase](https://www.firebase.com/) to set up a remote control for your deck.
  * Slide notes using [Remodal](http://vodkabears.github.io/remodal/).
  * Includes the custom material theme: a clean responsive style to help bootstrap your deck.

### Asset pipeline with [Jekyll::AssetsPlugin](https://github.com/ixti/jekyll-assets).

  * [Bower](http://bower.io/) for asset dependency management.
  * [Sass](http://sass-lang.com/), [CoffeeScript](http://coffeescript.org/).

### Modern web libraries and patterns.

  * Syntax highlighting with [highlight.js](http://highlightjs.org/).
  * Load fonts with [Web Font Loader](https://github.com/typekit/webfontloader).
  * Load JavaScript asynchronously with [HeadJS](http://headjs.com).
  * [MathJax](http://www.mathjax.org/) ready:
    just set `mathjax: true` in `_config.yml`.
  * Meta data system for SEO and social media:
    see `_data/meta.yml`.
  * Complete favicon set from [Favic-o-matic](http://www.favicomatic.com/).

### Analytics and social features.

  * Social media button support.
  * [Google Analytics](http://www.google.com/analytics/) ready:
    see `google_analytics` variable in `_config.yml`.
  * [Piwik](https://piwik.org/) ready:
    set `piwik: yoursite.com/piwik/` in `_config.yml`
    (yoursite.com/piwik/ points to the piwik install root).

## Quick start

You will need Ruby ≥ 2 with [Bundler](http://bundler.io/) and [Bower](http://bower.io/).

Just clone this with

```bash
$ git clone https://github.com/razor-x/jekyll-and-deck.js.git my-deck
```

run `bundle && bower install` and make your deck in `index.haml`.
Head over to the [Jekyll Docs](http://jekyllrb.com/docs/home/) and [deck.js docs](http://imakewebthings.com/deck.js/docs/) for the rest of the details.

Running off the `master` branch may be unstable and is not suitable for production.
Only tagged releases are considered stable.

## Demo site and documentation

The `master` branch of this project is designed to be used
as a starting point for your deck and as a branch to pull updates from.
Thus, most features are disabled by default,
and only a minimal deck has been created.

The `demo` branch is a full deck that will contain
real examples and documentation for the included features.
That branch is automatically built and published by Travis CI.

Demo deck hosted on GitHub pages:
[io.evansosenko.com/jekyll-and-deck.js/](https://io.evansosenko.com/jekyll-and-deck.js/).

## Add future update support

If you want to merge in future updates from this project and have your own origin,
set up a separate branch to track this.

```bash
$ git remote rename origin upstream
$ git branch jekyll-and-deck.js
$ git branch -u upstream/master jekyll-and-deck.js
```

Then add an origin and push master

```bash
$ git remote add origin git@github.com:username/my-deck.git
$ git push -u origin master
```

Now, the `jekyll-and-deck.js` branch will pull changes from this project,
which you can then merge into your other branches.

If you later clone your repo you will need to create the update branch again.

```bash
$ git remote add upstream https://github.com/razor-x/jekyll-and-deck.js.git
$ git fetch upstream
$ git checkout -b jekyll-and-deck.js upstream/master
```

## Automatic publishing to GitHub pages with Travis CI

Note: you can still use Travis CI for testing only (no deploy step):
simply add `SKIP_DEPLOY=true` to the Travis environment.

If you are hosting at `username.github.io` you will need to leave the `master` branch empty
and put your code in a different branch.
The `master` branch otherwise functions like the `gh-pages` branch below.

[See here](http://pages.github.com/) for details on the different use cases.

First, make a `gh-pages` branch unless you are using `master` as discussed above,

```bash
$ git checkout --orphan gh-pages
```

and **remove all files and folders except the `.git` directory**.

```bash
$ git reset .
$ git clean -fdx
```

Then, make an initial commit with only `index.html`, push it, and make sure it goes live online.

```bash
$ echo "GitHub Pages placeholder" > index.html
$ git add index.html
$ git commit -m "GitHub Pages placeholder"
$ git push -u origin gh-pages
$ git checkout master
```

Next, install the travis gem,

```bash
$ gem install travis
```

create a
[GitHub Deploy Key](https://developer.github.com/guides/managing-deploy-keys/#deploy-keys),
and name the private key `.deploy_key`.
Encrypt it with

```bash
$ travis encrypt-file .deploy_key
```

Commit the encrypted file `.deploy_key.enc` and modify
the `before_install` quoted command in `.travis.yml` to match the generated one.

Instead of (or in addition to) checking `.deploy_key.enc` into the repository,
if the `DEPLOY_KEY` environment variable is not empty, then its value will be
used to override the contents of the `.deploy_key` file during the build.
This is useful if you need to have repository specific deploy keys
(convenient when forking or maintaining a staging site as described below).
Do not use actual newlines or spaces in the environment variable string;
instead, `[NL]` will be converted to a real newline and `[SP]` to a real space.

Set the source branch that will be used to build the site.

```bash
$ travis env set SOURCE_BRANCH master
```

Other branches will still be built for testing,
but only changes to the `SOURCE_BRANCH` will be deployed.

Finally, switch on your repo in Travis CI and push your changes.

```bash
$ git add .travis.yml
$ git commit -m "Automatic publishing to GitHub pages with Travis CI."
$ git push
```

### Staging site

If the environment variable `STAGING_URL` is set,
then this value will be used to set `domain`, `baseurl`, and the assets `baseurl`.
This is useful when you want to setup a staging site
on a separate development repository.

You may override the CNAME for the staging site by setting
the `CNAME` environment variable.
Set `CNAME` to `false` to remove the `CNAME` file on build.

## Updating

The `Gemfile` is using pessimistic version constraints for everything,
so if you don't want to wait for updates, you need to bump the versions yourself,
run `bundle update` and commit the updated `Gemfile.lock`.

JavaScript library versions need to be updated in `bower.json` and `_config.yml` (for CDN).

## License

The code and content for this deck is Copyright © 2013-2015 Evan Sosenko.

This deck is built with [Jekyll & deck.js](https://github.com/razor-x/jekyll-and-deck.js)
which is licensed under the [MIT license](./MIT-LICENSE.txt).

## Warranty

This software is provided "as is" and without any express or
implied warranties, including, without limitation, the implied
warranties of merchantibility and fitness for a particular
purpose.
