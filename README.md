# @chibicode's Playbook

My personal playbook for coding/design (WIP).

[View on **chibicode.github.io/playbook** >](http://chibicode.github.io/playbook/)

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
