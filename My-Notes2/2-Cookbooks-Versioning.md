# Semantic versioning

A cookbook version might be indicative of compatibility
or support for third-party software, correcting a bug, or adding a feature.
And a cookbook version always takes the form of x.y.z,
where x, y, and z are decimal numbers.

Semantic versioning provides guidelines
on when to change versions and what digit to adjust,
depending on the impact of the change.
So given a version number, MAJOR, MINOR, and PATCH,

_`MAJOR version`_ - would be incremented when you make a change that would break previous versions, so if it's incompatible.

_`MINOR version`_ - would be incremented when you add functionality
in a backwards-compatible manner.

_`PATCH version`_ - would be incremented when you make backwards-compatible bug fixes.

So, an example of this might be 1.1.0,
which might be incompatible or have major functionality
changes when compared with version 2.0.0.

## If no constraint is specified

Then the default constraint is 0.0.0,
and that's what it's assumed to be.
And the highest available version would match
and would then be used.

## The pessimistic version constraint uses a

- > ~&gt; 2.5.0

  - Will match versions greater than 2.5.0,
    like 2.5.1, 2.5.2, so on, but it wouldn't match 2.6.0.
    The same functionality applies when using any 2 digits
    of significance in the version number.

- > &lt; 2.3.4
  - Will match anything available below the target number.

> ## Metadata functions (They are used within the `metadata.rb` file)

`conflicts` - which would declare our cookbook is in conflict.

`depends` - which declares a dependency on a cookbook.

`provides` - which is our list of recipes or definitions, which would not be
covered via auto-generation.

`recommends` - which adds a dependency recommendation.

`replaces` - which declares that this cookbook replaces another.

`suggests` - which adds a dependency on another cookbook as a suggestion.

`supports` - which declares a supported platform.

> ## Managing and controlling changes to cookbooks

`knife cookbook upload myco_app -freeze`

- prevent unwanted or accidental changes
  to a cookbook and that freezes the changes.

`knife cookbook upload myco_app --force`

- Other versions can still be uploaded,
  but none with this specific version, unless forced.
  You can see we have the --force option there.
  Using a freezing process for cookbooks
  associated with an environment
  can help avoid accidental overwrites.
