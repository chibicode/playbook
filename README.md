# @chibicode's Playbook

My personal playbook for coding/design (WIP).

[View on **chibicode.github.io/playbook** >](http://chibicode.github.io/playbook/)

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
* :non-potable_water: `:non-potable_water:` when plugging memory leaks
* :memo: `:memo:` when writing docs
* :penguin: `:penguin:` when fixing something on Linux
* :apple: `:apple:` when fixing something on Mac OS
* :checkered_flag: `:checkered_flag:` when fixing something on Windows
* :bug: `:bug:` when fixing a bug
* :fire: `:fire:` when removing code or files
* :green_heart: `:green_heart:` when fixing the CI build
* :white_check_mark: `:white_check_mark:` when adding tests
* :lock: `:lock:` when dealing with security
* :arrow_up: `:arrow_up:` when upgrading dependencies
* :arrow_down: `:arrow_down:` when downgrading dependencies
* :shirt: `:shirt:` when removing linter warnings

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
