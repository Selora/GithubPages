---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: default
---

# GithubPages
Selora's cozy infosec lumbershack

# Github Pages Dev Setup

This setup allows you to have your GitHub pages website locally, show the output locally, edit everything from VSCode, and have a somewhat ressembling result when pushing to GitHub. There's some minor differences there and there, but overall it's pretty good.

Site used as reference: 
https://dfederm.com/creating-a-blog-using-github-pages/

## TODO On Github

1. Create a repo \<yourUsername\>.github.io
2. Rename the branch 'main' to 'source'
2. Go to the repo settings, enable pages on the 'source' branch

Your website is now available on \<yourUsername\>.github.io

You now need to setup the dev env to go with it. You'd rather have that locally than using github's web editor...

## Setup Docker Env

With VSCode, use the Remote-Container extension and the `.devcontainer` and `Dockerfile` will take care of you.

**If you're starting a new projet:**

1. Create a new jekyll environment: `jekyll new .`
2. Replace the Gemfile so it uses Github pages extensions: 

```
source "https://rubygems.org"

# To update to the latest github dependencies run: `bundle update`
# To list current versions: `bundle exec github-pages versions`
# Check github versions: https://pages.github.com/versions/
gem "github-pages", group: :jekyll_plugins

group :jekyll_plugins do
  gem 'jekyll-feed'
  gem 'jekyll-paginate'
  gem 'jekyll-seo-tag'
  gem 'jekyll-sitemap'
end

# Windows and JRuby does not include zoneinfo files, so bundle the tzinfo-data gem
# and associated library.
install_if -> { RUBY_PLATFORM =~ %r!mingw|mswin|java! } do
  gem "tzinfo", "~> 1.2"
  gem "tzinfo-data"
end

# Performance-booster for watching directories on Windows
gem "wdm", "~> 0.1.1", :install_if => Gem.win_platform?
```

3. Download and install the gems: `bundle update`
4. Run the project (It'll auto-refresh as you go): `bundle exec jekyll serve --drafts --livereload`
