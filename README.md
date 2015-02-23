# @chibicode's Playbook

My personal playbook for coding/design (WIP).

## Rails

### Acceptance Testing

#### Don't do outside-in testing

Since I'm more of a designer than a developer, it takes a while for me to settle on the final UI. Hence, outside-in tesing (writing acceptance test first, then write unit tests) doesn't quite work for me. I'd usually write acceptance test last, abandoning the TDD process.

#### Use fixtures for acceptance tests

Fixtures make a lot of sense for acceptance tests, and it's way faster.
