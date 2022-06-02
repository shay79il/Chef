# Cookbook Depedencies

## How to reference one **cookbook** to another **cookbook**

### 1. Goto the `metadat.md` file in the dependent cookbook and add the following

```ruby
depends '<cookbook-name>'

# E.g.
depends 'ntpserver'
```

### 2. Add to the dependent cookbook `default.rb` file the following

```ruby
include_recipe 'ntpserver::default'
include_recipe 'webserver::apachepkg'
include_recipe 'webserver::apachefile'
include_recipe 'webserver::apacheservice'
```

### 3. Run the simple command

```bash
chef-client --local-mode --runlist "recipe[webserver]"
```
