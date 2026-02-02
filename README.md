
## Locally build


1. Ensure there is a `Gemfile`
    ```
    source "https://rubygems.org"

    gem "github-pages", group: :jekyll_plugins
    gem "webrick"
    ```
2. `bundle install`
3. `bundle exec jekyll serve --baseurl=""`