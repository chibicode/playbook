# @chibicode's Playbook

My personal playbook for coding/design (WIP).

<p class="hidden-flatdoc"><a href="http://chibicode.github.io/playbook/">View on <strong>chibicode.github.io/playbook</strong></a></p>

## Graphic Design

### Stock Photos

#### Use Unsplash

[https://unsplash.com/](https://unsplash.com/). There's also [Unsplash.it](https://unsplash.it/) for placeholders.

## Development Practices

### Git

#### Optionally use Emojis for commit

From [Atom's CONTRIBUTING.md](https://github.com/atom/atom/blob/master/CONTRIBUTING.md):

* :art: `:art:` when improving the format/structure of the code
* :racehorse: `:racehorse:` when improving performance
* :memo: `:memo:` when writing docs
* :bug: `:bug:` when fixing a bug
* :fire: `:fire:` when removing code or files
* :green_heart: `:green_heart:` when fixing the CI build
* :white_check_mark: `:white_check_mark:` when adding tests
* :lock: `:lock:` when dealing with security
* :arrow_up: `:arrow_up:` when upgrading dependencies
* :shirt: `:shirt:` when removing linter warnings

From other places:

* :gem: `:gem:` when installing gems

## CSS

### Go-to Font Stacks

#### Avenir:

```
font-family: avenir, 'avenir next', helvetica, 'helvetica neue', arial, sans-serif;
```

#### Code:

```
font-family: Consolas, monaco, monospace;
```

#### Japanese:

```
font-family: "游ゴシック", YuGothic, "ヒラギノ角ゴ ProN W3", "Hiragino Kaku Gothic ProN", "メイリオ", Meiryo, sans-serif;
```

Thanks to [tachyons](https://github.com/mrmrs/tachyons-font-family/blob/master/tachyons-font-family.css).

### Base Templates

#### MNML and Tachyons

- http://mn-ml.cc/
- http://tachyons.io/

## Ruby

### Style Guide

#### Use RuboCop (and optionally Hound CI, which uses RuboCop)

https://github.com/bbatsov/rubocop
https://github.com/thoughtbot/hound

## Rails

### Acceptance Testing

#### Don't use cucumber

I want to minimize the learning cost; I usually spend more time learning about Cucumber than using it.

#### Don't do outside-in testing

Since I'm more of a designer than a developer, it takes a while for me to settle on the final UI. Hence, outside-in tesing (writing acceptance test first, then write unit tests) doesn't quite work for me. I'd usually write acceptance test last, abandoning the TDD process.

#### Use fixtures for acceptance tests

Fixtures make a lot of sense for acceptance tests, and it's way faster.

### Speeding Up Rails Tests

#### Use spring binstubs

[See here.](https://github.com/jonleighton/spring-commands-rspec)

```ruby
gem "spring-commands-rspec", group: :development
```

#### Use RSpec tags to run specific tests

...and create a shell script under `bin` that runs all focused tests.

```
# Run tests that are of the form: `it "...", :f do`
rspec --tag f
```

#### Run Rails-less tests and with-Rails tests separately

...and create a shell script under `bin` that runs all Rails-less tests.

```
rspec spec/models spec/services spec/decorators ...
```

#### Use `active_record_spec_helper`

[`active_record_spec_helper`](https://gist.github.com/coreyhaines/2068977) lets you load ActiveRecord models without loading Rails.

> [View Related Blog Post](http://articles.coreyhaines.com/posts/active-record-spec-helper/)

#### Add `-I app` flag on `.rspec`

Instead of `require_relative ../../` for Rails-less tests, you can use relative paths directly by using the `-I` flag on `.rspec`, which adds a given path to load paths.

```
# On .rspec
-I app
```

### Emails

#### Don't spam customers accidentally on dev environment

Consider using:

- [letter_opener](https://github.com/ryanb/letter_opener)
- [mailcatcher](https://github.com/sj26/mailcatcher)
- [MailTrap](https://mailtrap.io/)
