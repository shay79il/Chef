# Cookstyle

Cookstyle is a code linting tool that helps you write better Chef Infra cookbooks by detecting and automatically correcting style, syntax, and logic mistakes in your code.

```bash
cookstyle /path/to/cookbook

# Autocorrecting Cookstyle Warnings
cookstyle -a /path/to/cookbook
```

## Example

```
Inspecting 8 files
CWCWCCCC

Offences:

cookbooks/apache/attributes/default.rb:1:1: C: Missing utf-8 encoding comment.
default["apache"]["indexfile"] = "index1.html"
^
cookbooks/apache/attributes/default.rb:1:9: C: Prefer single-quoted strings when you don't
need string interpolation or special symbols.
default["apache"]["indexfile"] = "index1.html"
        ^^^^^^^^
cookbooks/apache/attributes/default.rb:1:19: C: Prefer single-quoted strings when you
don't need string interpolation or special symbols.
default["apache"]["indexfile"] = "index1.html"
                  ^^^^^^^^^^^
```

## Explanation

```bash
# Cookstyle output:

# States the number of files found and examined. For example: Inspecting 8 files

# Lists the results of those files as a series of symbols. For example: CWCWCCCC

# For each symbol, states the file name, line number, character number, type of issue or error, describes the issue or error, and specifies the location in the source code at which the issue or error is located
```

```bash
# Symbols
# The following symbols appear in the standard output and are used to indicate the result of an evaluation:

# Symbol	Description
# .	The file does not have any issues.
# C	The file has an issue with convention.
# E	The file contains an error.
# F	The file contains a fatal error.
# W	The file contains a warning.
# R	The file contains code that should be refactored.
```

## [`.rubocop.yml `](https://docs.chef.io/workstation/cookstyle/#rubocopyml)

Use a `.rubocop.yml` file in a cookbook to override the default settings in Cookstyle for enabled and disabled rules.
