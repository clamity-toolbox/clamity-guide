# What's Clamity?

_...because tools separate us from the rest of the animals._

You guessed it, another opionated toolbox. **Clamity** was born from my personal
approach to providing structure, automation and repeatability for software
development through CI/CD pipelines and infrastructure. It has something to
offer all parts of the **SDLC** and **Systems Operations**. Try it. Maybe you'll like
it.

Its primary tool is the `clamity CLI` which blends a custom user interface
interface with documentation in context so my tiny pea-brain doesn't have to
memorize the zillions of ways things work and glue together.

A browser front-ended service is in the planning stage.

## Opinionated choices on Documentation

I consider relevant, well-scoped, easily retrieable documentation a primary
characteristic of any operational environment. Some of the tenets guiding my
choices for documentation include...

- There should be a single source of truth for things. Systems should support
  this philospohy by referring (linking) to them rather than copying or
  restating them.

- README files within a repo living along side code should be prioritized high
  when choosing a location for a document. In these cases, it should be
  _obvious_ the document is associated with the particular repo (think _user
  guide for an application living with the application code_).

- Less is more. Assume most people don't like to read (bet ya few make it
  through this page!). Keep it brief and make it as context sensitive as
  possible (think _README files throughout the directory tree of a repo_).
