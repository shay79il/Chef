# [Berkshelf](https://docs.chef.io/workstation/berkshelf/)

- Berkshelf is a dependency manager for Chef cookbooks.
- A Berksfile describes the set of sources and dependencies needed to use a cookbook. It is used in conjunction with the `berks` command.

With it, you can depend on community cookbooks and include them in your workflow.
You can also ensure that your CI systems reproducibly select the same cookbook versions, and can upload and bundle cookbook dependencies without needing a locally maintained copy.
Berkshelf is included in Chef Workstation.

### let's say this is the `metadata.rb` file

```ruby
name 'my_first_cookbook'
version '0.1.0'
depends 'apt', '~> 5.0'
```

### And this is the `Berksfile` file

```ruby
source 'https://supermarket.chef.io'
metadata
cookbook "NAME" [, "VERSION_CONSTRAINT"] [, SOURCE_OPTIONS]
```

- `source` Keyword defines where Berkshelf should look for cookbooks.
- The `cookbook` keyword allows the user to define where a cookbook is installed from, or to set additional version constraints. It can also be used to install additional cookbooks, for example to use during testing.

### Now just run

```bash
berks install
```

### Output

```bash
# Resolving cookbook dependencies...
# Fetching 'my_first_cookbook' from source at .
# Fetching cookbook index from https://supermarket.chef.io...
# Installing apt (5.0.0)
# Using my_first_cookbook (0.1.0) from source at .
# Installing compat_resource (12.16.2)
```
