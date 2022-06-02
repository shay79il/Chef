# Incluse_Recipe

## How to bundle multiple recipes to avoid running LONG RunLists

```bash
#E.g.
chef-client --local-mode --runlist  \
    "recipe[webserver::default],    \
     recipe[webserver::file],       \
     recipe[webserver::apache2]"
```

## 1. Divide your **long** `rb` file to multiple **meaningful** recipes

E.g.
Instead of having one big file to

- Installing apache
- Manipulating the html file
- Start the apache service

Have 3 `rb` files

- `apachepkg.rb`
- `apachefile.rb`
- `apacheservice.rb`

And have the `default.rb` file to be as follows

```ruby
include_recipe 'webserver::apachepkg'
include_recipe 'webserver::apachefile'
include_recipe 'webserver::apacheservice'
```

## 2. Run the simple command

```bash
# To refer to the default recipe ommit the 'recipe-name'
chef-client --local-mode --runlist "recipe[webserver]"
```
