# burst

Burst is a microblog first jekyll theme. Ideal for people who want to fire off quick posts that will not require much thought about formatting, tags, date, etc. 

All micro posts will be in the `_micro` folder. 

## Installation

** DOES NOT WORK YET**
**IGNORE - you can clone this repo and work from there, though**
Add this line to your Jekyll site's `Gemfile`:

```ruby
gem "burst"
```

And add this line to your Jekyll site's `_config.yml`:

```yaml
theme: burst
```

And then execute:

    $ bundle

Or install it yourself as:

    $ gem install burst

**IGNORE end of ignore**

If you really are committed to microblogging, wanting to fire off whatever thought without typing any yaml at all in your posts placed in the _micro folder, add this precommit hook that will add yaml to the top of all of the files that you newly commit to the _micro directory. The date in this file does not matter for your purposes because it is the file name that is used for sort order. So, continue to name posts like you are familiar with with jekyll yyyymmdd-something.md.

```
#!/bin/sh
# Contents of .git/hooks/pre-commit

git diff --cached --name-status | grep "_micro" | while read a b; do
  echo "---\ndate: $(date -u "+%Y-%m-%d %T %Z")\n---\n$(cat $b)" > tmp
  mv tmp $b
  git add $b
done
```

By "add this precommit hook", I mean add a file called `pre-commit` in the project subfolder `.git/hooks` You may have to make it executable with `chmod ug+x .git/hooks/*`


## Usage

TODO: Write usage instructions here. Describe your available layouts, includes, sass and/or assets.

## Contributing

Bug reports and pull requests are welcome on GitHub at https://github.com/[USERNAME]/hello. This project is intended to be a safe, welcoming space for collaboration, and contributors are expected to adhere to the [Contributor Covenant](http://contributor-covenant.org) code of conduct.

## Development

To set up your environment to develop this theme, run `bundle install`.

Your theme is setup just like a normal Jekyll site! To test your theme, run `bundle exec jekyll serve` and open your browser at `http://localhost:4000`. This starts a Jekyll server using your theme. Add pages, documents, data, etc. like normal to test your theme's contents. As you make modifications to your theme and to your content, your site will regenerate and you should see the changes in the browser after a refresh, just like normal.

When your theme is released, only the files in `_layouts`, `_includes`, `_sass` and `assets` tracked with Git will be bundled.
To add a custom directory to your theme-gem, please edit the regexp in `burst.gemspec` accordingly.

## License

The theme is available as open source under the terms of the [MIT License](https://opensource.org/licenses/MIT).

